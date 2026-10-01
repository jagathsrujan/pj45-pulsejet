# PJ-4.5 Pulse Jet — CAD Package Notes

**Model:** `PJ-4.5.FCStd` (FreeCAD) · `PJ-4.5.step` (AP214 solids) · `PJ-4.5.stl` (mesh)
**Basis:** ThermalPulse 12 "Giant Chinese Valveless" (© 2005 Eric Beck) scaled by **k = 0.61**, per `research/chinese-type/design-notes/04-PJ-4.5-DESIGN-PROPOSAL.md`
**Scale used:** 1 in = 15.5 mm · all model units mm · engine axis = Z, chamber head plane at z = 0, exhaust exit at z = 821.5 (833 mm overall incl. cap)

---

## 1. Dimension table (as modelled)

| # | Part | Drawing dim | Model (mm) | Object name in FCStd |
|---|---|---|---|---|
| 1 | Combustion chamber tube | Ø3.5 × 7.00 in | OD 54.25 / ID 50.25 × L 108.5 | `_01_ChamberTube_57x2` |
| 2 | Chamber→pipe nozzle cone | Ø3.5→Ø1.88, 4.00 in | OD 54.25→29.14 / ID 50.25→25.14 × L 62 | `_02_NozzleCone` |
| 3 | Center pipe | Ø1.88 × 15.25 in | OD 29.14 / ID 25.14 × L 236.4 | `_03_CenterPipe_29x2` |
| 4 | Exhaust cone (expanding) | Ø1.88→Ø3.5, 12.75 in | OD 29.14→54.25 / ID 25.14→50.25 × L 197.6 | `_04_ExhaustCone` |
| 5 | Exhaust pipe | Ø3.5 × 14.00 in | OD 54.25 / ID 50.25 × L 217 | `_05_ExhaustPipe_57x2` |
| 6 | Dished end cap + boss | dish 0.50 / stub 0.25 in | dome 6.5 deep, 2 mm wall, Ø12.7 boss, Ø9 (M10×1) tap | `_06_EndCap_Dished` |
| 7 | Intake (bent, flared) | Ø1.88, L 5.60 in, 68° root | OD 29.14 / ID 25.14, developed L 86.8, root 68° → mouth 45°, +2 mm lip flare | `_07_IntakeTube_Bent` |
| 8 | Propane injector | 1/8" tube, tip 2–4" in | Ø3.2 tube, tip 40 mm inside intake mouth, tapered tip | `_08_PropaneInjector_3x2` |
| 9 | Spark plug | NGK CM-6 | M10×1 Ø9.8 × 9.5, hex Ø16, insulator, terminal | `_09_SparkPlug_NGK_CM6` |
| | **Overall** | **53.75 in** | **833.0** (cap face z = −11.5 → exit z = 821.5) | |

Derived check: 7.00 + 4.00 + 15.25 + 12.75 + 14.00 = 53.00 in + 0.75 in cap = 53.75 in ✔

Aggregate objects: `PJ45_Shell_Assembly` (5 shell parts fused, 1 solid), `PJ45_Body_Welded` (shell + cap + intake, 1 solid), `PJ45_Section_YZ` / `PJ45_Section_Head` (half-sections for inspection).

## 2. Important: corrected reading of the source drawing

While modelling, the dims on `plan-page-1.jpg` were re-verified pixel-by-pixel against the drawing's own dimension text. Three dims the design notes had left "uncertain" resolve as follows (all at the drawing's internal 16.6 px/in scale, joint lines consistent to ±1 px):

- **"3.5" sits inside the 7.00 segment** → the combustion chamber is **Ø3.5 in**, not Ø5.625.
- **"1.88" sits inside the 15.25 segment** → the long center pipe is **Ø1.88 in**.
- **"5.625" (front view) spans from the intake circle to the chamber circle** (both edges dimensioned) → it is the *envelope across chamber + intake*, not a chamber diameter.
- Therefore the segment stack is: chamber Ø3.5 → contraction 3.5→1.88 (4.00) → center pipe Ø1.88 (15.25) → *expansion* 1.88→3.5 (12.75) → exhaust pipe Ø3.5 (14.00) → exit. The "Exhaust Pipe" label points at the straight top segment ✔. Cross-checks that support this: all five segment length dims land on their joint lines at a constant 16.6 px/in; the exhaust:chamber and chamber:intake volume ratios then match the classic rules of thumb (~5× and ~4×) that the drawing *failed* under the old reading.
- Consequence vs `04-PJ-4.5-DESIGN-PROPOSAL.md` §2: the proposal's chamber Ø87 / tailpipe Ø54 rows describe the **uncorrected** reading. The CAD and exports use the corrected values above (chamber Ø54.25, center pipe Ø29.14). Lengths (833 mm, 108.5 / 62 / 236.4 / 197.6 / 217) are unchanged.
- The "45°" callout belongs to the intake mouth/flare geometry (68° = root separation).

## 3. Assumptions (tuning points, not yet validated)

1. **Intake bend:** root at 68° from the axis, bending to 45° at the mouth, developed length 5.60 in (86.8 mm) — per the 68°/45° callouts + 5.60 dim + rules of thumb. Intake length and flare are the documented tuning knobs if the engine is reluctant to run.
2. Intake root centerline at **z = 40 mm** on the chamber wall (front of chamber, ≈1.25–2 in standoff per table/proposal).
3. Wall thicknesses: tubes 2 mm, cones 2 mm, cap 2 mm — not dimensioned on the drawing; adjust to stock.
4. Injector tip 40 mm into the bore (2–4 in scaled); injector is 1/8" hardware, un-scaled.
5. Spark plug modelled as a simplified NGK CM-6 envelope; boss tapped M10×1 (Ø9 model hole).
6. Procurement note: Ø54.25 / Ø29.14 are scaled-nominal; nearest stock is 57×2 mm tube (ID 53) and 33.4×2 or 30×1.5 for the pipe — lengths stay as modelled.

## 4. Files

| File | Contents |
|---|---|
| `PJ-4.5.FCStd` | full FreeCAD model — parts tree + fused assemblies + sections |
| `PJ-4.5.step` | STEP AP214: welded body + injector + plug |
| `PJ-4.5.stl` | combined mesh (0.3 mm deflection) for viewing/simulation |
| `PJ-4.5_iso.png` | isometric hero view |
| `PJ-4.5_side.png` | side elevation (matches drawing orientation) |
| `PJ-4.5_head-detail.png` | chamber / intake / cap / injector / plug detail |
| `PJ-4.5_section-head.png` | half-section of head — bore, intake channel, plug boss |
| `PJ-4.5_section-iso.png` | half-section, full engine |
| `PJ-4.5_section-rear.png` | half-section, rear elevation |

## 5. Remaining open items before cutting metal

- Confirm intake bend/standoff preference on a cardboard mock-up (cheap, per design notes).
- Confirm local tube stock against the two scaled nominal diameters above.
- Weld list unchanged from proposal §5 (cap→chamber, chamber→nozzle, nozzle→pipe, pipe→cone, cone→exhaust, intake saddle ×1–2).
