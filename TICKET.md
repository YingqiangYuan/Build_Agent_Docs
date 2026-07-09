# TICKET: Building Self-Updating Documentation-Expert Skills for AI Coding Agents — Learning Checklist

[Tutorial](https://github.com/easyscale-academy/learn_build_agent_docs_skill-project/tree/01-Learn-This-Project/)

## Objective

Track your progress absorbing this repo's core skill: building a documentation expert that reads live official docs (never stale training data), and the three-layer architecture — doc experts → concept alignment → automated migration — that repeats the "build a mechanism, not the answer" move. By the end you should be able to build one of these experts from scratch and defend every design choice.

## Checklist

### Setup
- [X] Clone the repo and switch to the `01-Learn-This-Project` branch
- [X] Open the repo in Claude Code and confirm the skills load — run `/claude-code-docs` with any question and verify it fetches a live doc URL and cites it
- [X] (Optional) Bootstrap the Python scaffolding: `mise install && mise run venv-create && mise run inst` — note this is NOT required to use the skills
- [X] Confirm your run-list from `docs/learn-this-project/02-runbook.md` § B: the things you actually *invoke* are the skills (`/claude-code-docs`, `/codex-docs`, `/antigravity-docs`, `/coding-agent-concept-mapping`, `/port-coding-agent-skill-generator`, the 12 `port-*` skills) — not Python scripts

### Absorb (learn the content)
- [X] Run `/learn-this-project-absorb` in **Orient mode** for the high-level map and the `files to READ` vs `files to RUN/DO` lists
- [X] Work through the run-list yourself: invoke each layer's skills and read what they return (ask a doc expert about a page you've never seen; run `/coding-agent-concept-mapping` on a concept; read a `port-*/SKILL.md`)
- [X] Come back to `/learn-this-project-absorb` in **Context-dive mode** whenever a specific `SKILL.md`, `ref/` file, or procedure needs unpacking
- [X] Knowhow: explain **why all three doc experts re-read their index fresh every run instead of caching page content** — and what would silently break if they cached (`01-knowhow-inventory.md#claude-code-docs`)
- [X] Knowhow: explain **why `antigravity-docs` uses a local `docs-manifest.json` + an index-builder** while `claude-code-docs` and `codex-docs` fetch `llms.txt` live (the SPA constraint) (`01-knowhow-inventory.md#antigravity-docs`)
- [X] Knowhow: explain the repeated **"generator first, output second"** move across all three layers, and **why the 12 port skills are generated and split into doer + checker** (`01-knowhow-inventory.md`, `examples/04`)

### Quiz (verify understanding)
- [-] Run `/learn-this-project-quiz` in **Bank mode** — clear the floor (no ⚠️ partial / ❌ wrong on a 10-question round)
- [-] Use **Open-ended mode** to drill 2–3 topics where you came up shallow (e.g. the O(N) porting-in-notes design, the runtime concept-list read in Layer 3)
- [-] (If anything keeps coming up partial, go back to the relevant analysis doc or `SKILL.md`, then re-quiz)

### Elevate (see what's beyond)
- [ ] Run `/learn-this-project-elevate`, explore 1–2 upgrade directions (e.g. automated verification/CI, drift-detection canary, adding a fourth tool like Gemini CLI)
- [ ] **Converge each chosen direction into a concrete starter deliverable** (e.g. "add `tests/test_no_placeholders.py` that asserts no generated `port-*/SKILL.md` still contains a template placeholder")
- [ ] (Optional, high-value) Hand the deliverable to `/learn-this-project-absorb` in **Build mode** and actually build the first iteration
- [ ] Note down "next small projects" that interest you

### Interview (pressure-test yourself)
- [ ] Run `/learn-this-project-interview`, complete a full mock session
- [ ] Review the debrief; for the 3 weak-spot questions, return to quiz / absorb and re-cover the gap

### Demo (learn to present)
- [ ] Run `/learn-this-project-demo`, rehearse at least the 5-minute version (open a live doc expert; show it citing a real doc URL)
- [ ] Walk through the cardinal-rule "do NOT show" list — `examples/`, `docs/learn-this-project/`, `tmp/`, and the `learn-this-project-*` skills must not appear on screen during the demo

### Mastery Gate
- [ ] You can answer ~70% of quiz questions to the 3-part standard (where + what + why), not just factually
- [ ] You can survive at least one pushback round per interview question
- [ ] You have a clear list of "what I'd study next" from the elevate session
- [ ] You can deliver the demo without notes, without exposing any cardinal artifact

### Publish (turn it into a portfolio artifact)
- [ ] Decide on a new public repo name (pattern: `<firstname>-<lastname>-agent-docs-skill-poc`)
- [ ] Run `/learn-this-project-publish` in **Transform mode** — the skill walks you through:
- [ ] Intake: new repo name + your name
- [ ] Delete cardinal teaching artifacts (skill does this with your consent)
- [ ] Borderline review (your call on each file — e.g. the `tmp/` Gemini-CLI prototype, the non-meta `lesson-smith-*` skills)
- [ ] Generate `tmp/publish-commit-plan.md` (your copy-paste cheat-sheet)
- [ ] Co-write your `README.md` in your own voice (D-mode — it asks, you answer, it drafts, you edit)
- [ ] Verify **Audit mode** returns 0 🔴 HIGH RISK findings before publishing
- [ ] Create the public GitHub repo yourself (skill won't do this)
- [ ] Open `tmp/publish-commit-plan.md` and run the 10–15+ commits one at a time
- [ ] `git remote add origin <github-url>` and `git push -u origin main`
