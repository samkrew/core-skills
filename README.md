# core-skills

Opinionated skills for Claude Code (and compatible agents) covering strategic auditing, cognitive reflection, technical review, and four operating modes (Plan, Implement, Explain, Audit).

## Install

Install all skills for your agent:

```bash
npx skills add samkrew/core-skills
```

Install selected skills only:

```bash
npx skills add samkrew/core-skills --skill lens-technical --skill mode-plan
```

Install into the current project (`.claude/skills/`) instead of user scope:

```bash
npx skills add samkrew/core-skills -p
```

Non-interactive (CI):

```bash
npx skills add samkrew/core-skills -a claude-code -g -y
```

See the [`skills` CLI reference](https://github.com/vercel-labs/skills) for the full flag set. The CLI supports Claude Code, Cursor, OpenCode, Codex, Gemini CLI, and several other agents.

## Catalog

| Skill | Description |
|---|---|
| `core-skills` | Universal ontological doctrine: Identity, Perception, and Epistemic Protocol. |
| `lens-activity` | Executive signal-to-noise audit for Slack, Telegram, and Jira. |
| `lens-cognitive` | Cognitive navigator: Jung-Cross, Quantum, Transition, and Immunity. |
| `lens-strategic` | High-integrity executive auditing: SNO Matrix, Watermelon detection, Strategic Foresight. |
| `lens-technical` | Technical code review: Bugs, Security, Performance, and Design. |
| `mode-audit` | Evaluation mode for strategic, technical, or cognitive audits. |
| `mode-explain` | Surgical discovery and knowledge-transfer mode. |
| `mode-implement` | High-precision implementation and verification mode. |
| `mode-plan` | Strategy and architectural planning mode. |

## Usage

After install, the skills appear in your agent's catalog. In Claude Code, run `/skills` to list them, or invoke a mode directly via `/mode-plan`, `/mode-implement`, `/mode-audit`, `/mode-explain`. The `lens-*` skills auto-trigger when the user asks for an audit, code review, pulse check, or reflection.

## Notes

- `lens-activity` writes reports as plain Markdown by default (`./reports/Activity-{Source}-{YYYY-MM-DD}.md`). Obsidian-specific conventions (wikilinks, callouts, block IDs, Dataview, Tasks plugin) are applied only when the user explicitly asks for Obsidian integration.
- `mode-audit` references the four lenses in this repo. If additional MCP servers (Slack, Jira, Confluence, Telegram) are connected, it will pull context from whichever are available and skip the rest.
- These skills are opinionated. Fork and adapt the `description:` frontmatter and output conventions to fit your workflow.

## License

[Unlicense](./LICENSE) — public domain dedication.
