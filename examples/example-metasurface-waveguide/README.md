# Metasurface Waveguide Coupler

> A TiO₂ metasurface on SiO₂ waveguide for efficient free-space to waveguide coupling at 633 nm.

## File Index

| File | Created | Purpose |
|------|---------|---------|
| `README.md` | 2026-04-10 | 项目概述（本文件） |
| `AGENTS.md` | 2026-04-10 | AI agent 上下文、设计决策记录 |
| `bugs.md` | 2026-04-15 | Bug 与错误记录 |
| `Logs/` | 2026-04-10 | 实验/仿真日志归档 |

## Key Results
- Best coupling efficiency: **74.3%** at period=418nm, FF=0.5 (2026-04-10)
- Angular tolerance: ±2° for >60% efficiency

## How to Reproduce
```bash
python run_sweep.py --period 300-500 --step 2 --ff 0.5
```

Requires S4 RCWA solver and Python 3.10+.

## Status
Active — optimizing fill factor and angular tolerance.
