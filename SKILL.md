---
name: lab-book-skill
description: >
  Maintain structured lab notebooks for research projects — log experiments,
  design decisions, bugs, simulation results, and raw data. Creates and manages
  AGENTS.md, bugs.md, README.md, and Logs/ in any project directory.
  Loaded on demand — only activates when user explicitly requests it.
  Especially useful for photonics/computational optics simulation workflows
  (COMSOL, Lumerical, Zemax, RCWA, FDTD).
metadata:
  author: "Wavesflow"
  version: "1.0"
  category: "research-workflow"
  audience: "photonics-computational-optics"
---

# Lab Book Skill

Maintain structured lab notebooks per research project — the kind you'd want your future self (or next agent) to pick up without asking "what was I doing?"

---

## When to Load

This skill is **loaded on demand** only. It does NOT activate automatically.

Say "加载 lab book" / "用 lab book" / "load lab book" when you want to use it.

Once loaded, it follows the workflows below to help you maintain the project's lab book.

---

## Lab Book Structure

Each research project maintains these files at its root:

| File | Audience | Purpose |
|------|----------|---------|
| `AGENTS.md` | AI agents (next session) | Project context, decisions, gotchas, env setup |
| `bugs.md` | Human + AI | Record of mistakes, bugs, and how they were fixed |
| `README.md` | Human (you) | The project's soul — one-paragraph, key results, how to run |
| `Logs/` | Human + AI | Date-stamped experiment records with raw data references |

Files are created on demand when the first relevant entry occurs. No empty files.

---

## Workflow

### Init — Bootstrap a lab book in a new project

Triggered when entering a project directory that lacks lab book files AND user signals intent to start.

1. Check for existing files — do NOT overwrite anything
2. For each missing file, create from template:
   - `README.md` — always create if missing (every project needs a soul)
   - `AGENTS.md` — create if the project involves code/simulations an agent will touch
   - `bugs.md` — create only when first bug is recorded
   - `Logs/` — create only when first log entry is written
3. Announced what was created and suggest user fill in the README intro

Never create lab book files in a directory without user consent.

### Log — Record experiment / simulation results

1. Ask the user what type of content they want to record:
   - **Simulation/experiment result** → create `Logs/YYYY-MM-DD--kebab-description.md`
   - **Design decision** → update `AGENTS.md` Decision section
   - **Bug discovered** → dispatch to Bug workflow
   - **Milestone** → dispatch to Milestone workflow
2. For a log entry:
   - Write structured markdown: **Why** → **Setup** → **Results** → **Interpretation** → **Next**
   - Reference raw data files with relative paths (figures, CSV, .mph, .fsp)
   - Keep interpretation separate from raw results — don't let narrative override data
   - Include YAML frontmatter: `date`, `type`, `tags` (Obsidian-compatible)
3. Append a one-line summary to `README.md` under "Recent Results" if active

### Bug — Record a mistake or fix

Triggered when user identifies a bug, wrong parameter, incorrect physical assumption, or any "that was dumb" moment.

1. Append to `bugs.md` with format:
   - **Date**, **Symptom** (what went wrong, what you observed), **Root cause**, **Fix/Workaround**, **Prevention**
2. Cross-reference any related Logs/ entry that produced the buggy result
3. If the bug invalidates prior log entries, add a note in those entries — do NOT delete or rewrite history

### Milestone — Update project state

Triggered when a phase finishes: parameter sweep done, paper draft complete, project archived.

1. Update `README.md`:
   - Key results section with concrete numbers
   - Status line (Active / Writing up / Archived)
   - If archived: add archive date and summary
2. Update `AGENTS.md`:
   - Current status
   - Important decisions section (what was decided, why, what was ruled out)
   - Any new gotchas or environment changes

### Sync — Periodic maintenance

Perform during idle time or when user says "整理一下 lab book".

1. Scan `Logs/` — any entry missing interpretation or next steps? Flag them.
2. Check `bugs.md` — any open bugs that can be closed?
3. Verify `AGENTS.md` decisions match current code/setup reality.
4. Prune no-longer-relevant temporary files referenced in logs (ask first).

---

## Decision Tree

```
Intent → Action
│
├─ Start a new project / first entry
│   → Init workflow
│
├─ Record a simulation or experiment result
│   → Log entry in Logs/YYYY-MM-DD--*.md
│   + optional: if result is significant → update README
│
├─ Record a bug / wrong parameter / wrong result
│   → append to bugs.md
│   + cross-ref affected Logs/ entries
│
├─ Record a design decision
│   → update AGENTS.md Decision section
│   (not README — README is for results, not decision history)
│
├─ Project milestone (done, submitted, archived)
│   → Milestone workflow: README (results) + AGENTS.md (status+decisions)
│
├─ Tidy up / sync
│   → Sync workflow
│
├─ Archive raw output files
│   → copy/symlink to Logs/ subdirectory, reference from log entry
```

---

## Red Lines

- **Never delete log entries** — mark as superseded/invalidated, never remove
- **Never overwrite raw data** — reference by path, don't duplicate
- **Dates are YYYY-MM-DD** — no relative dates ("today", "yesterday")
- **Log entries include YAML frontmatter** — `date`, `type`, `tags` for Obsidian Dataview compatibility
- **`README.md` ≠ `AGENTS.md`** — don't merge them; different audiences
- **No private keys, passwords, or access tokens** in any lab book file
- **Interpretation is not result** — keep the "what happened" separate from "what I think it means"
- If a bug invalidates previous results, annotate the old entry — don't silently correct it
