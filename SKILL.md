---
name: Nuclear Industry Documents
description: >
  Use this skill whenever a question touches nuclear power plant design, systems, operation,
  licensing basis, or accidents — especially GE BWR/3 and BWR/5, Westinghouse four-loop PWRs,
  and the Chernobyl RBMK-1000 disaster. It maps a local corpus of four primary documents
  (R304B BWR systems manual, R304P PWR systems manual, Columbia Generating Station FSAR
  Amendment 67, IAEA INSAG-7) into Markdown with inline figures and page anchors, and tells you
  which document is authoritative for what, how to search it, and how to cite it.
---

# Nuclear Industry Documents

A curated, AI-readable corpus of nuclear plant documents in this repository.

**Prime directive:** answer from these documents when they cover the question. They are the primary
sources; your parametric memory is the fallback. Quote them, cite the file and page, and say when the
corpus does not cover something.

---

## 1. When to use this skill

Load or consult this corpus when the task involves:

- **BWR systems** — recirculation, jet pumps, control rod drives, RCIC, HPCI, ADS, core spray, RHR,
  SRVs/MSIVs, Mark I/II containment, neutron monitoring, rod block, reactor protection.
- **BWR/3 vs BWR/5 differences**, or "what does a BWR/5 plant actually do".
- **Westinghouse PWR systems** — RCS, pressurizer, steam generators, CVCS, RHR/ECCS, AFW, rod control,
  ARPI/DRPI, ex-core/in-core instrumentation, RPS and ESFAS.
- **Comparing PWR and BWR** approaches to the same function.
- **Licensing basis** questions: design bases, GDC conformance, classification, setpoints, materials,
  acceptance criteria, design-basis accidents.
- **Chernobyl / RBMK-1000**: accident sequence, positive void coefficient, control-rod design,
  operating reactivity margin, AZ-5, operator actions, safety culture, Soviet regulatory failure.

Do **not** use it as the authority for: current plant configuration after Amendment 67, fuel cycle
details, security plans, emergency planning zones, or regulations newer than the documents.

---

## 2. Corpus map

| Folder | Document | Authority for | Not authoritative for |
|---|---|---|---|
| `R304B/` | GE BWR Systems Technology Manual (NRC HRTD, Rev 09/11) | How BWR systems work; component anatomy; operator indications and interfaces; BWR/3 and BWR/5 practice | One specific plant; licensing numbers |
| `R304P/` | Westinghouse PWR Systems Technology Manual (NRC HRTD) | How a Westinghouse 4-loop PWR works; PWR components; rod control, RPS/ESFAS | One specific plant; licensing numbers |
| `CGS_FSAR/` | Columbia Generating Station FSAR, Amendment 67 | Plant-specific BWR/5 design basis, numbers, analyses, commitments | Current docket; other plants |
| `INSAG-7/` | IAEA Safety Series 75-INSAG-7 (1992) | Chernobyl causes and sequence; RBMK design and physics; safety culture | Post-1992 RBMK modifications; health/environmental consequences |

Each folder contains:

```
<DOC>/TABLE_OF_CONTENTS.md   full outline down to sub-subsection, with links
<DOC>/FIGURE_INDEX.md        every extracted figure: number, caption, file, source page
<DOC>/chapters/*.md          the text, with inline figures and <!-- p.N --> page anchors
<DOC>/figures/*.png          figure images (raster preview, 200 dpi)
<DOC>/figures/*.svg          lossless vector original, same figure number (where the source page is vector art)
```

`SOURCES/` holds the original PDFs, one folder per document (same names as the Markdown
folders), when you need to check a page against the source. All paths and links are relative.

`MASTER_TABLE_OF_CONTENTS.md` at the root has the cross-document topic map — start there when you
do not know which document holds the answer. `DOCKET_NUMBERS.md` at the root maps plant names to NRC
dockets (all 95 operating units), including the dockets for this corpus.

---

## 3. Reading protocol

### Locate — search first, browse second

1. Select the appropriate document using the
   authority table in §2.

2. Search chapter filenames BEFORE opening any
   table of contents.

   rg --files R304B/chapters R304P/chapters \
     CGS_FSAR/chapters INSAG-7/chapters \
     | rg -i 'rhr|residual.*heat'

3. If filenames don't identify the relevant chapter,
   search chapter CONTENTS for matching files:

   rg -l -i 'residual heat removal' \
     CGS_FSAR/chapters/

