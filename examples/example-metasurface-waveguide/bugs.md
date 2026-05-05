# Bugs & Mistakes

## 2026-04-15: Grating offset caused 3 dB coupling loss

**Symptom:** Coupling efficiency peaked at 45% instead of expected >80%.
RCWA and FDTD agreed, so not a solver issue.

**Root cause:** Grating tooth position was offset by half a period relative to
the waveguide center. The design script used `x0 = period/2` but the reference
coordinate was at the waveguide edge, not center.

**Fix:** Changed offset to `x0 = period/2 + waveguide_width/2`. Efficiency
jumped to 83%, matching expectation.

**Prevention:** Document coordinate origin in script header. Add auto-plot
verification on first run.
