# Master Table of Contents — Nuclear Industry Documents

A local, AI-readable corpus covering **three reactor technologies** — GE BWR/3 and BWR/5, a Westinghouse four-loop PWR, and the RBMK-1000 at Chernobyl — assembled from four primary documents that are commonly needed together: the two NRC/utility training manuals for BWR and PWR systems, the licensing basis of an operating BWR/5, and the IAEA's definitive Chernobyl report.

Everything here is **Markdown with figures embedded inline**, so a reader (human or model) gets prose and diagram in the same flow, and can cite an exact page. The PDFs the corpus was built from are kept in [`SOURCES/`](SOURCES/README.md), mirroring the document folder names, so any quoted passage can be checked against the original page.

All links in this repository are **relative** — clone it anywhere and they keep working.

---

## 1. Layout

```
Nuclear_Docs/
├── MASTER_TABLE_OF_CONTENTS.md   ← this file
├── SKILL.md                      ← operating instructions / skill for using the corpus
├── DOCKET_NUMBERS.md             ← NRC docket numbers, all 95 operating units + this corpus
├── SOURCES/                      ← the original PDFs, one folder per document
│   ├── R304B/                    ← 57 GE chapter PDFs
│   ├── R304P/                    ← ML20057E160.pdf (1,127 pp.)
│   ├── CGS_FSAR/                 ← 16 chapter parts (all 5,262 pages, no file >100 MB)
│   ├── INSAG-7/                  ← Pub913e_web.pdf (148 pp.)
│   └── Vogtle_UFSAR/             ← Vogtle 1 & 2 UFSAR Rev 20, 31 parts (9,340 pp.)
├── R304B/                        ← GE BWR Systems Technology Manual (BWR/3, BWR/5)
│   ├── TABLE_OF_CONTENTS.md
│   ├── FIGURE_INDEX.md
│   ├── chapters/                 ← one .md per GE chapter
│   └── figures/                  ← figure images (200 dpi PNG + lossless SVG where vector)
├── R304P/                        ← Westinghouse PWR Systems Technology Manual
│   └── (same structure)
├── CGS_FSAR/                     ← Columbia Generating Station FSAR, Amendment 67 (BWR/5)
│   └── (same structure, one .md per FSAR section)
└── INSAG-7/                      ← IAEA INSAG-7, Chernobyl (RBMK-1000)
    └── (same structure)
```

Every chapter file starts with a header giving its document, source PDF, and source page range, then uses `<!-- p.N -->` comments to mark original PDF page boundaries so quotes can be cited precisely.

Docket numbers for every operating U.S. power reactor — including the dockets for this corpus — are in [`DOCKET_NUMBERS.md`](DOCKET_NUMBERS.md). Use it to go from a plant name to `50-xxx` / `05000xxx` (or `52-025` for a combined licence) and then into ADAMS.

---

## 2. Document map

| Folder | Document | Type | Plant | Size | What it answers |
|---|---|---|---|---|---|
| [`R304B/`](R304B/TABLE_OF_CONTENTS.md) | R304B — GE BWR Systems Technology Manual | NRC/GE training manual | BWR/3, BWR/5 | 57 files, 338 figures | Systems-level "how it works" for every BWR system. Purpose, components, features, operator interfaces. |
| [`R304P/`](R304P/TABLE_OF_CONTENTS.md) | R304P — Westinghouse PWR Systems Technology Manual | NRC/Westinghouse training manual | Westinghouse 4-loop PWR | 51 files, 387 figures | The PWR counterpart to R304B: RCS, CVCS, ECCS, containment, rod control, RPS/ESFAS, instrumentation. |
| [`CGS_FSAR/`](CGS_FSAR/TABLE_OF_CONTENTS.md) | CGS FSAR — Columbia Generating Station FSAR, Amendment 67 | Plant licensing basis (FSAR) | BWR/5, Mark II containment | 105 files, 744 figures | The licensed, plant-specific truth: design bases, materials, setpoints, analyses, commitments, accidents. |
| [`INSAG-7/`](INSAG-7/TABLE_OF_CONTENTS.md) | INSAG-7 — The Chernobyl Accident: Updating of INSAG-1 | IAEA international accident report | RBMK-1000 (Chernobyl 4) | 16 files, 11 figures | Definitive account of the Chernobyl disaster: design defects, accident sequence, operator actions, safety culture. |

### How the four fit together

- **R304B** and **R304P** are *teaching* documents: ideal for explaining how a system works and what its components are. They are generic vendor designs, not one specific plant.
- **CGS_FSAR** is the *licensing* document for one real BWR/5. Use it when you need the as-built answer, a number, a setpoint, an acceptance criterion, or the regulatory commitment behind a design feature.
- **INSAG-7** is the *forensic* document: an accident investigation with a design, physics, human-factors and regulatory dimension. It is the reference for anything Chernobyl/RBMK, and the origin of “safety culture” as a formal nuclear safety concept.
- BWR pair (R304B + CGS_FSAR) gives generic-vs-plant-specific coverage of the same technology.
- PWR manual (R304P) provides the contrast case for almost every BWR function.

---

## 3. The documents

### 3.1 R304B — GE BWR Systems Technology Manual

**Type:** NRC/GE training manual  
**Primary reference design:** GE BWR/4
**Additional coverage:** BWR/3 and BWR/5 design differences and shared systems
**Source PDFs:** [`SOURCES/R304B/`](SOURCES/R304B/) — 57 chapter PDFs, 41 MB  
**Detailed TOC:** [`R304B/TABLE_OF_CONTENTS.md`](R304B/TABLE_OF_CONTENTS.md)  
**Figures:** [`R304B/FIGURE_INDEX.md`](R304B/FIGURE_INDEX.md)

USNRC HRTD re-issue of the GE **Systems Technology Manual**. Explains each BWR system as purpose → description → components → features → interfaces → summary. This is the material a BWR licensed operator is trained from, so it is precise about what the plant does and what the operator sees, without drowning in licensing analysis.

**What it is good for**

- System-level explanation and component anatomy (jet pumps, CRD, MSIVs, SRVs, RCIC turbine).
- Operator indications, setpoints, interlocks, failure modes and system interfaces.
- BWR/3 vs BWR/5 differences and why they matter.
- Onboarding: read 1.7–1.9 then the system chapters in plant order.

**Chapters / sections**

