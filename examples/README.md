# Examples Index: Six Stories, One Mental Model

The README at the repo root explains what this repo technically does: it's an Agent Skill that teaches a coding agent how to discover, organize, and learn from other coding agents' official documentation, written for developers who will use it, maintain it, or build on top of it. This `examples/` folder is a different thing entirely. It's written for an outside reader who hasn't touched any other doc in this repo, and the goal isn't to re-explain the technical implementation — it's to distill the entire experience of building this repo into a story you could actually tell in a job interview, and, underneath that story, a transferable mental model you can carry into any industry and apply to any problem. Read the six pieces in order — each one builds on facts established in the last.

---

## 01-why-this-repo-matters

First, a correction to a common misconception: a coding agent looks like a tool for writing code, but underneath, it's a general-purpose productivity engine that can be bolted onto any industry. Starting from that premise, this piece lays out why people who learn to build agent experts will end up two or three generations ahead of people who don't, then explains what this repo is actually for: teaching you how to build your own expert that keeps learning on its own, rather than just handing you pre-packaged knowledge about a handful of tools.

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

This piece steps outside the repo entirely and isolates the mental model holding the whole story together: infinite recursive decomposition. It makes the case that this model isn't unique to this repo — it applies to problems of any size in any industry — and closes with the last piece of the puzzle: after reading all six, the real work is internalizing this model as your own skill.

[The mental model holding this whole story together](./06-the-mental-model-recursive-decomposition/README.md)