4. Search within the matching chapter for relevant
   headings and passages. Read only those sections.

5. Consult MASTER_TABLE_OF_CONTENTS.md or a document
   TABLE_OF_CONTENTS.md only when direct search fails
   or the question requires broad document exploration.

6. Use FIGURE_INDEX.md only for figure discovery.

7. Preserve original PDF page markers when citing.

```bash
# run from the repository root (the folder containing MASTER_TABLE_OF_CONTENTS.md)

# which document/section mentions a term
grep -rniE "operating reactivity margin|ORM" --include=*.md .

# inside one document, with line numbers
grep -niE "setpoint" R304B/chapters/10.2_ADS.md

# find a figure by topic
grep -i "suppression pool" */FIGURE_INDEX.md

# know how many places discuss something before reading
grep -rli "positive scram" .

# jump to the page containing a hit
grep -n -B2 -A6 "positive scram" INSAG-7/chapters/*.md
```

```python
# read a page range around a heading
from pathlib import Path
t = Path('CGS_FSAR/chapters/6.3_EMERGENCY_CORE_COOLING_SYSTEM.md').read_text()
i = t.find('6.3.1.1.1')
print(t[i:i+4000])
```

---

## 4. How to answer different question types

**"How does X work?" (system/component)**
R304B or R304P chapter for X → explain purpose, components, flow path, controls/interlocks, failure
modes, operator indications. Add the FSAR section only if the user needs plant-specific detail.

**"What is the setpoint / capacity / material / acceptance criterion?"**
CGS FSAR only. Numbers in the training manuals are typical values, not commitments. Quote the table
or section, and name the amendment if the page header shows a different one.

**"Why is the design like this?"**
Three layers, in order: (1) the functional requirement (FSAR design basis / GDC in Ch 3.1),
(2) the system implementation (R304B/R304P and FSAR Ch 5–7), (3) the operating consequence
(FSAR Ch 15, or R304B "system features").

**"Compare BWR and PWR."**
Use R304B ↔ R304P for the generic comparison and CGS ↔ a PWR FSAR for plant-specific. Anchor on
function, not hardware: reactivity control, heat removal, inventory control, pressure control,
containment, decay-heat removal, protection.

**"What happened at Chernobyl and why?"**
INSAG-7 only, and in this order: §2 (design features) → §3 (the accident) → §4 (re-analysis) →
§5–6 (judgements and contributing factors) → Annex II (physics and sequence in Soviet detail).
Do not repeat INSAG-1-era claims that INSAG-7 explicitly retracts (blanket operator-error causality;
"operation below 700 MW(th) was prohibited"; ECCS blocking as the trigger).

**"Is X safe / what would happen if…"**
Say explicitly that the corpus covers design basis, not PSA or severe-accident analysis. CGS Ch 15
gives design-basis results; there is no PRA, no SAMG, no source-term document here.

---

## 5. Orientation: the four technologies

Keep these straight; mixing them is the most common error.

| | BWR/3 & BWR/5 (R304B, CGS) | Westinghouse 4-loop PWR (R304P) | RBMK-1000 (INSAG-7) |
|---|---|---|---|
| Moderator | light water | light water | **graphite** |
| Coolant | boiling water, direct cycle | pressurised water, indirect cycle | boiling water in pressure tubes |
| Core geometry | pressure vessel, 7×7 (BWR/3) / 8×8 (BWR/5) fuel | pressure vessel, 17×17 fuel, RCCAs | ~1 660 fuel channels (pressure tubes) in a graphite stack |
| Power control | control rods + **recirculation flow** | control rods + **boric acid** | control rods + ORM; **positive void coefficient** |
| Shutdown | scram (hydraulic CRD) | trip (rod drop, gravity) | AZ-5 (rod insertion — the Chernobyl defect) |
| Heat removal | jet pumps/recirculation; RCIC, HPCI, ADS, core spray, RHR | RCPs; AFW, SI, accumulators, RHR | main circulation pumps; ECCS |
| Containment | Mark I (BWR/3) / **Mark II** (BWR/5, CGS) | large dry (or ice-condenser/subatmospheric) | **none** (reactor hall / confinement) |
| Signature term | "scram", "jet pump", "SRV", "suppression pool" | "trip", "pressurizer", "PORV", "accumulator" | "ORM", "AZ-5", "positive scram" |