| File | Section |
|---|---|
| [`01.7_Reactor_Physics.md`](R304B/chapters/01.7_Reactor_Physics.md) | 1.7 Reactor Physics |
| [`01.8_Thermal_Limits.md`](R304B/chapters/01.8_Thermal_Limits.md) | 1.8 Thermal Limits |
| [`01.9_Chemistry.md`](R304B/chapters/01.9_Chemistry.md) | 1.9 Chemistry |
| [`02.0_Primary_Aux_Systems.md`](R304B/chapters/02.0_Primary_Aux_Systems.md) | 2.0 Primary Aux Systems |
| [`02.1_Reactor_Vessel.md`](R304B/chapters/02.1_Reactor_Vessel.md) | 2.1 Reactor Vessel |
| [`02.2_Fuel_Control_Rods.md`](R304B/chapters/02.2_Fuel_Control_Rods.md) | 2.2 Fuel Control Rods |
| [`02.3_Control_Rod_Drive.md`](R304B/chapters/02.3_Control_Rod_Drive.md) | 2.3 Control Rod Drive |
| [`02.4_Recirculation.md`](R304B/chapters/02.4_Recirculation.md) | 2.4 Recirculation |
| [`02.5_Main_Steam.md`](R304B/chapters/02.5_Main_Steam.md) | 2.5 Main Steam |
| [`02.6_Condensate_Feedwater.md`](R304B/chapters/02.6_Condensate_Feedwater.md) | 2.6 Condensate Feedwater |
| [`02.7_RCIC.md`](R304B/chapters/02.7_RCIC.md) | 2.7 RCIC |
| [`02.8_RW_Cleanup.md`](R304B/chapters/02.8_RW_Cleanup.md) | 2.8 RW Cleanup |
| [`03.0_Process_Instrumentation.md`](R304B/chapters/03.0_Process_Instrumentation.md) | 3.0 Process Instrumentation |
| [`03.1_RV_Instrumentation.md`](R304B/chapters/03.1_RV_Instrumentation.md) | 3.1 RV Instrumentation |
| [`03.2_Electro_Hydraulic_Control.md`](R304B/chapters/03.2_Electro_Hydraulic_Control.md) | 3.2 Electro Hydraulic Control |
| [`03.3_Feedwater_Level_Control.md`](R304B/chapters/03.3_Feedwater_Level_Control.md) | 3.3 Feedwater Level Control |
| [`04.0_Containment_Intro.md`](R304B/chapters/04.0_Containment_Intro.md) | 4.0 Containment Intro |
| [`04.1_Primary_Containment.md`](R304B/chapters/04.1_Primary_Containment.md) | 4.1 Primary Containment |
| [`04.2_Secondary_Containment.md`](R304B/chapters/04.2_Secondary_Containment.md) | 4.2 Secondary Containment |
| [`04.3_RB_Standby_Ventilation.md`](R304B/chapters/04.3_RB_Standby_Ventilation.md) | 4.3 RB Standby Ventilation |
| [`04.4_NSSS_Shutoff.md`](R304B/chapters/04.4_NSSS_Shutoff.md) | 4.4 NSSS Shutoff |
| [`05.0_Neutron_Monitoring_Intro.md`](R304B/chapters/05.0_Neutron_Monitoring_Intro.md) | 5.0 Neutron Monitoring Intro |
| [`05.1_Source_Range.md`](R304B/chapters/05.1_Source_Range.md) | 5.1 Source Range |
| [`05.2_Intermediate_Range.md`](R304B/chapters/05.2_Intermediate_Range.md) | 5.2 Intermediate Range |
| [`05.3_Local_Power_Range.md`](R304B/chapters/05.3_Local_Power_Range.md) | 5.3 Local Power Range |
| [`05.4_Average_Power_Range.md`](R304B/chapters/05.4_Average_Power_Range.md) | 5.4 Average Power Range |
| [`05.5_Rod_Block.md`](R304B/chapters/05.5_Rod_Block.md) | 5.5 Rod Block |
| [`05.6_TIP.md`](R304B/chapters/05.6_TIP.md) | 5.6 TIP |
| [`07.0_Reactivity_Control_Intro.md`](R304B/chapters/07.0_Reactivity_Control_Intro.md) | 7.0 Reactivity Control Intro |
| [`07.1_Reactor_Manual_Control.md`](R304B/chapters/07.1_Reactor_Manual_Control.md) | 7.1 Reactor Manual Control |
| [`07.2_Recirc_Flow_Control.md`](R304B/chapters/07.2_Recirc_Flow_Control.md) | 7.2 Recirc Flow Control |
| [`07.3_Reactor_Protection.md`](R304B/chapters/07.3_Reactor_Protection.md) | 7.3 Reactor Protection |
| [`07.4_SLC.md`](R304B/chapters/07.4_SLC.md) | 7.4 SLC |
| [`07.5_RWM.md`](R304B/chapters/07.5_RWM.md) | 7.5 RWM |
| [`08.0_Radwaste_Intro.md`](R304B/chapters/08.0_Radwaste_Intro.md) | 8.0 Radwaste Intro |
| [`08.1_Offgas.md`](R304B/chapters/08.1_Offgas.md) | 8.1 Offgas |
| [`08.2_Liquid_Radwaste.md`](R304B/chapters/08.2_Liquid_Radwaste.md) | 8.2 Liquid Radwaste |
| [`08.3_Solid_Radwaste.md`](R304B/chapters/08.3_Solid_Radwaste.md) | 8.3 Solid Radwaste |
| [`09.0_Electrical_Intro.md`](R304B/chapters/09.0_Electrical_Intro.md) | 9.0 Electrical Intro |
| [`09.1_Normal_AC_Power.md`](R304B/chapters/09.1_Normal_AC_Power.md) | 9.1 Normal AC Power |
| [`09.2_Emergency_AC_Power.md`](R304B/chapters/09.2_Emergency_AC_Power.md) | 9.2 Emergency AC Power |
| [`09.3_120VAC_Power.md`](R304B/chapters/09.3_120VAC_Power.md) | 9.3 120VAC Power |
| [`09.4_DC_Power.md`](R304B/chapters/09.4_DC_Power.md) | 9.4 DC Power |
| [`10.0_ECCS_Intro.md`](R304B/chapters/10.0_ECCS_Intro.md) | 10.0 ECCS Intro |
| [`10.1_HPCI.md`](R304B/chapters/10.1_HPCI.md) | 10.1 HPCI |
| [`10.2_ADS.md`](R304B/chapters/10.2_ADS.md) | 10.2 ADS |
| [`10.3_Core_Spray.md`](R304B/chapters/10.3_Core_Spray.md) | 10.3 Core Spray |
| [`10.4_RHR.md`](R304B/chapters/10.4_RHR.md) | 10.4 RHR |
| [`10.5_ECCS_Wrapup.md`](R304B/chapters/10.5_ECCS_Wrapup.md) | 10.5 ECCS Wrapup |
| [`11.0_Plant_Support_Intro.md`](R304B/chapters/11.0_Plant_Support_Intro.md) | 11.0 Plant Support Intro |
| [`11.1_Circulating_Water.md`](R304B/chapters/11.1_Circulating_Water.md) | 11.1 Circulating Water |
| [`11.2_RB_Service_Water.md`](R304B/chapters/11.2_RB_Service_Water.md) | 11.2 RB Service Water |
| [`11.3_RB_Closed_Loop.md`](R304B/chapters/11.3_RB_Closed_Loop.md) | 11.3 RB Closed Loop |
| [`11.4_Turbine_Service_Water.md`](R304B/chapters/11.4_Turbine_Service_Water.md) | 11.4 Turbine Service Water |
| [`11.5_TB_Closed_Loop.md`](R304B/chapters/11.5_TB_Closed_Loop.md) | 11.5 TB Closed Loop |
| [`11.6_Service_Instrument_Air.md`](R304B/chapters/11.6_Service_Instrument_Air.md) | 11.6 Service Instrument Air |
| [`11.7_Fuel_Pool_Cooling.md`](R304B/chapters/11.7_Fuel_Pool_Cooling.md) | 11.7 Fuel Pool Cooling |

### 3.2 R304P — Westinghouse PWR Systems Technology Manual

**Type:** NRC/Westinghouse training manual  
**Covers:** Westinghouse 4-loop PWR  
**Source PDF:** [`SOURCES/R304P/ML20057E160.pdf`](SOURCES/R304P/ML20057E160.pdf) (1,127 pp., 26 MB)  
**Detailed TOC:** [`R304P/TABLE_OF_CONTENTS.md`](R304P/TABLE_OF_CONTENTS.md)  
**Figures:** [`R304P/FIGURE_INDEX.md`](R304P/FIGURE_INDEX.md)

USNRC HRTD **Westinghouse Technology Systems Manual** for a four-loop Westinghouse PWR with 17×17 fuel, RCCAs and recirculating U-tube steam generators. Same didactic structure as R304B, adapted to PWR systems, including pressurizer and steam generator level control.

**What it is good for**

- PWR system explanation equivalent to R304B (RCS, CVCS, RHR, ECCS, AFW, steam dump).
- PWR-specific hardware: reactor internals, RCCAs/CRDMs, pressurizer, SGs, ARPI/DRPI.
- Protection and control: rod control, RPS trip signals, ESFAS, ex-core/in-core neutron monitoring.
- Side-by-side BWR vs PWR comparison of the same function.

**Chapters / sections**

