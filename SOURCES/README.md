# SOURCES — original PDFs

The PDFs this corpus was extracted from, one folder per document, named exactly like the
Markdown folders at the repository root. They are here so that any statement in the Markdown
can be checked against the page it came from.

| Folder | Files | Size | What it is |
|---|---|---|---|
| [`R304B/`](R304B/) | 57 PDFs | 41 MB | GE BWR Systems Technology Manual (USNRC HRTD, Rev 09/11), one PDF per GE chapter |
| [`R304P/`](R304P/) | 1 PDF | 26 MB | Westinghouse PWR Systems Technology Manual (USNRC HRTD), `ML20057E160.pdf`, 1,127 pp. |
| [`CGS_FSAR/`](CGS_FSAR/chapters/) | 16 PDFs | 462 MB | Columbia Generating Station FSAR Amendment 67, split into chapter parts that together hold all 5,262 pages (largest 92 MB) |
| [`INSAG-7/`](INSAG-7/) | 1 PDF | 7.2 MB | IAEA INSAG-7, *The Chernobyl Accident: Updating of INSAG-1*, `Pub913e_web.pdf`, 148 pp. |
| [`Vogtle_UFSAR/`](Vogtle_UFSAR/README.md) | 31 PDFs | 1,060 MB | Vogtle Units 1 & 2 UFSAR Rev 20, split at chapter boundaries (9,340 pp.; largest file 87 MB) |

## Single-file sources (checksums)

| File | Pages | SHA-256 |
|---|---|---|
| `R304P/ML20057E160.pdf` | 1,127 | `ce0b68ee…f1a4856070` |
| `INSAG-7/Pub913e_web.pdf` | 148 | `75627db8…e21152455` |

<details><summary>Full SHA-256 values</summary>

```
ce0b68ee2eead6d8383b23dc31ce001cbbe13c94d234152699f5ccf1a4856070  R304P/ML20057E160.pdf
75627db871b8cec591eaf9443ef32da70e6ccb72c34c38b01c18933e21152455  INSAG-7/Pub913e_web.pdf
```

</details>

## Where the files came from

- **R304B** — `NRC_R304/R304B/`, originally downloaded per chapter from the NRC Reactor Systems
  Training Program material (also mirrored on the NRC ADAMS / HRTD pages).
- **R304P** — `ML20057E160.pdf`, NRC ADAMS.
- **CGS_FSAR** — the Energy Northwest / NRC submission compiling Columbia's FSAR through Amendment
  67, split at chapter boundaries. The filenames give each part's original page range; together the
  16 parts are continuous from p.1 to p.5262, i.e. they contain every page of the 5,262-page
  original with nothing dropped. This is also what the extraction pipeline used.
  To rebuild a single PDF: `python3 -c "import pymupdf,glob; o=pymupdf.open(); [o.insert_pdf(pymupdf.open(f)) for f in sorted(glob.glob('SOURCES/CGS_FSAR/chapters/*.pdf'))]; o.save('Amendment-67.pdf')"`.
- **INSAG-7** — `Pub913e_web.pdf`, IAEA publication 75-INSAG-7 (1992 scan).

## Note for the GitHub repository

Every file is **under 100 MB** (largest: `CGS_FSAR/chapters/03_chapter-660-1910.pdf`, 92 MB and
`Vogtle_UFSAR/reference-drawings_part4of5.pdf`, 87 MB), so all sources fit GitHub's per-file limit
without Git LFS. The whole repository is about 2.3 GB, above GitHub's *recommended* 1 GB but well
under the 5 GB soft limit. Two compiled monoliths were **not** kept, because their page content is
fully covered by the split parts: CGS Amendment 67 (404 MB; rebuilt from the 16 chapter parts) and
the merged Vogtle UFSAR (992 MB; rebuilt from the 31 chapter parts).

_Organised 2026-10-25. Verify a file with_ `sha256sum SOURCES/<path>`.
