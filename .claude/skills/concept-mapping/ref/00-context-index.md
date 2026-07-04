# Concept Index

This is the table of contents for the cross tool concept mapping knowledge base.
It lists every project level configuration concept that has been mapped across
Claude Code, Codex, and Antigravity, with a one line blurb, each tool's primary
file or location, and a link to the full detail file. Read a concept's blurb
here to find the right detail file, then open that file for the aspect by aspect
comparison and the porting notes.

Concept sections are added in registry order as each detail file is authored.
The registry that assigns concept numbers, and the format both this index and
the detail files follow, live in the `concept-mapping-builder` skill at
`../../concept-mapping-builder/ref/mapping-file-standard.md`. This index is
generated from the detail files and is not a place where new facts first appear.
When a concept below disagrees with its detail file, the detail file is correct.

## 1. Project prompt

The persistent project instruction file an agent loads at the start of every
session. Claude Code and Codex each read one canonical file, while Antigravity
has no single always-on file and spreads the role across a global file and a
project rules directory.

| Tool | Primary file or location |
|---|---|
| Claude Code | `CLAUDE.md` at repo root or `.claude/` |
| Codex | `AGENTS.md` at repo root |
| Antigravity | `.agents/rules/*.md` plus global `~/.gemini/GEMINI.md` |

Detail: [01-project-prompt.md](01-project-prompt.md)

---

## 2. Project settings

The project level configuration that controls model, permissions, MCP servers,
and related behavior. Claude Code and Codex each keep one committed config file
per scope, while the Antigravity CLI keeps its settings in one user level file
and has no project level settings file.

| Tool | Primary file or location |
|---|---|
| Claude Code | `.claude/settings.json` (plus `.claude/settings.local.json`) |
| Codex | `.codex/config.toml` in the repo |
| Antigravity | `~/.gemini/antigravity-cli/settings.json`; no project file |

Detail: [02-project-settings.md](02-project-settings.md)

---

## 3. Skills

Reusable capability packages defined by a `SKILL.md` file with YAML frontmatter,
loaded on demand and triggered explicitly or by description match. The three
tools converge on the same entry file and contract; Codex and Antigravity share
the tool neutral `.agents/skills/` path, while Claude Code uses `.claude/skills/`.

| Tool | Primary file or location |
|---|---|
| Claude Code | `.claude/skills/<name>/SKILL.md` |
| Codex | `.agents/skills/<name>/SKILL.md` |
| Antigravity | `.agents/skills/<name>/SKILL.md` |

Detail: [03-skills.md](03-skills.md)

---

## 4. Custom commands

User defined slash commands that expand a trigger into a saved prompt or
procedure. The concept has collapsed into skills: Claude Code merged its command
files into skills, Codex deprecated custom prompts for skills, and Antigravity
documents no separate mechanism at all, since a skill compiles directly into a
`/name` command. Antigravity workflows are a distinct multi step primitive.

| Tool | Primary file or location |
|---|---|
| Claude Code | `.claude/commands/*.md` (legacy, merged into skills) |
| Codex | `~/.codex/prompts/*.md` (deprecated, use skills) |
| Antigravity | a skill compiles into `/<name>`; no separate command mechanism |

Detail: [04-custom-commands.md](04-custom-commands.md)
