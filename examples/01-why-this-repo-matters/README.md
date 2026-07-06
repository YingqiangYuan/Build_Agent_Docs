# What This Repo Is Really Trying to Do

## 1. A coding agent looks like it writes code, but it's the one skill that sits above all other skills

Let's clear up something that gets misunderstood a lot. The name "coding agent" has the word "coding" baked into it, which makes it easy to file away as a programmer's tool — one more vertical skill, irrelevant to anyone who isn't writing software. That's exactly the misread this whole repo is built to correct. A coding agent can write code because, underneath, it's a generic feedback loop: give it a goal, it breaks the goal down, executes, checks the result, adjusts, and converges on an answer over successive rounds. Writing code just happens to be the first domain that loop landed in, because writing code barely needs any tooling beyond a text editor — so it was the easiest place to prove the idea out.

But the loop itself has nothing intrinsically to do with code. Bolt on the right tools for any other domain and it takes off there just as well:

* Designing experiments and analyzing data in scientific research
* Organizing source material and writing literature reviews in the humanities
* Helping a physician draft clinical notes
* Editing video or producing music for content creators

Here is the point that makes this different from any other skill you could pick up. Every other skill is **horizontal** — it makes you better at one field and stops there. This one is **vertical to all of them**: learn it well and you can pick up any field's tools and do that field's work, because the agent can. It is the one piece of knowledge in this era that sits *above* all other knowledge — a meta-skill whose payoff is every other skill at once. So if you're still treating a coding agent as a tool for programmers, you're already standing on the wrong side of the gap the next section is about to describe.

---

## 2. A gap of two or three generations

Precisely because this one skill sits above all the others, knowing how to wield it stops being a nice-to-have for technical roles and becomes the line that separates people in every role. Here's a chain of reasoning worth writing down right now, because the next few installments keep coming back to it: an agent's ceiling, provided you direct it well, is effectively unlimited, because it can pick up the tools of any domain and go do the work of that domain. Flip that around — if you want to become unstoppable, you don't need to personally become an expert in every field. You only need to deeply master the agent itself, and you inherit, indirectly, everything the agent is capable of mastering.

So the person who crosses that threshold doesn't end up one notch ahead in one skill. Their learning speed, the quality with which they absorb and process information, how precisely they communicate inside a team, and their overall output all end up **two or three generations** ahead of everyone who hasn't crossed it. And "deeply master the agent" doesn't mean knowing a few clever prompts — it means knowing how to make it teach itself something new, how to make it build, on its own, the ability to solve a problem it has never seen before. That is exactly what this repo is here to teach, and it's exactly what an interviewer is really probing when they ask "so, how do you actually use AI day to day" — underneath the question about a habit, they're checking whether your entire mental model has already been rebuilt for the AI era.

---

## 3. This course doesn't teach you facts — it teaches a three-layer way of attacking any problem

So what does "making the agent teach itself" actually look like as a habit? It's a three-layer way of attacking any problem — the thing I call **infinite recursive problem-solving**.

* **Layer 1 — throw the problem straight at the AI.** The ordinary move: hand the problem to the agent as-is and ask it to solve the surface of the question. Sometimes that's genuinely enough, and there's nothing wrong with it.
* **Layer 2 — build the expert first, then let the expert solve it.** The sharper move: don't solve the problem directly at all. First use the agent to *identify* what the problem really is, then build a super-expert agent specialized in this whole class of problem, and let *that* expert do the solving. You've stopped solving one problem and started building the thing that solves every problem of that shape.
* **Layer 3 — build the agent that builds the expert.** Sometimes you can't even build that expert yet. So you step back once more and build an agent whose job is to build the expert-agent — you learn to hand-craft the builder itself.

Why does stopping at three layers work? Because between them they cover every case. Any problem is either solved directly (Layer 1), or solved by an expert you build (Layer 2). If the expert you built *still* can't crack it, then the problem is effectively unsolvable — but notice you've *earned* that verdict by actually constructing the expert, not by guessing at it. And when you can't build the expert yet, you drop to Layer 3 and build the expert-builder. In principle it keeps going — Layer 4, Layer 5 — but you rarely need to spell the recursion out that far; the whole point is that a problem can always be decomposed one level further. That's why the habit is *infinite recursive problem-solving*: you never hit a dead end, you just recurse down one more level until you reach something you can build with your own hands, then assemble back up.

This repo lives at Layers 2 and 3. Think about an ordinary teacher: you ask, they answer once, and next time you're back to square one. The Layer-2 move is to build an expert agent whose entire job is teaching that one subject — available around the clock, never impatient, never going stale. The three documentation Skills in this repo are exactly that: three such experts, one each for Claude Code, Codex, and Antigravity. But the repo's real target is Layer 3 — it doesn't just hand you three finished experts, it teaches you to build one yourself. So what you walk away with was never "how to use Claude Code," a fact guaranteed to go stale. It's the underlying skill: "when a tool keeps changing under me, how do I build an expert that stays in sync and keeps teaching me." That's the method for building experts, not one particular expert.

---

## 4. Three experts already built, as examples — and a heads-up that this pattern runs four times

This expert-building method has already been proven out on three coding agents: `claude-code-docs`, `codex-docs`, and `antigravity-docs`, covering Claude Code, Codex, and Antigravity respectively. Each is responsible for discovering and reading the official documentation for its own tool, and can answer questions about installation, authentication, configuration, commands, workflows, automation, troubleshooting, and advanced usage — always grounded in the current version of the official docs, never in a stale impression from training data. The three tools organize their docs differently, so the internal implementation of each expert isn't identical either — a detail for the next installment. For now, just hold onto this: these three are three examples this method produced, not the full extent of the method itself. You can point the same approach at a fourth tool, a fifth, whatever comes next.

One thing worth planting now, because it's what the final installment pays off. This recursive move doesn't happen just once in this repo — it happens **four** times, nested inside each other. Building the documentation expert (Layer 1) is one complete recursion on its own. So is Layer 2. So is Layer 3. And then the three of them *combined* — taking Layer 3's goal as the real endpoint — form one larger recursion whose sub-steps are exactly Layers 1, 2, and 3. Three inner recursions, all wrapped inside a fourth, bigger one: think of it as **1 + 3** — one overarching decomposition built out of three smaller ones, four instances of the identical pattern. We won't rush all four at once. We start from the first — building a single expert — and lead you out from there.

---

## 5. This is only the first layer of the story

If this repo stopped here, it would amount to, at best, three carefully built expert agents. But it doesn't stop here: on top of these three experts, this repo adds two more layers of capability — one that aligns matching concepts across different agents, and one that actually executes a migration, carrying a project's configuration from one agent over to another. These three layers together are what this repo is really trying to show you, and that's what the next installment will unpack — the first of the four recursions we just flagged.

And whoever thinks the expert-building idea all the way through, end to end, and actually builds it, has already gotten hold of the key to that chain of reasoning from Section 2: you don't need to become unstoppable in every domain individually — you only need to deeply master the agent, and you inherit everything it touches. That might still sound a bit abstract right now. The next few installments will make it concrete.