| File | Section |
|---|---|
| [`0.1_Approved_Acronyms.md`](R304P/chapters/0.1_Approved_Acronyms.md) | 0.1 Approved Acronyms |
| [`0.1_NUREG_0544_Abbreviations_ML17004A106.md`](R304P/chapters/0.1_NUREG_0544_Abbreviations_ML17004A106.md) | 0.1 NUREG-0544 Abbreviations ML17004A106 |
| [`01.2_Intro_to_PWR.md`](R304P/chapters/01.2_Intro_to_PWR.md) | 01.2 Intro to PWR |
| [`02.0_Core_Characteristics.md`](R304P/chapters/02.0_Core_Characteristics.md) | 02.0 Core Characteristics |
| [`02.1_Rx_Physics_Review.md`](R304P/chapters/02.1_Rx_Physics_Review.md) | 02.1 Rx Physics Review |
| [`02.1_Rx_Physics_Review_rev.md`](R304P/chapters/02.1_Rx_Physics_Review_rev.md) | 02.1 Rx Physics Review rev |
| [`02.2_Power_Distribution_Limits.md`](R304P/chapters/02.2_Power_Distribution_Limits.md) | 02.2 Power Distribution Limits |
| [`03.0_RCS.md`](R304P/chapters/03.0_RCS.md) | 03.0 RCS |
| [`03.1_Rx_Vessel_and_Internals.md`](R304P/chapters/03.1_Rx_Vessel_and_Internals.md) | 03.1 Rx Vessel and Internals |
| [`03.2_Reactor_Coolant_System.md`](R304P/chapters/03.2_Reactor_Coolant_System.md) | 03.2 Reactor Coolant System |
| [`04.1_CVCS.md`](R304P/chapters/04.1_CVCS.md) | 04.1 CVCS |
| [`05.0_Intro_to_ESF.md`](R304P/chapters/05.0_Intro_to_ESF.md) | 05.0 Intro to ESF |
| [`05.1_RHR.md`](R304P/chapters/05.1_RHR.md) | 05.1 RHR |
| [`05.2_ECCS.md`](R304P/chapters/05.2_ECCS.md) | 05.2 ECCS |
| [`05.3_Containment.md`](R304P/chapters/05.3_Containment.md) | 05.3 Containment |
| [`05.4_CTMT_Temp_Press_Gas_Control.md`](R304P/chapters/05.4_CTMT_Temp_Press_Gas_Control.md) | 05.4 CTMT Temp Press Gas Control |
| [`05.6_CTMT_Isolation.md`](R304P/chapters/05.6_CTMT_Isolation.md) | 05.6 CTMT Isolation |
| [`05.8_AFW.md`](R304P/chapters/05.8_AFW.md) | 05.8 AFW |
| [`06.0_Elect_dist.md`](R304P/chapters/06.0_Elect_dist.md) | 06.0 Elect dist |
| [`07.1_Main_Aux_Stm.md`](R304P/chapters/07.1_Main_Aux_Stm.md) | 07.1 Main & Aux Stm |
| [`07.2_Condensate_and_Feedwater.md`](R304P/chapters/07.2_Condensate_and_Feedwater.md) | 07.2 Condensate and Feedwater |
| [`07.4_GE_Turb_Aux.md`](R304P/chapters/07.4_GE_Turb_Aux.md) | 07.4 GE Turb & Aux |
| [`07_Secondary_Systems.md`](R304P/chapters/07_Secondary_Systems.md) | 07 Secondary Systems |
| [`08.0_Rod_Control_and_Instrumentation.md`](R304P/chapters/08.0_Rod_Control_and_Instrumentation.md) | 08.0 Rod Control and Instrumentation |
| [`08.1_Rod_Control.md`](R304P/chapters/08.1_Rod_Control.md) | 08.1 Rod Control |
| [`08.2_ARPI.md`](R304P/chapters/08.2_ARPI.md) | 08.2 ARPI |
| [`08.3_DRPI.md`](R304P/chapters/08.3_DRPI.md) | 08.3 DRPI |
| [`08.4_RIL.md`](R304P/chapters/08.4_RIL.md) | 08.4 RIL |
| [`09.0_Neutron_Monitoring.md`](R304P/chapters/09.0_Neutron_Monitoring.md) | 09.0 Neutron Monitoring |
| [`09.1_Excores.md`](R304P/chapters/09.1_Excores.md) | 09.1 Excores |
| [`09.2_Incores.md`](R304P/chapters/09.2_Incores.md) | 09.2 Incores |
| [`0_Cover.md`](R304P/chapters/0_Cover.md) | 0 Cover |
| [`10.0_Primary_Instrumentation.md`](R304P/chapters/10.0_Primary_Instrumentation.md) | 10.0 Primary Instrumentation |
| [`10.1_RCS_Instrumentation.md`](R304P/chapters/10.1_RCS_Instrumentation.md) | 10.1 RCS Instrumentation |
| [`10.2_Pzr_Press_Control.md`](R304P/chapters/10.2_Pzr_Press_Control.md) | 10.2 Pzr Press Control |
| [`10.3_Pzr_Level_Control.md`](R304P/chapters/10.3_Pzr_Level_Control.md) | 10.3 Pzr Level Control |
| [`11.1_SGWLC.md`](R304P/chapters/11.1_SGWLC.md) | 11.1 SGWLC |
| [`11.2_Steam_Dump.md`](R304P/chapters/11.2_Steam_Dump.md) | 11.2 Steam Dump |
| [`11.5_GE_EHC.md`](R304P/chapters/11.5_GE_EHC.md) | 11.5 GE EHC |
| [`12.1_RPS.md`](R304P/chapters/12.1_RPS.md) | 12.1 RPS |
| [`12.2_RPS_Reactor_Trip_Signals.md`](R304P/chapters/12.2_RPS_Reactor_Trip_Signals.md) | 12.2 RPS Reactor Trip Signals |
| [`12.3_RPS_ESFAS.md`](R304P/chapters/12.3_RPS_ESFAS.md) | 12.3 RPS - ESFAS |
| [`13.0_Inst_Air.md`](R304P/chapters/13.0_Inst_Air.md) | 13.0 Inst Air |
| [`14.4_Spent_Fuel_Cooling.md`](R304P/chapters/14.4_Spent_Fuel_Cooling.md) | 14.4 Spent Fuel Cooling |
| [`14.5_CCW.md`](R304P/chapters/14.5_CCW.md) | 14.5 CCW |
| [`14.6_Service_Water.md`](R304P/chapters/14.6_Service_Water.md) | 14.6 Service Water |
| [`14.7_CW_and_TBCW.md`](R304P/chapters/14.7_CW_and_TBCW.md) | 14.7 CW and TBCW |
| [`16.0_Rad_Monitoring.md`](R304P/chapters/16.0_Rad_Monitoring.md) | 16.0 Rad Monitoring |
| [`17.1_Fuel_Handling.md`](R304P/chapters/17.1_Fuel_Handling.md) | 17.1 Fuel Handling |
| [`17.2_Spent_Fuel_Storage.md`](R304P/chapters/17.2_Spent_Fuel_Storage.md) | 17.2 Spent Fuel Storage |
| [`18.0_Computer.md`](R304P/chapters/18.0_Computer.md) | 18.0 Computer |

### 3.3 CGS FSAR — Columbia Generating Station FSAR, Amendment 67

**Type:** Plant licensing basis (FSAR)  
**Covers:** BWR/5, Mark II containment  
**Docket:** `05000397` (50-397) — licence NPF-21  
**Source PDFs:** [`SOURCES/CGS_FSAR/chapters/`](SOURCES/CGS_FSAR/chapters/) — 16 parts, all 5,262 pages (largest 92 MB)  
**Detailed TOC:** [`CGS_FSAR/TABLE_OF_CONTENTS.md`](CGS_FSAR/TABLE_OF_CONTENTS.md)  
**Figures:** [`CGS_FSAR/FIGURE_INDEX.md`](CGS_FSAR/FIGURE_INDEX.md)

The **Final Safety Analysis Report** for Columbia Generating Station (Energy Northwest), a BWR/5 (Mark II containment) plant, as compiled through Amendment 67. It is the licensing basis: the plant-specific answer for design, materials, setpoints, analysis methods, acceptance criteria, and regulatory commitments in the Standard Review Plan chapter format.

**What it is good for**

- Plant-specific data: capacities, setpoints, materials, as-built system descriptions.
- Design-basis accident analysis (Chapter 15) — the numbers, not just the method.
- Regulatory conformance (1.8), GDC compliance (3.1), classification (3.2).
- Cross-check generic training material against a real licensed BWR/5.

**Chapters / sections**