BWR/3 → BWR/5 in one line: Mark I → **Mark II** containment, 7×7 → 8×8 fuel, refined ECCS
(HPCI/RCIC/ADS/core spray/RHR suite) and tighter seismic and QA requirements; both remain
boiling, direct-cycle, jet-pump plants.

---

## 6. Chernobyl essentials (the corpus's most misunderstood material)

From INSAG-7, the accepted causal picture:

- The RBMK had a **positive void coefficient** at low operating reactivity margin, and the ORM at the
  time of the test was far below the permitted value — the reactor was in a condition where a power
  excursion was possible.
- The **control rods had graphite displacers with a 1.25 m water-filled gap** at each end. Inserting a
  fully withdrawn rod therefore displaced water at the bottom of the core first, adding **positive**
  reactivity before the absorber arrived — "positive scram".
- The accident was triggered by the **AZ-5 scram at 01:23:40** while the reactor was in that
  low-ORM, high-void state, not by a single operator blunder; design secrecy, weak regulation and a
  production-pressure culture ("safety culture" deficit) are treated as root causes.
- INSAG-7 **retracts or qualifies** several INSAG-1 assertions: ECCS blocking was permitted with
  authorization, sustained operation below 700 MW(th) was not formally prohibited, and blame should
  not be assigned to operators alone.

For anything finer — timestamps, rod counts, ORM values, test procedure steps — read the file, and
prefer INSAG-7's Annex II (Soviet working group) for numbers.

---

## 7. Caveats to state when relevant

- **Snapshot, not current:** CGS FSAR is Amendment 67; pages carry different amendment vintages
  (see the per-page header). Plants amend FSARs continuously.
- **OCR noise:** INSAG-7 is a 1992 scan. Expect substitutions (`dear` for `clear`, mangled Greek
  symbols). CGS drawing-plate labels are partly garbled OCR — trust the image.
- **Figure numbering:** where the document printed a figure number it is used (`fig_2.4-1.png`);
  CGS drawing plates have no machine-readable captions and are named by PDF page (`fig_page-114.png`).
  Always confirm a figure's identity against its surrounding text.
- **Use the SVG for detail:** every figure that the source has as true vector art now ships as both a
  200 dpi PNG (inline preview, universally viewable) and an `.svg` named identically (e.g.
  `fig_2.5-13.svg`). Diagrams and schematics are line art in SVG: zoom or rasterize at any size and the
  text/lines stay sharp. Scanned plates (most INSAG-7 figures, some CGS appendices) have PNG only —
  for those the source scan is the resolution limit, so don't over-zoom and expect more detail.
- **Read-offs:** even with vector art, do not attempt exact numeric read-off from a plotted curve
  without checking the corresponding table in the text.
- **Coverage gaps:** R304B lacks GE sections 1.1–1.6 and 6.x; R304P has no chapter 1.x or 15/16
  beyond what is listed; the corpus has no PRA, no technical specifications, no emergency plan, no
  regulatory guides, no current docket.

---

## 8. If the corpus does not answer it

Say so, then name the document that would. The highest-value additions (already listed in
`MASTER_TABLE_OF_CONTENTS.md` §7) are: NUREG-0800 (Standard Review Plan), 10 CFR 50,
NUREG-1150 / NUREG-1465 (severe accidents and source term), INSAG-1 (for the revision history),
IAEA INSAG-3 / SF-1 (safety principles), the IAEA 1996 Chernobyl consequences report, a BWR/6 or
ABWR design control document, and NUREG-0654 for emergency planning.

For a plant-specific 4-loop Westinghouse PWR, `SOURCES/Vogtle_UFSAR/` already holds the Vogtle
Units 1 & 2 UFSAR Rev 20 (31 PDFs, 9,340 pages, split by chapter). It is a source PDF set, not
Markdown: open it only when a question needs plant-specific PWR numbers that R304P does not give.
See [`SOURCES/Vogtle_UFSAR/README.md`](SOURCES/Vogtle_UFSAR/README.md) for the chapter map.

---

## 9. Style for answers

- Lead with the direct answer, then the mechanism, then the citation.
- Use the document's own vocabulary (BWR "scram"/"SRV"; PWR "trip"/"PORV"; RBMK "ORM"/"AZ-5").
- Distinguish **design basis** (what the plant is licensed to withstand) from **operating practice**
  (what the procedures say) from **beyond design basis** (what the corpus mostly does not cover).
- When two documents disagree, name both and explain which governs and why.
- Never invent setpoints, dimensions, or timestamps. If it is not in the text, say where it would be.
