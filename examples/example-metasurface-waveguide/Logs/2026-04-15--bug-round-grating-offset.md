# 2026-04-15: Bug fix — grating coordinate offset

## What happened
Reran optimal design (period=418, FF=0.55) target to verify and got only 45% efficiency.
Spent 2 hours checking convergence, mesh, material properties — nothing wrong.

## Root cause
Found it: the coordinate origin convention in `design_grating.py` used waveguide
edge as x=0, but the period array assumed center-aligned coordinates. Half-period offset.

## Fix
`x0 = period/2 + waveguide_width/2` instead of `x0 = period/2`.
Post-fix: 76% (consistent with prior result).

## Log
See bugs.md for permanent record.
