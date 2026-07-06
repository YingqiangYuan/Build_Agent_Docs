# learn_build_agent_docs_skill — teaching yourself to build "documentation experts"

This repo teaches one concrete thing: when you're facing a fast-moving AI coding tool (Claude Code, Codex, Antigravity…), how do you build a **documentation expert that never goes stale** — one that reads the live official docs every time instead of leaning on a moldy impression from training data? The repo does this in three layers: layer one is three documentation experts, layer two aligns the same concept across all three tools, and layer three carries a project's config from one tool to another. The real payoff isn't the three layers themselves — it's the idea running underneath all of them: **don't build the answer directly; build a mechanism that keeps producing the answer.**

## What is this — the methodology in 30 seconds

This is a "learn-this-project" repo: a small, deliberately-scoped codebase that teaches one vertical skill end-to-end. The point isn't to ship the code — it's to **absorb** the skill by running it, reading it, being able to defend every design choice, and finishing with a portfolio version on your own GitHub.

Six interactive skills make up the process:

- **`/learn-this-project-absorb`** — on-call mentor for the repo. Multi-mode: Orient (gives you the map + a `files to READ` vs `files to RUN/DO` split), Context-dive (you bring a `file:line`, it unpacks that spot), Next-step, Build (helps you extend the repo). It's a mentor, not a curriculum — use it when you need help, not as something to sit through linearly.
- **`/learn-this-project-quiz`** — discussion-style Q&A. Each answer is scored against the 3-part standard: **where to look + what + why**. A factually correct one-liner doesn't pass. Two modes: the pre-written bank (lower-bound check) and open-ended (you name a topic, it generates fresh questions).
- **`/learn-this-project-elevate`** — what's beyond this repo's current state. For each upgrade direction it walks you through current state → senior target → alternatives → prerequisite knowledge, and **converges into a concrete starter deliverable** you can hand back to Absorb Build mode to actually build.
- **`/learn-this-project-interview`** — full-project mock interview with pushback. Tests whether you can defend the work to a stranger.
- **`/learn-this-project-demo`** — script your live walk-through; the highest-value part is the "don't show teaching artifacts" cardinal-rule list.
- **`/learn-this-project-publish`** — convert this teaching repo into a portfolio version on your own GitHub. Deletes teaching artifacts, generates a commit cheat-sheet for you to copy-paste, co-writes your README in your own voice, finishes with a hostile-scan audit.

**Recommended order**: absorb → quiz → elevate → interview → demo → publish. The skills are mentors on call — invoke when you need orientation, context, or help. Not a curriculum to follow linearly.

## What's in this repo

The core isn't Python code — it's a set of Markdown skills under `.claude/skills/`, organized as a three-layer stack:

```
.claude/skills/
├── write-agent-skill/               # Layer 1 "generator": the method for writing a Skill
├── claude-code-docs/                # Layer 1: Claude Code documentation expert
├── codex-docs/                      # Layer 1: Codex documentation expert
├── antigravity-docs/                # Layer 1: Antigravity expert (reads a local manifest)
├── antigravity-docs-index-builder/  # rebuilds antigravity-docs' manifest
├── coding-agent-concept-mapping-builder/         # Layer 2 "generator" + the mapping-file standard
├── coding-agent-concept-mapping/                 # Layer 2: cross-tool concept alignment KB (01–08)
├── port-coding-agent-skill-generator/            # Layer 3 "generator": port + checker templates
└── port-<src>-to-<tgt>[-checker]/   # Layer 3: 6 directions x (doer + checker) = 12 skills

docs/learn-this-project/             # teaching analysis docs (01 inventory → 07 publish, 7 files)
examples/                            # six-part interview story + the "recursive decomposition" model
```

Every layer follows the same move: a *generator* comes first (left), a concrete output comes second (right) — `write-agent-skill` → the three doc experts, `coding-agent-concept-mapping-builder` → the concept files, `port-coding-agent-skill-generator` → the 12 migration skills. Information only ever flows up once, always as a fresh question, never as a cached old answer.

## The core idea — discover, verify, encode, test

