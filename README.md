# Lab Book Skill

An [OpenCode](https://opencode.ai) skill for maintaining structured lab notebooks in photonics/computational optics research projects.

## Installation

```bash
git clone https://github.com/Wavesflow/lab-book-skill.git \
  C:\Users\Administrator\.config\opencode\skills\lab-book-skill
```

## Usage

Loaded **on demand** — say "加载 lab book" / "load lab book" when you want to use it.

> Unlike most skills that auto-trigger, lab-book-skill only activates when you explicitly ask.

## Structure

```
lab-book-skill/
├── SKILL.md                 ← Skill 定义 + 工作流（系统入口）
├── README.md                ← 本文件
├── templates/               ← 新项目 lab book 初始化模板
│   ├── AGENTS.md.tpl
│   ├── bugs.md.tpl
│   ├── README.md.tpl
│   └── Logs/YYYY-MM-DD--template.md
├── references/              ← 给 agent 的参考材料
│   ├── what-to-log.md
│   └── log-examples.md
└── examples/                ← 完整示例项目
    └── example-metasurface-waveguide/
```

## File Index

| File | Purpose |
|------|---------|
| `SKILL.md` | Skill 定义 + agent 工作流指令 |
| `templates/AGENTS.md.tpl` | Agent 项目上下文模板 |
| `templates/bugs.md.tpl` | Bug 追踪模板（含示例条目） |
| `templates/README.md.tpl` | 项目 README 模板（含文件索引） |
| `templates/Logs/YYYY-MM-DD--template.md` | 日志条目模板（含 YAML frontmatter） |
| `references/what-to-log.md` | 事件→文件决策树 |
| `references/log-examples.md` | 4 个领域示例（RCWA/COMSOL/PSO/结构色） |
| `examples/example-metasurface-waveguide/` | 完整 lab book 示例 |

## Conventions

Applies to all lab book files created by this skill:

| Rule | Standard |
|------|----------|
| Log filenames | `YYYY-MM-DD--kebab-description.md` |
| Dates | Always `YYYY-MM-DD`, no relative dates |
| Log structure | Why → Setup → Results → Interpretation → Next |
| Bug structure | Symptom → Root cause → Fix → Prevention |
| Log YAML frontmatter | `date`, `type`, `tags` (Obsidian-compatible) |

## License

MIT