| File | Section |
|---|---|
| **Chapter 00** | 1 section files |
| [`00.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/00.0_Chapter_Front_Matter.md) | 00.0 Chapter Front Matter |
| **Chapter 01** | 1 section files |
| [`01.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/01.0_Chapter_Front_Matter.md) | 01.0 Chapter Front Matter |
| **Chapter 1** | 8 section files |
| [`1.1_INTRODUCTION.md`](CGS_FSAR/chapters/1.1_INTRODUCTION.md) | 1.1 INTRODUCTION |
| [`1.2_GENERAL_PLANT_DESCRIPTION.md`](CGS_FSAR/chapters/1.2_GENERAL_PLANT_DESCRIPTION.md) | 1.2 GENERAL PLANT DESCRIPTION |
| [`1.3_COMPARISON_TABLES.md`](CGS_FSAR/chapters/1.3_COMPARISON_TABLES.md) | 1.3 COMPARISON TABLES |
| [`1.4_IDENTIFICATION_OF_AGENTS_AND_CONTRACTORS.md`](CGS_FSAR/chapters/1.4_IDENTIFICATION_OF_AGENTS_AND_CONTRACTORS.md) | 1.4 IDENTIFICATION OF AGENTS AND CONTRACTORS |
| [`1.5_REQUIREMENTS_FOR_FURTHER_TECHNICAL_INFORMATION.md`](CGS_FSAR/chapters/1.5_REQUIREMENTS_FOR_FURTHER_TECHNICAL_INFORMATION.md) | 1.5 REQUIREMENTS FOR FURTHER TECHNICAL INFORMATION |
| [`1.6_MATERIAL_INCORPORATED_BY_REFERENCE.md`](CGS_FSAR/chapters/1.6_MATERIAL_INCORPORATED_BY_REFERENCE.md) | 1.6 MATERIAL INCORPORATED BY REFERENCE |
| … | +2 more in `CGS_FSAR/chapters/` |
| **Chapter 02** | 1 section files |
| [`02.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/02.0_Chapter_Front_Matter.md) | 02.0 Chapter Front Matter |
| **Chapter 2** | 5 section files |
| [`2.1_GEOGRAPHY_AND_DEMOGRAPHY.md`](CGS_FSAR/chapters/2.1_GEOGRAPHY_AND_DEMOGRAPHY.md) | 2.1 GEOGRAPHY AND DEMOGRAPHY |
| [`2.2_Nearby_Industrial_Transportation_And_Military_Facilitie.md`](CGS_FSAR/chapters/2.2_Nearby_Industrial_Transportation_And_Military_Facilitie.md) | 2.2 Nearby Industrial, Transportation, And Military Facilities |
| [`2.3_METEOROLOGY.md`](CGS_FSAR/chapters/2.3_METEOROLOGY.md) | 2.3 METEOROLOGY |
| [`2.4_HYDROLOGY_ENGINEERING.md`](CGS_FSAR/chapters/2.4_HYDROLOGY_ENGINEERING.md) | 2.4 HYDROLOGY ENGINEERING |
| [`2.5_GEOLOGY_SEISMOLOGY_AND_GEOTECHNICAL_ENGINEERING.md`](CGS_FSAR/chapters/2.5_GEOLOGY_SEISMOLOGY_AND_GEOTECHNICAL_ENGINEERING.md) | 2.5 GEOLOGY, SEISMOLOGY, AND GEOTECHNICAL ENGINEERING |
| **Chapter 03** | 1 section files |
| [`03.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/03.0_Chapter_Front_Matter.md) | 03.0 Chapter Front Matter |
| **Chapter 3** | 12 section files |
| [`3.10_Seismic_And_Dynamic_Qualification_Of_Safety_Related.md`](CGS_FSAR/chapters/3.10_Seismic_And_Dynamic_Qualification_Of_Safety_Related.md) | 3.10 Seismic And Dynamic Qualification Of Safety-Related |
| [`3.11_Environmental_Design_Of_Mechanical_And_Electrical.md`](CGS_FSAR/chapters/3.11_Environmental_Design_Of_Mechanical_And_Electrical.md) | 3.11 Environmental Design Of Mechanical And Electrical |
| [`3.12_Computer_Programs_For_Structural_Analysis_And_Design.md`](CGS_FSAR/chapters/3.12_Computer_Programs_For_Structural_Analysis_And_Design.md) | 3.12 Computer Programs For Structural Analysis And Design |
| [`3.1_Conformance_With_Nrc_General_Design_Criteria.md`](CGS_FSAR/chapters/3.1_Conformance_With_Nrc_General_Design_Criteria.md) | 3.1 Conformance With Nrc General Design Criteria |
| [`3.2_Classification_Of_Structures_Components_And_Systems.md`](CGS_FSAR/chapters/3.2_Classification_Of_Structures_Components_And_Systems.md) | 3.2 Classification Of Structures, Components, And Systems |
| [`3.3_WIND_AND_TORNADO_LOADINGS.md`](CGS_FSAR/chapters/3.3_WIND_AND_TORNADO_LOADINGS.md) | 3.3 WIND AND TORNADO LOADINGS |
| … | +6 more in `CGS_FSAR/chapters/` |
| **Chapter 04** | 1 section files |
| [`04.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/04.0_Chapter_Front_Matter.md) | 04.0 Chapter Front Matter |
| **Chapter 4** | 6 section files |
| [`4.1_Summary_Description.md`](CGS_FSAR/chapters/4.1_Summary_Description.md) | 4.1 Summary Description |
| [`4.2_FUEL_SYSTEM_DESIGN.md`](CGS_FSAR/chapters/4.2_FUEL_SYSTEM_DESIGN.md) | 4.2 FUEL SYSTEM DESIGN |
| [`4.3_NUCLEAR_DESIGN.md`](CGS_FSAR/chapters/4.3_NUCLEAR_DESIGN.md) | 4.3 NUCLEAR DESIGN |
| [`4.4_THERMAL_HYDRAULIC_DESIGN.md`](CGS_FSAR/chapters/4.4_THERMAL_HYDRAULIC_DESIGN.md) | 4.4 THERMAL-HYDRAULIC DESIGN |
| [`4.5_REACTOR_MATERIALS.md`](CGS_FSAR/chapters/4.5_REACTOR_MATERIALS.md) | 4.5 REACTOR MATERIALS |
| [`4.6_FUNCTIONAL_DESIGN_OF_REACTIVITY_CONTROL_SYSTEMS.md`](CGS_FSAR/chapters/4.6_FUNCTIONAL_DESIGN_OF_REACTIVITY_CONTROL_SYSTEMS.md) | 4.6 FUNCTIONAL DESIGN OF REACTIVITY CONTROL SYSTEMS |
| **Chapter 05** | 1 section files |
| [`05.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/05.0_Chapter_Front_Matter.md) | 05.0 Chapter Front Matter |
| **Chapter 5** | 4 section files |
| [`5.1_Summary_Description.md`](CGS_FSAR/chapters/5.1_Summary_Description.md) | 5.1 Summary Description |
| [`5.2_Integrity_Of_Reactor_Coolant_Pressure_Boundary.md`](CGS_FSAR/chapters/5.2_Integrity_Of_Reactor_Coolant_Pressure_Boundary.md) | 5.2 Integrity Of Reactor Coolant Pressure Boundary |
| [`5.3_REACTOR_VESSEL.md`](CGS_FSAR/chapters/5.3_REACTOR_VESSEL.md) | 5.3 REACTOR VESSEL |
| [`5.4_COMPONENT_AND_SUBSYSTEM_DESIGN.md`](CGS_FSAR/chapters/5.4_COMPONENT_AND_SUBSYSTEM_DESIGN.md) | 5.4 COMPONENT AND SUBSYSTEM DESIGN |
| **Chapter 06** | 1 section files |
| [`06.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/06.0_Chapter_Front_Matter.md) | 06.0 Chapter Front Matter |
| **Chapter 6** | 7 section files |
| [`6.1_ENGINEERED_SAFETY_FEATURE_MATERIALS.md`](CGS_FSAR/chapters/6.1_ENGINEERED_SAFETY_FEATURE_MATERIALS.md) | 6.1 ENGINEERED SAFETY FEATURE MATERIALS |
| [`6.2_CONTAINMENT_SYSTEMS.md`](CGS_FSAR/chapters/6.2_CONTAINMENT_SYSTEMS.md) | 6.2 CONTAINMENT SYSTEMS |
| [`6.3_EMERGENCY_CORE_COOLING_SYSTEM.md`](CGS_FSAR/chapters/6.3_EMERGENCY_CORE_COOLING_SYSTEM.md) | 6.3 EMERGENCY CORE COOLING SYSTEM |
| [`6.4_HABITABILITY_SYSTEMS.md`](CGS_FSAR/chapters/6.4_HABITABILITY_SYSTEMS.md) | 6.4 HABITABILITY SYSTEMS |
| [`6.5_FISSION_PRODUCT_REMOVAL_AND_CONTROL_SYSTEMS.md`](CGS_FSAR/chapters/6.5_FISSION_PRODUCT_REMOVAL_AND_CONTROL_SYSTEMS.md) | 6.5 FISSION PRODUCT REMOVAL AND CONTROL SYSTEMS |
| [`6.6_Inservice_Inspection_Of_Asme_Code_Class_2_And_Class_3.md`](CGS_FSAR/chapters/6.6_Inservice_Inspection_Of_Asme_Code_Class_2_And_Class_3.md) | 6.6 Inservice Inspection Of Asme Code Class 2 And Class 3 |
| … | +1 more in `CGS_FSAR/chapters/` |
| **Chapter 07** | 1 section files |
| [`07.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/07.0_Chapter_Front_Matter.md) | 07.0 Chapter Front Matter |
| **Chapter 7** | 7 section files |
| [`7.1_INTRODUCTION.md`](CGS_FSAR/chapters/7.1_INTRODUCTION.md) | 7.1 INTRODUCTION |
| [`7.2_REACTOR_PROTECTION_TRIP_SYSTEM.md`](CGS_FSAR/chapters/7.2_REACTOR_PROTECTION_TRIP_SYSTEM.md) | 7.2 REACTOR PROTECTION (TRIP) SYSTEM |
| [`7.3_ENGINEERED_SAFETY_FEATURE_SYSTEMS.md`](CGS_FSAR/chapters/7.3_ENGINEERED_SAFETY_FEATURE_SYSTEMS.md) | 7.3 ENGINEERED SAFETY FEATURE SYSTEMS |
| [`7.4_SYSTEMS_REQUIRED_FOR_SAFE_SHUTDOWN.md`](CGS_FSAR/chapters/7.4_SYSTEMS_REQUIRED_FOR_SAFE_SHUTDOWN.md) | 7.4 SYSTEMS REQUIRED FOR SAFE SHUTDOWN |
| [`7.5_SAFETY_RELATED_DISPLAY_INSTRUMENTATION.md`](CGS_FSAR/chapters/7.5_SAFETY_RELATED_DISPLAY_INSTRUMENTATION.md) | 7.5 SAFETY-RELATED DISPLAY INSTRUMENTATION |
| [`7.6_All_Other_Instrumentation_Systems_Required_For_Safety.md`](CGS_FSAR/chapters/7.6_All_Other_Instrumentation_Systems_Required_For_Safety.md) | 7.6 All Other Instrumentation Systems Required For Safety |
| … | +1 more in `CGS_FSAR/chapters/` |
| **Chapter 08** | 1 section files |
| [`08.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/08.0_Chapter_Front_Matter.md) | 08.0 Chapter Front Matter |
| **Chapter 8** | 3 section files |
| [`8.1_INTRODUCTION.md`](CGS_FSAR/chapters/8.1_INTRODUCTION.md) | 8.1 INTRODUCTION |
| [`8.2_OFFSITE_POWER_SYSTEM.md`](CGS_FSAR/chapters/8.2_OFFSITE_POWER_SYSTEM.md) | 8.2 OFFSITE POWER SYSTEM |
| [`8.3_ONSITE_POWER_SYSTEMS.md`](CGS_FSAR/chapters/8.3_ONSITE_POWER_SYSTEMS.md) | 8.3 ONSITE POWER SYSTEMS |
| **Chapter 09** | 1 section files |
| [`09.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/09.0_Chapter_Front_Matter.md) | 09.0 Chapter Front Matter |
| **Chapter 9** | 5 section files |
| [`9.1_FUEL_STORAGE_AND_HANDLING.md`](CGS_FSAR/chapters/9.1_FUEL_STORAGE_AND_HANDLING.md) | 9.1 FUEL STORAGE AND HANDLING |
| [`9.2_WATER_SYSTEMS.md`](CGS_FSAR/chapters/9.2_WATER_SYSTEMS.md) | 9.2 WATER SYSTEMS |
| [`9.3_PROCESS_AUXILIARIES.md`](CGS_FSAR/chapters/9.3_PROCESS_AUXILIARIES.md) | 9.3 PROCESS AUXILIARIES |
| [`9.4_HEATING_VENTILATING_AND_AIR_CONDITIONING_SYSTEMS.md`](CGS_FSAR/chapters/9.4_HEATING_VENTILATING_AND_AIR_CONDITIONING_SYSTEMS.md) | 9.4 HEATING, VENTILATING, AND AIR CONDITIONING SYSTEMS |
| [`9.5_OTHER_AUXILIARY_SYSTEMS.md`](CGS_FSAR/chapters/9.5_OTHER_AUXILIARY_SYSTEMS.md) | 9.5 OTHER AUXILIARY SYSTEMS |
| **Chapter 10** | 5 section files |
| [`10.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/10.0_Chapter_Front_Matter.md) | 10.0 Chapter Front Matter |
| [`10.1_SUMMARY_DESCRIPTION.md`](CGS_FSAR/chapters/10.1_SUMMARY_DESCRIPTION.md) | 10.1 SUMMARY DESCRIPTION |
| [`10.2_TURBINE_GENERATOR.md`](CGS_FSAR/chapters/10.2_TURBINE_GENERATOR.md) | 10.2 TURBINE GENERATOR |
| [`10.3_MAIN_STEAM_SUPPLY_SYSTEM.md`](CGS_FSAR/chapters/10.3_MAIN_STEAM_SUPPLY_SYSTEM.md) | 10.3 MAIN STEAM SUPPLY SYSTEM |
| [`10.4_Other_Features_Of_Steam_And_Power_Conversion_System.md`](CGS_FSAR/chapters/10.4_Other_Features_Of_Steam_And_Power_Conversion_System.md) | 10.4 Other Features Of Steam And Power Conversion System |
| **Chapter 11** | 7 section files |
| [`11.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/11.0_Chapter_Front_Matter.md) | 11.0 Chapter Front Matter |
| [`11.1_Source_Terms.md`](CGS_FSAR/chapters/11.1_Source_Terms.md) | 11.1 Source Terms |
| [`11.2_Liquid_Waste_Management_System.md`](CGS_FSAR/chapters/11.2_Liquid_Waste_Management_System.md) | 11.2 Liquid Waste Management System |
| [`11.3_Gaseous_Waste_Management_Systems.md`](CGS_FSAR/chapters/11.3_Gaseous_Waste_Management_Systems.md) | 11.3 Gaseous Waste Management Systems |
| [`11.4_SOLID_WASTE_MANAGEMENT_SYSTEM.md`](CGS_FSAR/chapters/11.4_SOLID_WASTE_MANAGEMENT_SYSTEM.md) | 11.4 SOLID WASTE MANAGEMENT SYSTEM |
| [`11.5_Process_And_Effluent_Radiological_Monitoring_And_Sampli.md`](CGS_FSAR/chapters/11.5_Process_And_Effluent_Radiological_Monitoring_And_Sampli.md) | 11.5 Process And Effluent Radiological Monitoring And Sampling |
| … | +1 more in `CGS_FSAR/chapters/` |
| **Chapter 12** | 6 section files |
| [`12.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/12.0_Chapter_Front_Matter.md) | 12.0 Chapter Front Matter |
| [`12.1_Ensuring_That_Occupational_Radiation_Exposures_And.md`](CGS_FSAR/chapters/12.1_Ensuring_That_Occupational_Radiation_Exposures_And.md) | 12.1 Ensuring That Occupational Radiation Exposures And |
| [`12.2_RADIATION_SOURCES.md`](CGS_FSAR/chapters/12.2_RADIATION_SOURCES.md) | 12.2 RADIATION SOURCES |
| [`12.3_RADIATION_PROTECTION_DESIGN_FEATURES.md`](CGS_FSAR/chapters/12.3_RADIATION_PROTECTION_DESIGN_FEATURES.md) | 12.3 RADIATION PROTECTION DESIGN FEATURES |
| [`12.4_DOSE_ASSESSMENT.md`](CGS_FSAR/chapters/12.4_DOSE_ASSESSMENT.md) | 12.4 DOSE ASSESSMENT |
| [`12.5_RADIATION_PROTECTION_PROGRAM.md`](CGS_FSAR/chapters/12.5_RADIATION_PROTECTION_PROGRAM.md) | 12.5 RADIATION PROTECTION PROGRAM |
| **Chapter 13** | 6 section files |
| [`13.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/13.0_Chapter_Front_Matter.md) | 13.0 Chapter Front Matter |
| [`13.2_TRAINING.md`](CGS_FSAR/chapters/13.2_TRAINING.md) | 13.2 TRAINING |
| [`13.3_EMERGENCY_PLANNING.md`](CGS_FSAR/chapters/13.3_EMERGENCY_PLANNING.md) | 13.3 EMERGENCY PLANNING |
| [`13.4_REVIEW_AND_AUDIT.md`](CGS_FSAR/chapters/13.4_REVIEW_AND_AUDIT.md) | 13.4 REVIEW AND AUDIT |
| [`13.5_PLANT_PROCEDURES.md`](CGS_FSAR/chapters/13.5_PLANT_PROCEDURES.md) | 13.5 PLANT PROCEDURES |
| [`13.6_INDUSTRIAL_SECURITY.md`](CGS_FSAR/chapters/13.6_INDUSTRIAL_SECURITY.md) | 13.6 INDUSTRIAL SECURITY |
| **Chapter 14** | 3 section files |
| [`14.0_Chapter_Front_Matter.md`](CGS_FSAR/chapters/14.0_Chapter_Front_Matter.md) | 14.0 Chapter Front Matter |
| [`14.1_Specific_Information_Included_In_Preliminary_Safety.md`](CGS_FSAR/chapters/14.1_Specific_Information_Included_In_Preliminary_Safety.md) | 14.1 Specific Information Included In Preliminary Safety |
| [`14.2_System_Lineup_Preoperational_And_Initial_Startup_Test.md`](CGS_FSAR/chapters/14.2_System_Lineup_Preoperational_And_Initial_Startup_Test.md) | 14.2 System Lineup, Preoperational, And Initial Startup Test |
| **Chapter 15** | 9 section files |
| [`15.0_GENERAL.md`](CGS_FSAR/chapters/15.0_GENERAL.md) | 15.0 GENERAL |
| [`15.1_DECREASE_IN_REACTOR_COOLANT_TEMPERATURE.md`](CGS_FSAR/chapters/15.1_DECREASE_IN_REACTOR_COOLANT_TEMPERATURE.md) | 15.1 DECREASE IN REACTOR COOLANT TEMPERATURE |
| [`15.2_INCREASE_IN_REACTOR_PRESSURE.md`](CGS_FSAR/chapters/15.2_INCREASE_IN_REACTOR_PRESSURE.md) | 15.2 INCREASE IN REACTOR PRESSURE |
| [`15.3_DECREASE_IN_REACTOR_COOLANT_SYSTEM_FLOW_RATE.md`](CGS_FSAR/chapters/15.3_DECREASE_IN_REACTOR_COOLANT_SYSTEM_FLOW_RATE.md) | 15.3 DECREASE IN REACTOR COOLANT SYSTEM FLOW RATE |
| [`15.4_REACTIVITY_AND_POWER_DISTRIBUTION_ANOMALIES.md`](CGS_FSAR/chapters/15.4_REACTIVITY_AND_POWER_DISTRIBUTION_ANOMALIES.md) | 15.4 REACTIVITY AND POWER DISTRIBUTION ANOMALIES |
| [`15.5_INCREASE_IN_REACTOR_COOLANT_INVENTORY.md`](CGS_FSAR/chapters/15.5_INCREASE_IN_REACTOR_COOLANT_INVENTORY.md) | 15.5 INCREASE IN REACTOR COOLANT INVENTORY |
| … | +3 more in `CGS_FSAR/chapters/` |
| **Chapter 17** | 2 section files |
| [`17.1_Quality_Assurance_During_Design_And_Construction.md`](CGS_FSAR/chapters/17.1_Quality_Assurance_During_Design_And_Construction.md) | 17.1 Quality Assurance During Design And Construction |
| [`17.2_Quality_Assurance_During_The_Operations_Phase.md`](CGS_FSAR/chapters/17.2_Quality_Assurance_During_The_Operations_Phase.md) | 17.2 Quality Assurance During The Operations Phase |

