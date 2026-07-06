# Examples Index: Six Stories, One Mental Model

The README at the repo root explains what this repo technically does: it's an Agent Skill that teaches a coding agent how to discover, organize, and learn from other coding agents' official documentation, written for developers who will use it, maintain it, or build on top of it. This `examples/` folder is a different thing entirely. It's written for an outside reader who hasn't touched any other doc in this repo, and the goal isn't to re-explain the technical implementation — it's to distill the entire experience of building this repo into a story you could actually tell in a job interview, and, underneath that story, a transferable mental model you can carry into any industry and apply to any problem. Read the six pieces in order — each one builds on facts established in the last.

> 🧭 **The one idea under all six parts.** A coding agent isn't just another skill — it's the one skill that sits *above* all other skills: master it and you can learn any field and solve any problem, because the agent can. The way you wield it is **infinite recursive problem-solving**, a three-layer habit: (L1) hand the problem straight to the AI; (L2) don't solve it — build an expert agent that solves the whole class of problem, and let it solve; (L3) if you can't build that expert, build the agent that builds it. This repo runs that exact move **four** times, nested — the **"1 + 3"**: three inner recursions (one per layer) wrapped inside one larger recursion. That nesting is the proof you've grasped the model, not a coincidence.

> 🎯 **The payoff — how to *use* this in an interview (Part 6, §5).** This ability is something you **show**, not something you describe. Two plays: **(A)** when asked about a skill you already know, pre-build its expert with this method and walk the interviewer through how you learned it — proving, with a live artifact, that you're a genuine quick learner; **(B)** when asked about a field you *don't* know, show the method itself — "give me a little time and I can become the expert in anything." Real artifacts have visual impact and carry evidence; a candidate merely claiming "I learn fast" doesn't. (Always show the live Skill under `.claude/skills/`, never the `examples/` tutorial folder.)

---

## 01-why-this-repo-matters

First, a correction to a common misconception: a coding agent looks like a tool for writing code, but underneath it's the one skill that sits above all other skills — learn it and you can pick up any field, because the agent can. Starting from that premise, this piece lays out the two-or-three-generation gap that opens up between people who wield it and people who don't, defines the three-layer **infinite-recursive-problem-solving** model (throw it at the AI → build the expert → build the agent that builds the expert), and plants the **"1 + 3"** heads-up: this same recursion runs four times across the repo, and we'll start from the first.

[What this repo is actually trying to do](./01-why-this-repo-matters/README.md)

---

## 02-building-the-first-expert

This piece digs into just the first layer, using a single example: the `claude-code-docs` expert. It starts with digging through the official docs and noticing an easy-to-miss "Copy page" button, follows that thread to the site's full documentation index, checks whether this is actually an official and reliable mechanism, and then turns the discovery into a working Skill and tests it — walking through, start to finish, what building an expert actually looks like.

[How the first-layer expert actually got built](./02-building-the-first-expert/README.md)

---

## 03-the-interview-story

This piece folds the first two into a story you can tell in an interview, and explains why that story only needs the first layer as its example — deliberately holding back layers two and three unless asked. It comes with a ready-to-use script, spelling out everything from your opening line to exactly when to show the interviewer what.

[A story you can actually tell in an interview](./03-the-interview-story/README.md)

---

## 04-building-layers-two-and-three

This piece goes back and lays out the full implementation of layers two and three. It starts by explaining why they're worth building at all — one is about accelerating how fast you learn, the other is about enterprise-grade portability across agents, so you're never locked into one platform — and then walks through concrete examples of how each layer actually got built. This is the longest piece of the six.

[How layers two and three actually got built](./04-building-layers-two-and-three/README.md)

---

## 05-answering-follow-up-questions

This piece preps you for the follow-up questions an interviewer is likely to ask. For each one, it first calls out what the interviewer is really trying to probe, then gives you a ready-to-use answer. The second half walks through two proactive examples that prove this approach works far beyond this repo, in situations that have nothing to do with it.

[When the interviewer pushes back, here's how to respond](./05-answering-follow-up-questions/README.md)

---

## 06-the-mental-model-recursive-decomposition

This piece steps outside the repo entirely and isolates the mental model holding the whole story together: infinite recursive decomposition. It makes the "1 + 3" nesting explicit, argues the model applies to problems of any size in any industry, and then — the most practical part — spells out the **two interview plays** for actually *using* this ability (show it, don't describe it), before closing with the last piece of the puzzle: after reading all six, the real work is internalizing this model as your own skill.

[The mental model holding this whole story together](./06-the-mental-model-recursive-decomposition/README.md)
