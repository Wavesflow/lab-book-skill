# Metasurface Waveguide Coupler — Agent Guide

## Project Overview
Design a TiO₂ metasurface on SiO₂ waveguide that couples free-space 633 nm light into the TE₀₀ waveguide mode with >70% efficiency.

## Key Files
- `AGENTS.md` — this file
- `bugs.md` — bug/mistake log
- `README.md` — project overview
- `Logs/` — experiment records

## Current Status
Active — parameter sweep phase. Peak efficiency so far: 74.3% at period=418nm.

## Important Decisions
- 2026-04-10: Chose TiO₂ over SiN for higher index contrast → better coupling efficiency, but more fabrication challenge
- 2026-04-12: SBH (Spatial BEER expansion) decided to use TE polarization only (TM gave <30% efficiency)

## Known Issues / Gotchas
- RCWA convergence requires >201 Fourier orders at high index contrast
- Mesh refinement beyond 5 nm doesn't change results but multiplies runtime ×3

## Environment
- RCWA: S4 (Stanford Stratified Structure Solver)
- Python 3.10, numpy, scipy, matplotlib
