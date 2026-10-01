# PJ-4.5 — Valveless Pulse Jet (Chinese-type)

A ~4.5 lbf (≈20 N) valveless "Chinese-type" pulse jet for a college static-thrust demo — delivered as a **hybrid build: reusable metal hot sections + 3D-printed cones/intake, assembled with zero welding**, so the design can be tested and iterated before committing to a full metal engine.

**Build path:** `build/BOM-INDIA.md` (shopping list) → print `printed-test/HJ_*.stl` → assemble per `printed-test/HYBRID-TEST-GUIDE.md` → test.

## Repo map

| Path | Contents |
|---|---|
| `cad/` | Metal-design CAD master — `PJ-4.5.FCStd` / `.step` / `.stl`, section renders, `CAD-NOTES.md` (dimension table, assumptions, drawing analysis) |
| `printed-test/` | Hybrid rig — printable STLs (`HJ_01…HJ_05`), assembly + test guide, renders, `PJ-4.5-HYBRID.FCStd` |
| `build/` | `BOM-INDIA.md` — itemized bill of materials with Indian-market prices and sourcing |

## Design at a glance

| | |
|---|---|
| Type | Valveless "Chinese-type" pulse jet, propane fuel |
| Overall length | 833 mm (≈53.75 in) |
| Bores (design) | Chamber Ø54 · centre pipe Ø29 · exhaust Ø54 |
| Target thrust | 4.3–4.8 lbf (19–21 N) static |
| Pulse frequency | ~70–100 Hz (cold quarter-wave ≈ 103 Hz) |
| Mass | ~2.4–2.5 kg |
| Noise | 120–140 dB near-field — double hearing protection mandatory |
| Hybrid rig | metal chamber/head/centre & exhaust pipe + printed nozzle/exhaust cones, intake, couplers |

## Provenance & what this repo is

The internal geometry is a ×0.61 scale of the **ThermalPulse 12 "Giant Chinese Valveless"** (© 2005 Eric Beck / Beck-Technologies), which is shared for hobby use only ("not for commercial use"). This repository contains only original work — the CAD redraw/scale, printed-part design, BOM and test documentation. The source research archive (third-party plans, papers, forum captures) is **not** redistributed here.

## Safety

This is a real jet engine: LPG fuel, 120–140 dB noise, glowing-hot metal, burning-plastic risk in the printed version. Test outdoors, upwind, extinguisher staged, ball-valve kill on the fuel line, double hearing protection, nobody within 5–10 m. Educational/hobby project — build and operate entirely at your own risk.

## License

**CC BY-NC-SA 4.0** — share and adapt freely with attribution, **non-commercial**, share-alike. (Non-commercial because the design derives from the non-commercially licensed ThermalPulse 12 plans.) See [LICENSE](LICENSE).