### 3.4 INSAG-7 — The Chernobyl Accident: Updating of INSAG-1

**Type:** IAEA international accident report  
**Covers:** RBMK-1000 (Chernobyl 4)  
**Source PDF:** [`SOURCES/INSAG-7/Pub913e_web.pdf`](SOURCES/INSAG-7/Pub913e_web.pdf) (148 pp., 7 MB)  
**Detailed TOC:** [`INSAG-7/TABLE_OF_CONTENTS.md`](INSAG-7/TABLE_OF_CONTENTS.md)  
**Figures:** [`INSAG-7/FIGURE_INDEX.md`](INSAG-7/FIGURE_INDEX.md)

IAEA Safety Series No. 75-INSAG-7 (1992). The **authoritative post-Soviet account of Chernobyl** Unit 4. It corrects INSAG-1: the root cause is the **positive-scram control-rod design** acting at an **abnormally low operating reactivity margin**, with operator and regulatory failures as contributing factors. Contains the full SCSSINP Commission report (Annex I) and the USSR experts' report (Annex II).

**What it is good for**

- Minute-by-minute accident sequence and the physics behind each step.
- RBMK-1000 design: positive void coefficient, rod/displacer geometry, ORM, AZ-5.
- Safety culture, regulatory and management failure analysis.
- Debunking 1986-era misconceptions about operator error and ECCS blocking.

