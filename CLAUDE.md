## What This Project Does

`learn_build_agent_docs_skill` is an Agent Skill that teaches coding agents to
discover, organize, and learn from the *official* documentation of other AI
coding agents — rather than relying on outdated training data or assumptions.
Because tools like Claude Code, Gemini, and Codex change their commands, config,
and workflows frequently, the skill provides a repeatable process: find the
authoritative docs, map their structure, follow relevant links, extract
operational knowledge, and package it into a reusable documentation skill. It
currently targets Claude Code, Google Gemini (antigravity), and OpenAI Codex.
The goal is not to copy docs, but to build a reliable discovery-and-learning
workflow that produces accurate, grounded, source-verified answers.

## Development Setup

**Package Manager:** uv (via mise)

**Core Configuration Files:**
- `mise.toml` - Project tasks and tool versions (Python 3.12, uv)
- `pyproject.toml` - Dependencies and project metadata
- `.venv/` - Virtual environment directory

**Available Tasks:**
- `mise run venv-create` - Create Python virtual environment
- `mise run venv-remove` - Remove virtual environment
- `mise run inst` - Install Python dependencies
