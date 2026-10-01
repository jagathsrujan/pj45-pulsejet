# PJ-4.5 — Hybrid Test Unit Guide (printed + metal, **zero welding**)

**Concept:** metal where it's hot and reusable forever · printed where the geometry is critical and reprints are cheap · **no welds anywhere** — the chamber head is a standard threaded pipe stack.

**Files:** `PJ-4.5-HYBRID.FCStd`, 5 STLs (this folder), `HJ_assembly-iso.png`, `HJ_section.png`. Printed parts are **pre-oriented** for the H2D.

## 1. What is metal vs printed

| Section | Material | Why | Reusability |
|---|---|---|---|
| Chamber tube | **Metal** — 2″ threaded nipple | hottest zone | forever |
| Chamber head + plug boss | **Metal** — threaded coupling + bushing + hex plug | no weld, serviceable | forever |
| Centre pipe | **Metal** — Ø30×1.5 tube | long hot run | forever |
| Exhaust pipe | **Metal** — 2″ pipe offcut | straight tube, cheap | forever |
| Nozzle cone | **Printed** (HJ_01) | exact design cone geometry, tuneable by reprint | consumable ~₹40–120 |
| Exhaust cone | **Printed** (HJ_02) | exact 197.6 mm / 11° cone | consumable |
| Intake | **Printed** (HJ_03) | geometry + injector holder, coolest zone | long life |
| Couplers ×4 | **Printed** (HJ_04 ×2, HJ_05 ×2) | joints + seals | long life |

Full printed set = **200 cm³ ≈ 220 g ≈ ₹160 (ABS) / ₹430 (ASA)** — that's your per-session worst-case consumable cost. Normally ₹0.

## 2. Metal shopping list (no weld — all standard fittings)

| Item | Spec | Qty | Est. ₹ | Where |
|---|---|---|---|---|
| Chamber nipple | 2″ BSP SS304 threaded pipe nipple, 150 mm (2″×6″) | 1 | 300–500 | local pipe/plumbing market |
| Chamber coupling | 2″ BSP SS304 coupling (socket) | 1 | 200–300 | same |
| Head bushing | 2″×½″ BSP SS304 hex reducing bushing | 1 | 120–200 | same |
| **Plug boss** | ½″ BSP SS304 hex plug — **drill Ø9 + tap M10×1** | 1 | 80–150 | same (tap is BOM item H3) |
| Centre pipe | Ø30×1.5 mm SS304 tube, ~245 mm (BOM A2′) | 1 | 150–250 | steel market |
| Exhaust pipe | 2″ NB SS304 pipe Sch-10S, ~220 mm (BOM A1 offcut) | 1 | 250–400 | steel market |
| Copper washers | ½″ + M10 | 4 | ~30 | hardware |
| | | | **~₹1,150–1,850** | **all reusable forever** |

Alternative head (if the bushing is hard to find): 2″ SS cap, drill centre Ø9.5, tap M10×1, back it with a **thin M10×1 jam nut** inside + copper washer outside.

**Joint architecture:** every metal↔metal and metal↔printed joint is a butt joint bridged by a printed coupler (ID 60.55 or 30.8) + ceramic cement + 2–3 M3 self-tapping screws through the printed pilot holes. The intake is **not** pressure-bearing — it beds onto the chamber with furnace cement + 2 turns of fiberglass tape (serviceable: chip off, reposition, redo).

**Assembly order:**
1. **Head stack:** plug boss (drilled/tapped) → bushing + ½″ copper washer + PTFE → coupling; screw the nipple into the coupling to set the **chamber run to ~108 mm** — it's tunable ±10 mm here; log the setting.
2. Slide printed **nozzle cone** onto the nipple; **C1 coupler** over the butt, screws + cement.
3. **Centre pipe** into the nozzle's small end; **C2 coupler** + screws + cement.
4. **Exhaust cone**, second **C2**; **exhaust pipe**, second **C1**.
5. **Intake:** bed at ≈75 mm up from the nozzle-cone joint, cement + fiberglass tape wrap (hose clamp optional).
6. **Injector** 40 mm into the mouth, PTFE, small clamp.
7. Check the plug tip doesn't touch anything inside; spark gap in the chamber.

**Known (documented) bore steps** vs the all-metal design — acceptable for a test rig, note them in the report: chamber ID 54.8 (design 50.25) · centre ID 27 (25.14) · exhaust ID 54.8 (50.25). The printed cones keep the design cone lengths/angles exactly.

## 3. Filament & print settings (H2D)

Same as before: **ABS (₹710–900/kg, e.g. Numakers) or ASA (₹1,950/kg)** — this rig is metal where it matters, so the cheap filament is genuinely fine for the printed cones/couplers. 0.6 mm hardened nozzle, 5 perimeters, 0.24–0.28 layers, 0 % infill, brim on, elephant-foot compensation ON, supports only under the intake (it prints pre-rotated mouth-down). Never PVC. Burning ABS/ASA fumes — outdoors, upwind.

**Thermal protection for the printed cones (now the only weak links):** sodium silicate or zirconia kiln-wash inside the nozzle + exhaust cone bores, and a kaowool wrap over the nozzle cone. Cheap, and it decides how long between reprints.

## 4. Expected performance (hybrid)

| Parameter | Expected | Notes |
|---|---|---|
| Static thrust | **3.5–4.5 lbf (16–20 N) sustained** | metal gas-path; measure properly now — the numbers are real |
| Pulse frequency | 70–100 Hz design; **expect ~3–7 % lower** | the 2″/Ø30 pipe bores are ~7–9 % larger than the all-metal design — log the measured value |
| Run length | **minutes, recharged indefinitely** | metal sections unlimited; only printed cones age |
| Duty cycle | start 15–30 s runs, 60–120 s cools | inspect the printed nozzle cone between runs; extend as confidence grows |
| Reusable | chamber, head, centre pipe, exhaust | forever |
| Consumables | printed cones/intake/couplers | ~₹160 (ABS) per reprint as needed |
| Mass | ~2.4–2.5 kg | metal dominates |

**Bonus tuning feature:** chamber length is adjustable ±10 mm by how deep the nipple screws into the coupling — A/B that in one session and you'll have real data for the metal build.

## 5. Test protocol

**Stage 0 — PLA mockup** of the 5 printed parts (draft settings) → fit against the metal parts, especially the coupler slip fits and the intake saddle on the 2″ nipple.
**Stage 1 — cold acoustic test** (no fuel): assembled rig + speaker sweep (40–300 Hz) at the exhaust / rubber-mallet impulse; record at 0.5 m; FFT (phyphox/Spectroid). Expect the quarter-wave peak near ~100 Hz; compare with your measured hot frequency later.
**Stage 2 — systems check:** soap-test LPG joints; spark test on the plug; blower flow at the intake.
**Stage 3 — progressive fire tests (outdoors only):** 5 s → inspect → 10 s → 15–30 s as confidence grows. Standard start recipe (injector 40 mm in → spark → needle ¼ → ball valve → blower). Ball valve always in hand; sand/steel tray; ABC extinguisher; double hearing protection; ≥ 5–10 m clearance; film everything (240 fps for pulse counting).
**Stage 4 — data:** thrust curve vs time (load cell), frequency FFT, best injector position, chamber-length setting, valve position. Only the printed nozzle/exhaust cone wear — reprint, swap, keep testing.

## 6. Safety

120–140 dB when running · hot metal glows, plastic cones can sag/char · toxic smoke if a printed part burns · LPG fire/explosion risk. Outdoors, upwind, extinguisher staged, fuel valve never unattended, ears doubled. Never indoors.