**Chapters / sections**

| File | Section |
|---|---|
| [`00_BIBLIOGRAPHY_TO_ANNEX_I.md`](INSAG-7/chapters/00_BIBLIOGRAPHY_TO_ANNEX_I.md) | BIBLIOGRAPHY TO ANNEX I |
| [`00_EDITORIAL_NOTE.md`](INSAG-7/chapters/00_EDITORIAL_NOTE.md) | EDITORIAL NOTE |
| [`00_FOREWORD.md`](INSAG-7/chapters/00_FOREWORD.md) | FOREWORD |
| [`00_LIST_OF_ACRONYMS_AND_SYMBOLS.md`](INSAG-7/chapters/00_LIST_OF_ACRONYMS_AND_SYMBOLS.md) | LIST OF ACRONYMS AND SYMBOLS |
| [`00_REFERENCES_TO_ANNEX_I.md`](INSAG-7/chapters/00_REFERENCES_TO_ANNEX_I.md) | REFERENCES TO ANNEX I |
| [`00_THE_CHERNOBYL_ACCIDENT_UPDATING_OF_INSAG_1_INSAG_7.md`](INSAG-7/chapters/00_THE_CHERNOBYL_ACCIDENT_UPDATING_OF_INSAG_1_INSAG_7.md) | THE CHERNOBYL ACCIDENT: UPDATING OF INSAG-1 INSAG-7 |
| [`1_INTRODUCTION.md`](INSAG-7/chapters/1_INTRODUCTION.md) | 1. INTRODUCTION |
| [`2_FEATURES_OF_THE_REACTOR.md`](INSAG-7/chapters/2_FEATURES_OF_THE_REACTOR.md) | 2. FEATURES OF THE REACTOR |
| [`3_THE_ACCIDENT.md`](INSAG-7/chapters/3_THE_ACCIDENT.md) | 3. THE ACCIDENT |
| [`4_MORE_RECENT_ANALYSES_OF_THE_FAULT_SCENARIO.md`](INSAG-7/chapters/4_MORE_RECENT_ANALYSES_OF_THE_FAULT_SCENARIO.md) | 4. MORE RECENT ANALYSES OF THE FAULT SCENARIO |
| [`5_VIEWS_OF_INSAG.md`](INSAG-7/chapters/5_VIEWS_OF_INSAG.md) | 5. VIEWS OF INSAG |
| [`6_CONCLUSIONS_ON_FACTORS_CONTRIBUTORY_TO_THE_ACCIDENT.md`](INSAG-7/chapters/6_CONCLUSIONS_ON_FACTORS_CONTRIBUTORY_TO_THE_ACCIDENT.md) | 6. CONCLUSIONS ON FACTORS CONTRIBUTORY TO THE ACCIDENT |
| [`A1_REPORT_BY_A_COMMISSION_TO_THE_USSR_STATE_COMMITTEE_FOR_THE_S.md`](INSAG-7/chapters/A1_REPORT_BY_A_COMMISSION_TO_THE_USSR_STATE_COMMITTEE_FOR_THE_S.md) | Annex I REPORT BY A COMMISSION TO THE USSR STATE COMMITTEE FOR THE SUPERVISION OF SAFETY IN INDUSTRY AND NUCLEAR POWER |
| [`A2_REPORT_BY_A_WORKING_GROUP_OF_USSR_EXPERTS.md`](INSAG-7/chapters/A2_REPORT_BY_A_WORKING_GROUP_OF_USSR_EXPERTS.md) | Annex II REPORT BY A WORKING GROUP OF USSR EXPERTS |
| [`AP_Appendix_MEASURES_TO_IMPROVE_THE_SAFETY_OF_RBMK_PLANTS.md`](INSAG-7/chapters/AP_Appendix_MEASURES_TO_IMPROVE_THE_SAFETY_OF_RBMK_PLANTS.md) | Appendix MEASURES TO IMPROVE THE SAFETY OF RBMK PLANTS |
| [`Z_References_Cyrillic.md`](INSAG-7/chapters/Z_References_Cyrillic.md) | БИБЛИOГPAФИЯ K ПPИЛOЖEHИIO I |

---

## 4. Topic map — where to look for what

Best entry points per topic, across all four documents. Chapter numbers are clickable; the per-document `TABLE_OF_CONTENTS.md` goes down to sub-subsection level.

