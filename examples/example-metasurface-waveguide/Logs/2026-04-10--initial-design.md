# 2026-04-10: Initial RCWA period sweep

## Why
Find optimal grating period for TiO₂ metasurface coupler at 633 nm TE.

## Setup
- Method: RCWA (S4), 301 Fourier orders, TE polarization
- Period sweep: 300–500 nm, step 2 nm
- FF: 0.5 fixed, height: 150 nm fixed

## Results
Peak efficiency: 74.3% at period = 418 nm.
See Logs/figs/period-sweep-20260410.png

## Interpretation
Optimum matches Bragg condition (~415 nm). Asymmetric tolerance.

## Next
- [ ] Sweep fill factor at period = 418 nm
