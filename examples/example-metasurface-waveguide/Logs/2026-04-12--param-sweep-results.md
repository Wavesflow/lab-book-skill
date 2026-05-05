# 2026-04-12: Fill factor & angular tolerance sweep

## Why
Fix period=418 nm, find optimal fill factor; check angular tolerance.

## Setup
- Period: 418 nm (fixed from 2026-04-10)
- FF sweep: 0.3–0.8, step 0.05
- Angle sweep: 0–20°, step 1°, at optimal FF

## Results
- Optimal FF: 0.55 → efficiency 76.1% (slight improvement over 74.3% at FF=0.5)
- Angular tolerance: ±2° for >60% efficiency

Raw data: Logs/data/ff-angle-sweep-20260412.csv

## Interpretation
FF optimum is broad (0.45–0.65 gives >70%), good for fabrication.
Angular tolerance is tight but acceptable for collimated illumination.

## Next
- [ ] Fabrication tolerance study (±10 nm on CD)