| Topic | R304B (BWR) | R304P (PWR) | CGS FSAR (BWR/5 plant) | INSAG-7 (RBMK) |
|---|---|---|---|---|
| **Reactor physics & kinetics** | [1.7 Reactor Physics](R304B/chapters/01.7_Reactor_Physics.md) | [02.1 Rx Physics Review rev](R304P/chapters/02.1_Rx_Physics_Review_rev.md) | [4.3 NUCLEAR DESIGN](CGS_FSAR/chapters/4.3_NUCLEAR_DESIGN.md) | [2. FEATURES OF THE REACTOR](INSAG-7/chapters/2_FEATURES_OF_THE_REACTOR.md) |
| **Thermal limits / fuel thermal margin** | [1.8 Thermal Limits](R304B/chapters/01.8_Thermal_Limits.md) | [02.2 Power Distribution Limits](R304P/chapters/02.2_Power_Distribution_Limits.md) | [4.4 THERMAL-HYDRAULIC DESIGN](CGS_FSAR/chapters/4.4_THERMAL_HYDRAULIC_DESIGN.md) | — |
| **Fuel assembly & rod design** | [2.2 Fuel Control Rods](R304B/chapters/02.2_Fuel_Control_Rods.md) | [03.1 Rx Vessel and Internals](R304P/chapters/03.1_Rx_Vessel_and_Internals.md) | [4.2 FUEL SYSTEM DESIGN](CGS_FSAR/chapters/4.2_FUEL_SYSTEM_DESIGN.md) | — |
| **Control rods, CRD/CRDM, reactivity control** | [2.3 Control Rod Drive](R304B/chapters/02.3_Control_Rod_Drive.md)<br>[7.1 Reactor Manual Control](R304B/chapters/07.1_Reactor_Manual_Control.md) | [03.1 Rx Vessel and Internals](R304P/chapters/03.1_Rx_Vessel_and_Internals.md)<br>[08.1 Rod Control](R304P/chapters/08.1_Rod_Control.md) | [4.6 FUNCTIONAL DESIGN OF REACTIVITY CONTROL SYSTEMS](CGS_FSAR/chapters/4.6_FUNCTIONAL_DESIGN_OF_REACTIVITY_CONTROL_SYSTEMS.md) | [2. FEATURES OF THE REACTOR](INSAG-7/chapters/2_FEATURES_OF_THE_REACTOR.md) |
| **Reactor vessel & internals** | [2.1 Reactor Vessel](R304B/chapters/02.1_Reactor_Vessel.md) | [03.1 Rx Vessel and Internals](R304P/chapters/03.1_Rx_Vessel_and_Internals.md) | [5.3 REACTOR VESSEL](CGS_FSAR/chapters/5.3_REACTOR_VESSEL.md) | — |
| **Reactor coolant / recirculation** | [2.4 Recirculation](R304B/chapters/02.4_Recirculation.md) | [03.2 Reactor Coolant System](R304P/chapters/03.2_Reactor_Coolant_System.md) | [5.4 COMPONENT AND SUBSYSTEM DESIGN](CGS_FSAR/chapters/5.4_COMPONENT_AND_SUBSYSTEM_DESIGN.md) | — |
| **Main steam, MSIVs, SRVs, turbine** | [2.5 Main Steam](R304B/chapters/02.5_Main_Steam.md) | [07.1 Main & Aux Stm](R304P/chapters/07.1_Main_Aux_Stm.md)<br>[07.4 GE Turb & Aux](R304P/chapters/07.4_GE_Turb_Aux.md) | [10.3 MAIN STEAM SUPPLY SYSTEM](CGS_FSAR/chapters/10.3_MAIN_STEAM_SUPPLY_SYSTEM.md) | — |
| **Feedwater, condensate, level control** | [2.6 Condensate Feedwater](R304B/chapters/02.6_Condensate_Feedwater.md)<br>[3.3 Feedwater Level Control](R304B/chapters/03.3_Feedwater_Level_Control.md) | [07.2 Condensate and Feedwater](R304P/chapters/07.2_Condensate_and_Feedwater.md)<br>[11.1 SGWLC](R304P/chapters/11.1_SGWLC.md) | [7.7 CONTROL SYSTEMS NOT REQUIRED FOR SAFETY](CGS_FSAR/chapters/7.7_CONTROL_SYSTEMS_NOT_REQUIRED_FOR_SAFETY.md) | — |
| **ECCS / core cooling** | [10.0 ECCS Intro](R304B/chapters/10.0_ECCS_Intro.md)<br>[10.1 HPCI](R304B/chapters/10.1_HPCI.md)<br>[10.2 ADS](R304B/chapters/10.2_ADS.md)<br>[10.3 Core Spray](R304B/chapters/10.3_Core_Spray.md)<br>[10.4 RHR](R304B/chapters/10.4_RHR.md)<br>[10.5 ECCS Wrapup](R304B/chapters/10.5_ECCS_Wrapup.md) | [05.2 ECCS](R304P/chapters/05.2_ECCS.md) | [6.3 EMERGENCY CORE COOLING SYSTEM](CGS_FSAR/chapters/6.3_EMERGENCY_CORE_COOLING_SYSTEM.md) | — |
| **Containment & containment systems** | [4.1 Primary Containment](R304B/chapters/04.1_Primary_Containment.md)<br>[4.2 Secondary Containment](R304B/chapters/04.2_Secondary_Containment.md) | [05.3 Containment](R304P/chapters/05.3_Containment.md)<br>[05.4 CTMT Temp Press Gas Control](R304P/chapters/05.4_CTMT_Temp_Press_Gas_Control.md)<br>[05.6 CTMT Isolation](R304P/chapters/05.6_CTMT_Isolation.md) | [6.2 CONTAINMENT SYSTEMS](CGS_FSAR/chapters/6.2_CONTAINMENT_SYSTEMS.md) | — |
| **Neutron monitoring & instrumentation** | [5.1 Source Range](R304B/chapters/05.1_Source_Range.md)<br>[5.2 Intermediate Range](R304B/chapters/05.2_Intermediate_Range.md)<br>[5.3 Local Power Range](R304B/chapters/05.3_Local_Power_Range.md)<br>[5.4 Average Power Range](R304B/chapters/05.4_Average_Power_Range.md)<br>[5.5 Rod Block](R304B/chapters/05.5_Rod_Block.md)<br>[5.6 TIP](R304B/chapters/05.6_TIP.md) | [09.1 Excores](R304P/chapters/09.1_Excores.md)<br>[09.2 Incores](R304P/chapters/09.2_Incores.md) | [7.5 SAFETY-RELATED DISPLAY INSTRUMENTATION](CGS_FSAR/chapters/7.5_SAFETY_RELATED_DISPLAY_INSTRUMENTATION.md) | — |
| **Reactor protection / trips / ESFAS** | [7.3 Reactor Protection](R304B/chapters/07.3_Reactor_Protection.md) | [12.1 RPS](R304P/chapters/12.1_RPS.md)<br>[12.2 RPS Reactor Trip Signals](R304P/chapters/12.2_RPS_Reactor_Trip_Signals.md)<br>[12.3 RPS - ESFAS](R304P/chapters/12.3_RPS_ESFAS.md) | [7.2 REACTOR PROTECTION (TRIP) SYSTEM](CGS_FSAR/chapters/7.2_REACTOR_PROTECTION_TRIP_SYSTEM.md)<br>[7.3 ENGINEERED SAFETY FEATURE SYSTEMS](CGS_FSAR/chapters/7.3_ENGINEERED_SAFETY_FEATURE_SYSTEMS.md) | — |
| **Auxiliary & support systems (RCIC, RWCU, HVAC, air, water)** | [2.7 RCIC](R304B/chapters/02.7_RCIC.md)<br>[2.8 RW Cleanup](R304B/chapters/02.8_RW_Cleanup.md)<br>[11.1 Circulating Water](R304B/chapters/11.1_Circulating_Water.md)<br>[11.2 RB Service Water](R304B/chapters/11.2_RB_Service_Water.md)<br>[11.3 RB Closed Loop](R304B/chapters/11.3_RB_Closed_Loop.md)<br>[11.4 Turbine Service Water](R304B/chapters/11.4_Turbine_Service_Water.md)<br>[11.5 TB Closed Loop](R304B/chapters/11.5_TB_Closed_Loop.md)<br>[11.6 Service Instrument Air](R304B/chapters/11.6_Service_Instrument_Air.md)<br>[11.7 Fuel Pool Cooling](R304B/chapters/11.7_Fuel_Pool_Cooling.md) | [13.0 Inst Air](R304P/chapters/13.0_Inst_Air.md)<br>[14.5 CCW](R304P/chapters/14.5_CCW.md)<br>[14.6 Service Water](R304P/chapters/14.6_Service_Water.md)<br>[14.7 CW and TBCW](R304P/chapters/14.7_CW_and_TBCW.md) | [9.2 WATER SYSTEMS](CGS_FSAR/chapters/9.2_WATER_SYSTEMS.md)<br>[9.4 HEATING, VENTILATING, AND AIR CONDITIONING SYSTEMS](CGS_FSAR/chapters/9.4_HEATING_VENTILATING_AND_AIR_CONDITIONING_SYSTEMS.md)<br>[9.5 OTHER AUXILIARY SYSTEMS](CGS_FSAR/chapters/9.5_OTHER_AUXILIARY_SYSTEMS.md) | — |
| **Electrical power** | [9.1 Normal AC Power](R304B/chapters/09.1_Normal_AC_Power.md)<br>[9.2 Emergency AC Power](R304B/chapters/09.2_Emergency_AC_Power.md)<br>[9.3 120VAC Power](R304B/chapters/09.3_120VAC_Power.md)<br>[9.4 DC Power](R304B/chapters/09.4_DC_Power.md) | [06.0 Elect dist](R304P/chapters/06.0_Elect_dist.md) | [8.2 OFFSITE POWER SYSTEM](CGS_FSAR/chapters/8.2_OFFSITE_POWER_SYSTEM.md)<br>[8.3 ONSITE POWER SYSTEMS](CGS_FSAR/chapters/8.3_ONSITE_POWER_SYSTEMS.md) | — |
| **Radioactive waste & radiation protection** | [8.1 Offgas](R304B/chapters/08.1_Offgas.md)<br>[8.2 Liquid Radwaste](R304B/chapters/08.2_Liquid_Radwaste.md)<br>[8.3 Solid Radwaste](R304B/chapters/08.3_Solid_Radwaste.md) | [16.0 Rad Monitoring](R304P/chapters/16.0_Rad_Monitoring.md) | [11.2 Liquid Waste Management System](CGS_FSAR/chapters/11.2_Liquid_Waste_Management_System.md)<br>[11.3 Gaseous Waste Management Systems](CGS_FSAR/chapters/11.3_Gaseous_Waste_Management_Systems.md)<br>[12.2 RADIATION SOURCES](CGS_FSAR/chapters/12.2_RADIATION_SOURCES.md) | — |
| **Fuel handling & spent fuel storage** | [11.7 Fuel Pool Cooling](R304B/chapters/11.7_Fuel_Pool_Cooling.md) | [17.1 Fuel Handling](R304P/chapters/17.1_Fuel_Handling.md)<br>[17.2 Spent Fuel Storage](R304P/chapters/17.2_Spent_Fuel_Storage.md) | [9.1 FUEL STORAGE AND HANDLING](CGS_FSAR/chapters/9.1_FUEL_STORAGE_AND_HANDLING.md) | — |
| **Accident analysis & design-basis events** | — | — | [15.0 GENERAL](CGS_FSAR/chapters/15.0_GENERAL.md)<br>[15.1 DECREASE IN REACTOR COOLANT TEMPERATURE](CGS_FSAR/chapters/15.1_DECREASE_IN_REACTOR_COOLANT_TEMPERATURE.md)<br>[15.3 DECREASE IN REACTOR COOLANT SYSTEM FLOW RATE](CGS_FSAR/chapters/15.3_DECREASE_IN_REACTOR_COOLANT_SYSTEM_FLOW_RATE.md)<br>[15.6 DECREASE IN REACTOR COOLANT INVENTORY](CGS_FSAR/chapters/15.6_DECREASE_IN_REACTOR_COOLANT_INVENTORY.md) | [3. THE ACCIDENT](INSAG-7/chapters/3_THE_ACCIDENT.md)<br>[4. MORE RECENT ANALYSES OF THE FAULT SCENARIO](INSAG-7/chapters/4_MORE_RECENT_ANALYSES_OF_THE_FAULT_SCENARIO.md) |
| **Chernobyl sequence, causes & lessons** | — | — | — | [1. INTRODUCTION](INSAG-7/chapters/1_INTRODUCTION.md)<br>[3. THE ACCIDENT](INSAG-7/chapters/3_THE_ACCIDENT.md)<br>[4. MORE RECENT ANALYSES OF THE FAULT SCENARIO](INSAG-7/chapters/4_MORE_RECENT_ANALYSES_OF_THE_FAULT_SCENARIO.md)<br>[5. VIEWS OF INSAG](INSAG-7/chapters/5_VIEWS_OF_INSAG.md)<br>[6. CONCLUSIONS ON FACTORS CONTRIBUTORY TO THE ACCIDENT](INSAG-7/chapters/6_CONCLUSIONS_ON_FACTORS_CONTRIBUTORY_TO_THE_ACCIDENT.md) |
| **Safety culture & regulatory failure** | — | — | [13.2 TRAINING](CGS_FSAR/chapters/13.2_TRAINING.md)<br>[13.5 PLANT PROCEDURES](CGS_FSAR/chapters/13.5_PLANT_PROCEDURES.md) | [5. VIEWS OF INSAG](INSAG-7/chapters/5_VIEWS_OF_INSAG.md) |

