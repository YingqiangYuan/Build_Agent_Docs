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
