# Log Entry Examples

These are realistic examples from photonics/computational optics research. Adapt the format to your domain.

---

## Example 1: RCWA Parameter Sweep

```
# 2026-04-10: Period sweep for TiO2 grating coupler

## Why
Find the optimal grating period that maximizes -1st order diffraction
efficiency into waveguide mode at λ = 633 nm.

## Setup
- Method: RCWA (S4), 301 Fourier orders
- Polarization: TE (E // grating lines)
- Parameters swept:
  - Period: 300–500 nm, step 2 nm
  - Fill factor: 0.5 fixed
  - Grating height: 150 nm fixed
- Substrate: SiO2, n=1.46
- Grating: TiO2, n=2.40
- Incident angle: 10° (from substrate side)

## Results
Peak efficiency: 74.3% at period = 418 nm, fill factor 0.5.
FWHM: ~35 nm in period.

Plot: see Logs/figs/2026-04-10-period-sweep.png
Raw data: Logs/data/period_sweep_20260410.csv

## Interpretation
- The 418 nm optimum matches simple Bragg condition: λ / (n_eff - n_substrate sinθ)
  ≈ 633 / (1.8 - 1.46*sin10°) ≈ 415 nm — close, consistent with effective index ~1.8.
- Low-side ripple at period < 350 nm due to mode cutoff in waveguide.
- Efficiency drops faster on the high-period side → alignment tolerance is asymmetric.

## Next
- [ ] Sweep fill factor at period = 418 nm
- [ ] Check angular tolerance (±2° around 10°)
```

---

## Example 2: COMSOL Eigenmode Analysis

```
# 2026-04-12: Waveguide mode analysis for 450 nm edge-emitting grating

## Why
Confirm that the etched grating region supports only the fundamental TE mode
at λ = 450 nm. Higher-order modes would cause beam quality degradation.

## Setup
- Solver: COMSOL 6.2, RF Module, Eigenfrequency study
- Geometry: 2D cross-section, 5 µm waveguide width
- Mesh: max element size 30 nm in grating region, 80 nm elsewhere
- BCs: PML on top/bottom, periodic on sides
- Material: GaN (n=2.45), AlGaN cladding (n=2.38)

## Results
Found 3 confined modes:
1. TE00 — n_eff = 2.32, mode overlaps grating region well
2. TE01 — n_eff = 2.28, weak overlap with grating (10% of TE00 coupling)
3. TM00 — n_eff = 2.20, negligible grating overlap

Mode profiles: Logs/figs/2026-04-12-eigenmode-profiles.png
COMSOL file: Logs/data/waveguide_450nm.mph

## Interpretation
- TE00 is clearly the target mode. TE01 exists but won't couple efficiently.
- The n_eff contrast (2.32 vs 2.38 cladding) is sufficient for confinement
  but marginal — consider increasing etch depth to 80 nm.
- Mesh convergence check: halving mesh changed n_eff by < 0.001. OK.

## Next
- [ ] Increase etch depth to 80 nm, check n_eff change
- [ ] Run FDTD coupling simulation with TE00 input
```

---

## Example 3: Optimization Run (Particle Swarm)

```
# 2026-04-18: Inverse design — metagrating for 45° beam deflection

## Why
Design a 1D metagrating that deflects normally-incident TM light to 45°
at λ = 940 nm, with efficiency > 80%.

## Setup
- Method: PSO, 60 particles, 120 iterations
- Objective: maximize power in +1 order at 45°
- Design variables: 5 rectangular bars per period
  - width each: 60–240 nm
  - position each: 0–600 nm (within period)
  - height: fixed 300 nm
- Simulator: FDTD (Lumerical), 2D, mesh 5 nm
- Time: ~14 hours on 12-core workstation

## Results
Best efficiency: **83.7%** at iteration 94.
Convergence: flat after iteration 80 → could have stopped earlier.

Topology: see Logs/figs/2026-04-18-optimized-geometry.png
Evolution: Logs/data/pso_convergence_20260418.csv

## Interpretation
- Achieved target >80%. The optimized geometry resembles a detuned
  binary grating — not intuitive, but robust.
- Two distinct design families emerged in early iterations (cluster A and B).
  Both converged to similar efficiency (83% vs 81%), so the optimum is
  relatively flat.
- Next Q: is the design robust to ±10 nm fabrication error?

## Next
- [ ] Fabrication tolerance sweep (±10 nm on all critical dimensions)
- [ ] Angular sensitivity: test ±2° incident angle variation
```

---

## Example 4: Structural Color — Experimental Validation

```
# 2026-04-22: Fabricated sample characterization — Session 1

## Why
Measure the reflectance spectrum of the fabricated Si metasurface sample
and compare with FDTD design target (peak at 550 nm, FWHM < 50 nm).

## Setup
- Instrument: Custom micro-spectroscopy setup (10x objective, halogen source)
- Calibration: Reflectance normalized to Ag mirror standard
- Measurement: 450–750 nm, 1 nm step, 3 spots per sample
- Sample: 5 × 5 mm, 1 cm from center

## Results
- Peak reflectance: 78% at 548 nm
- FWHM: 47 nm (vs. 44 nm simulated) — excellent agreement
- Spot-to-spot variation: ±3 nm peak shift (within fabrication tolerance)

Spectra: Logs/figs/2026-04-22-measured-reflectance.png
Raw data: Logs/data/reflectance_20260422.csv

## Interpretation
- Design target validated. The 2 nm blue shift and 3 nm FWHM broadening
  are consistent with +5 nm sidewall angle from the etch process.
- Spot variation likely due to slight thickness non-uniformity across
  the sample — typical for 4" Si wafer processing.

## Next
- [ ] Angle-resolved measurement (±20°)
- [ ] SEM cross-section to confirm sidewall angle
- [ ] Check aging: re-measure in 1 week
```