---

## 5. How to use the corpus

### Reading a system end to end

1. Open the generic manual chapter (R304B or R304P) for purpose/components/operation.
2. Open the matching FSAR section in CGS for the plant-specific design and numbers.
3. Use the figure right after the text that introduces it — figures are inlined where the caption was.

### Search recipes

```bash
# everything containing a term, with file names
grep -rniE "setpoint|set point" Nuclear_Docs/CGS_FSAR/chapters | less

# a specific chapter only
grep -ni "ADS" Nuclear_Docs/R304B/chapters/10.2_ADS.md

# find which figure shows something
grep -i "recirculation" Nuclear_Docs/R304B/FIGURE_INDEX.md

# page-anchored lookup: find the PDF page marker before a hit
grep -n "positive scram" Nuclear_Docs/INSAG-7/chapters/*.md
```

### Citation format

`R304B/chapters/10.3_Core_Spray.md` (PDF p. 7) — the `<!-- p.7 -->` marker above the quoted text gives the page in the original PDF.

---

## 6. Conventions, provenance and caveats

- **Page anchors:** `<!-- p.N -->` marks the start of original PDF page *N* in that chapter's source PDF, not the printed page number of the document.
- **Figures:** rendered at 200 dpi. Every figure is a PNG; where the source page is true vector art the same figure is also written as a lossless **SVG** (`fig_2.4-1.svg`, same stem) that stays sharp at any zoom — use it for schematics, one-line diagrams, and plots. Scanned plates are PNG only. Figures are named after their figure number where the document gives one (`fig_2.4-1.png`), otherwise `fig_page-N.png` (CGS drawing plates, which have no machine-readable caption).
- **Figure pages keep their text:** for image-rendered pages the page's own text (drawing labels, title block) is included underneath the image so the labels stay searchable.
- **Scanned OCR:** INSAG-7 is an OCR'd 1992 scan; expect occasional character substitutions (e.g. “dear” for “clear”, mangled Greek symbols in equations). CGS FSAR drawing plates are partly scanned and their labels can be garbled — trust the drawing, not the OCR of the drawing.
- **CGS FSAR** is an Amendment 67 compilation assembled from pages of different vintages; the per-page header (Amendment NN, date) tells you which amendment that page came from.
- **R304B** is missing GE sections 1.1–1.6 and 6.x (not in the source set). R304P contains two copies of section 2.1 (base and revised) as supplied.
- **Not legal advice / not current licensing basis:** CGS FSAR Amendment 67 is a snapshot. Operating plants amend their FSARs; confirm against the current docket before relying on a number.

---

## 7. Gaps and suggested additions

The corpus covers BWR/3, BWR/5, a Westinghouse PWR and Chernobyl in depth, but several areas that come up in real nuclear work are thin or absent. Suggested additions, in priority order:

| Priority | Document | Why it fills a real gap |
|---|---|---|
| 1 | **NUREG-0800, Standard Review Plan** (all chapters) | The review criteria behind every FSAR section; turns “FSAR says X” into “X is acceptable because SRP §Y says Z”. |
| 2 | **Regulatory Guide 1.82 / NUREG-0800 §6.3 + NUREG-0800 §15** or **NUREG-0800 §6.3** | ECCS evaluation model acceptance criteria (10 CFR 50.46) — referenced constantly by Ch 6/15. |
| 3 | **NUREG-1150** (Severe Accident Risks) or **NUREG-1465** (Source Term) | Beyond design basis: core damage, containment failure modes, source terms. CGS Ch 15 stops at design basis. |
| 4 | **NUREG/CR-XXXX BWR/5 and PWR transient benchmarks**, or **TRACE/RELAP5 theory manuals** | How the Ch 15 numbers are actually produced; the FSAR only states results. |
| 5 | **10 CFR 50 / 10 CFR 50 Appendix A & B** | The regulation itself, so FSAR conformance claims can be checked. |
| 6 | **NUREG-1738 or SECY-93-087** (Mark I/II containment performance) | The BWR containment vulnerability debate that shaped modern BWR regulation. |
| 7 | **INSAG-1 (75-INSAG-1)** | To read INSAG-7 as the revision it is; INSAG-7 quotes it throughout. |
| 8 | **IAEA INSAG-3 / SF-1 Fundamental Safety Principles**, **GSR Part 4** | The safety-case and defence-in-depth frameworks used in the Chernobyl analysis, in their current form. |
| 9 | **Chernobyl: “The Accident and its Consequences” (IAEA 1996) or OECD/NEA “Chernobyl Ten Years On”** | Consequences, doses, sarcophagus, and the post-accident regulatory response. INSAG-7 deliberately stops at causes. |
| 10 | **A GE BWR/6 or ABWR design control document (ESBWR/ABWR DCD)** | Extends BWR coverage forward from BWR/5; shows what changed after the 1980s (passive safety, digital I&C). |
| 11 | **[Vogtle Units 1 & 2 UFSAR, Rev 20](SOURCES/Vogtle_UFSAR/README.md)** — *already in this repo* | R304P is generic; this is the plant-specific counterpart CGS provides for BWR — a 4-loop Westinghouse PWR (Model D, 3,411 MWt) with real design bases, setpoints and accident analyses. Source-only: not yet split into Markdown chapters. |
| 12 | **NUREG-0654 / FEMA REP-1 (emergency planning)** and **EPRI SAMG guidance** | Emergency preparedness and severe accident management, absent from all four documents. |
| 13 | **TMI-2 (NUREG-0600 / “TMI-2 Accident”)** | The other canonical accident; pairs with Chernobyl and explains many PWR design changes present in R304P. |
| 14 | **NRC inspection reports / ADAMS documents for Columbia** | Ground truth on plant changes since Amendment 67. |