The `examples/` folder tells the whole thing as a six-part interview story, and underneath the three layers there's one repeatable four-move skeleton worth internalizing:

- **Discover** — notice the mechanism others skim past (the "Copy page" button → the `llms.txt` index behind it).
- **Verify** — don't trust it; confirm `llms.txt` is a real, widely-adopted standard before building on it.
- **Encode** — turn the verified mechanism into a reusable skill (lazy-load the index, fetch 1–3 pages, cap at 9, cite sources).
- **Test** — run it against pages it has never seen and confirm every answer is grounded.

The same skeleton scales up: each layer sets an end goal, then works backward to a generator it can build directly — which is why the mental model transfers to any changing tool, and to problems with nothing to do with coding.

## Tech stack & setup

- **The product**: Agent Skills — a pile of `SKILL.md` files (Markdown + YAML frontmatter). "Running" means invoking a skill inside Claude Code, not executing code.
- **Fetching docs**: `WebFetch` (built into Claude Code); Antigravity's index is generated by a Python script, `build_manifest.py`.
- **Optional Python scaffolding**: Python 3.12 + uv (managed via mise). The skills don't depend on it — you can use every skill without it.

```bash
# optional — only needed to run the antigravity index script or touch Python
mise install            # installs python 3.12 + uv (see mise.toml)
mise run venv-create    # uv venv, creates .venv/
mise run inst           # uv sync --all-extras
```

The real entry point is `.claude/skills/` — asking `/claude-code-docs <question>` inside Claude Code is the fastest way to feel layer one.

## Recommended learning flow

Six skills, invoked in order (they're mentors — call them when you need them):

1. **`/learn-this-project-absorb`** — run Orient mode first for the map and the READ / RUN lists; use Context-dive when a specific `SKILL.md` or `ref/` file stumps you.
2. **`/learn-this-project-quiz`** — self-test on the bank; aim for a clean 10-question round; drill weak spots in open-ended mode.
3. **`/learn-this-project-elevate`** — pick 1–2 upgrade directions (testing, drift-detection, adding a fourth tool…) and converge a starter deliverable.
4. **`/learn-this-project-interview`** — run a full mock interview; the point is surviving pushback.
5. **`/learn-this-project-demo`** — rehearse the live walk-through; walk the cardinal-rule "do NOT show" list (`examples/`, `docs/learn-this-project/`, `tmp/` never hit the screen).
6. **`/learn-this-project-publish`** — turn the repo into a portfolio version.

> Note: the methodology recently evolved — absorb is now multi-mode (Orient / Context-dive / Next-step / Build / Resume) rather than a linear walkthrough; quiz scores against the "where + what + why" 3-part standard and has an open-ended mode; elevate ends by converging a starter deliverable and handing it to absorb Build mode; publish is the new sixth skill. The descriptions above reflect the current behavior.

## Publish — turn it into a portfolio artifact

Once you've learned it, `/learn-this-project-publish` converts this teaching repo into a clean portfolio piece on your own GitHub. There's one cardinal rule: **it must not read as tutorial material.** The skill walks you through:

- Deleting teaching artifacts (`examples/`, `docs/learn-this-project/`, the six `learn-this-project-*` skills, every `README-cn.md`, `README-ORIGINAL.md`, etc. — the skill performs the deletes with your consent);
- Generating `tmp/publish-commit-plan.md`, a dependency-ordered commit cheat-sheet you copy-paste yourself (the skill never touches git);
- Co-writing an English README in D-mode (it asks, you answer, it drafts, you edit), then running a hostile-scan audit that must return zero HIGH-RISK findings before you publish.

## What mastery looks like

You've mastered this when, faced with an unfamiliar and fast-changing tool, your reflex is to ask "what mechanism should I build for this?" and then run the four moves — discover → verify → encode → test — to produce a self-updating documentation expert. When you can explain why every layer is "generator first, output second," and why the porting-in notes are keyed by destination rather than direction. And when you can transplant this recursive-decomposition method onto problems that have nothing to do with coding (tracking papers, giving every teammate their own Scrum Master…). At that point what you hold isn't fluency with one tool — it's the skill of mastering tools itself. That's what this repo is really trying to leave you with.
