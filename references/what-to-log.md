# Decision Tree: What Goes Where

## Quick Map

| Event | Write to | Example |
|-------|----------|---------|
| Simulation run with numerical results | `Logs/YYYY-MM-DD--*.md` + raw data file | RCWA sweep, FDTD, COMSOL eigenmode |
| Bug / wrong parameter / incorrect assumption | `bugs.md` (+ cross-ref Logs) | Grating offset, wrong boundary condition |
| Design decision (why X over Y) | `AGENTS.md` (Decisions section) | "Chose TiO2 over SiN for low absorption at 450nm" |
| Milestone / phase complete | `README.md` (Results + Status) | "Parameter sweep done, best efficiency: 73% at period=420nm" |
| Environment change | `AGENTS.md` (Environment section) | "Updated to Python 3.12, broke legacy RCWA wrapper" |
| External discussion / meeting notes | `Logs/YYYY-MM-DD--*.md` | Paper review comments, conference talk feedback |
| Raw data dump (figure, CSV, .mph) | `Logs/<subdir>/` + reference from log entry | Copy to `Logs/figs/` or `Logs/data/` |

## Detailed Rules

### Simulation / Experiment Results → Logs/

Write a log entry whenever:
- A simulation finishes with meaningful numbers
- You change a key parameter and observe a different outcome
- An experiment (real or numerical) produces data worth revisiting

**What the entry must contain:**
- Enough parameter detail to reproduce without hunting through scripts
- Raw results (numbers) separated from interpretation
- File paths to any raw data, plots, or simulation files

### Bug → bugs.md

A "bug" includes:
- Coding error (wrong index, wrong axis, wrong sign)
- Physical modeling mistake (wrong BC, wrong material model, wrong approximation)
- Parameter entry error (typo in period, thickness, wavelength)
- Solver configuration mistake (mesh too coarse, tolerance too loose)

**What is NOT a bug:** a failed experiment that correctly tested a wrong hypothesis (that's just science).

### Design Decision → AGENTS.md

Record when:
- You choose between alternative approaches (material, geometry, algorithm)
- You set a convention (coordinate origin, phase sign, normalization)
- You rule out a promising approach (with reason — saves future you from retrying)

The goal: future agents should be able to read the Decisions section and understand *why* the project is where it is, not just *what* was done.

### Milestone → README.md

Update README when:
- A significant result is obtained
- The project direction changes
- The project is archived

The README is for humans who need the fastest possible understanding of what this project achieved and whether it's relevant to them.
