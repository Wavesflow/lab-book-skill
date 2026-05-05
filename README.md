# Lab Book Skill

An [OpenCode](https://opencode.ai) skill for maintaining structured lab notebooks in photonics/computational optics research projects.

## What it does

When loaded, this skill helps AI agents maintain a per-project lab book consisting of:

- **`Logs/`** — date-stamped experiment/simulation records
- **`bugs.md`** — bug and mistake tracking
- **`AGENTS.md`** — project context for future AI agents
- **`README.md`** — project overview for human readers

## Usage

This skill is automatically loaded by OpenCode when detecting research-workflow-related phrases. See [SKILL.md](SKILL.md) for the full workflow definition.

## Files

| Path | Description |
|------|-------------|
| `SKILL.md` | Skill definition and agent workflow instructions |
| `templates/` | Boilerplate templates for new lab book files |
| `references/` | Decision tree and worked examples |
| `examples/` | Complete example lab book for a metasurface project |

## License

MIT
