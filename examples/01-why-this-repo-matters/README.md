# What This Repo Is Really Trying to Do

## 1. A coding agent looks like it writes code, but underneath it's a general-purpose productivity engine

Let's clear up something that gets misunderstood a lot. The name "coding agent" has the word "coding" baked into it, which makes it easy to assume this is just a tool for writing software, something irrelevant to anyone who isn't a programmer. That's not what's actually going on. A coding agent can write code because, at its core, it's a feedback loop: give it a goal, it breaks the goal down, executes, checks the result, adjusts, and converges on an answer over successive rounds. Writing code just happens to be the first domain where this loop landed, because writing code barely needs any extra tooling beyond a text editor — so it's the easiest place to verify the idea and the first place it got proven out.

But the feedback loop itself has nothing intrinsically to do with code. Hook it up to the right tools for any other domain, and it takes off there just as well:

* Designing experiments and analyzing data in scientific research
* Organizing source material and writing literature reviews in the humanities
* Helping a physician draft clinical notes
* Editing video or producing music for content creators

None of these have anything to do with typing out code, but from the agent's point of view, it's just a different toolbelt — the feedback loop underneath is completely generic. So if you're still treating a coding agent as a tool exclusively for programmers, you're already on the path to being left behind by the kind of generational gap this document is about to describe, because what this thing actually is, is a general-purpose productivity engine that any industry, any profession, can put to use.

---

## 2. A gap of two or three generations

Precisely because this engine is general-purpose, knowing how to use it stops being a nice-to-have for technical roles and becomes the dividing line that separates people in every role. Once you cross that threshold — once you learn to turn your everyday workflows into Agent Skills, build tools for the agent, and wire it into your own file system and habits — your learning speed, the quality with which you absorb and process information, how precisely you communicate within your team, and your overall output will all end up two or three generations ahead of people who haven't crossed it.

Here's a chain of reasoning worth writing down right now, because the next few installments will keep coming back to it: an agent's capability, provided you're skilled enough at directing it, is effectively unlimited, because it can pick up the tools of any domain and go do the work of that domain. Flip that around: if you want to become unstoppable, you don't need to personally become an expert in every field. You only need to deeply master the agent itself, and you inherit, indirectly, everything the agent is capable of mastering. And "deeply mastering the agent" doesn't mean knowing how to write a few clever prompts — it means knowing how to get it to teach itself something new, how to get it to build, on its own, the capability to solve a problem it's never seen before. That is exactly what this repo is here to teach.

This is also exactly why companies have started probing for this specifically in interviews. When an interviewer asks "how do you use AI day to day," on the surface they're asking about a habit, but what they're really trying to figure out is: has your mental model, your cognitive framework, already been rebuilt for the AI era? Have you developed the instinct to start from the end goal, break a problem down without limit, and hand each piece to whichever role — human or agent — is best suited to solve it?

---

## 3. This course doesn't teach you facts, it teaches you to build the expert that teaches you

Think about what an ordinary teacher looks like. You have a specific question, you want to learn a specific thing, the teacher teaches you, the session ends, and next time you have a new question you have to go back and find the teacher again, or go figure it out yourself from scratch.

A sharper approach looks like this: rather than personally teaching you every single time, build yourself an expert agent whose entire job is teaching that one subject. This expert agent is available around the clock, you can ask it anything anytime, it never gets impatient, and what it knows doesn't go stale just because a human teacher's memory does. That alone is already a serious upgrade — and the three documentation Skills in this repo are exactly that: three expert agents, one each for Claude Code, Codex, and Antigravity.

But what this repo actually wants to teach you sits a level above even that. It's not just handing you three ready-made expert agents and calling it done — it's teaching you how to build one of these expert agents yourself. In other words, this course was never about teaching you "how to use Claude Code," a fact that will inevitably go stale. It's about teaching the underlying skill of: "when I run into a tool that keeps changing, how do I build an expert agent that stays in sync with it and keeps teaching me." Once you've internalized that, you're no longer limited to three tools — you can handle any tool, any body of knowledge that keeps shifting under your feet, because what you're holding is the method for building experts, not just one particular expert.

---

## 4. Three experts already built, as examples

This expert-building method has already been proven out on three coding agents: `claude-code-docs`, `codex-docs`, and `antigravity-docs`, covering Claude Code, Codex, and Antigravity respectively. Each of these three experts is responsible for discovering and reading the official documentation for its own tool, and can answer questions about installation, authentication, configuration, commands, workflows, automation, troubleshooting, and advanced usage — always grounded in the current version of the official docs, never in a stale impression left over from training data.

The three tools organize their documentation differently, so the internal implementation of each expert isn't identical either — that's a detail for the next installment to unpack. For now, just remember this: these three are merely three examples this method has produced, not the full extent of the method itself. You can absolutely use the same approach to build a new expert for a fourth tool, a fifth tool, whatever comes next.

---

## 5. This is only the first layer of the story

If this repo stopped here, it would amount to, at best, three carefully built expert agents. But it doesn't stop here: on top of these three experts, this repo adds two more layers of capability — one that aligns matching concepts across different agents, and one that actually executes a migration, carrying a project's configuration from one agent over to another. These three layers together are what this repo is really trying to show you, and that's what the next installment will unpack.

And whoever thinks the expert-building idea all the way through, end to end, and actually builds it, has already gotten hold of the key to that chain of reasoning: you don't need to become unstoppable in every domain individually — you only need to deeply master the agent, and you inherit everything it touches. That might still sound a bit abstract right now. The next few installments will make it concrete.
