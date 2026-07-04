# The Mental Model Holding This Whole Story Together

## 1. Stepping outside this repo to see what's actually holding the story up

The first five parts stayed inside this one repo: why it's worth learning, how the first layer got built, how it all rolled up into an interview story, how layers two and three actually work under the hood, and how to handle follow-up questions about it. This part does something different. It steps outside the repo entirely and pulls out, on its own, the mental model that's been holding the whole story together — and makes the case that this model isn't just a trick that happens to work for this one repo.

If this mental model only worked for telling this one story, its value would be capped at that one story. What actually makes it valuable is that it transfers, unmodified, to any problem that has nothing to do with Claude Code or this repo. [The previous part](../05-answering-follow-up-questions/README.md) already showed two of these transfers near the end. This part is going to spell out the general rule behind that transfer.

---

## 2. What this mental model actually is: recursive decomposition, taken as far as it needs to go

The name sounds abstract, but broken down it's just a handful of very concrete moves, taken one at a time:

* First ask yourself what the real end goal is — not the step in front of you, but the outcome you actually need at the end.
* Ask whether you can build that end goal directly and reliably. If yes, just build it. Done.
* If not, don't grind through it manually one layer at a time. Instead, step back and ask: can I build a mechanism that keeps producing this end goal, reliably, on an ongoing basis?
* If you can't even build that mechanism yet, step back again and ask whether you can build a mechanism whose job is to build that mechanism.
* Keep stepping back until you hit a point where you genuinely can just build the thing with your own hands. That point is your foundation.
* Once the foundation is built, assemble back upward in the reverse order: use the bottom layer to build the layer above it, use that layer to build the one above it, and keep going until you're back at the original end goal.

That's the full meaning of "start from the end goal" combined with "recursion." Starting from the end goal decides where the stepping-back should stop; recursion is what tells you that each step back lands you in a smaller version of the exact same problem, solved with the exact same line of questioning, just at a smaller scale.

---

## 3. This model doesn't show up just once in this repo

[Part 2](../02-building-the-first-expert/README.md) and [Part 4](../04-building-layers-two-and-three/README.md) already walked through this model in concrete detail — and not just once:

* It ran once inside layer one: the end goal was a Claude Code expert that wouldn't go stale, so the plan stepped back to build `write-agent-skill`, a method for writing Skills, and then used that method to build `claude-code-docs`.
* It ran again inside layer two: the end goal was a reliable concept-alignment knowledge base, so the plan stepped back to build `concept-mapping-builder`, and then used that to produce concrete alignment files like `03-skills.md`.
* It ran again inside layer three: the end goal was twelve migration tools that stay faithful to the source, so the plan stepped back to build `port-skill-generator`, and then used that to stamp out all twelve Skills.
* And then it ran once more across all three layers stitched together, at an even bigger scale: the end goal was enterprise-grade cross-agent migration capability. Working backward, that required layer three, which required layer two, which required layer one.

The same line of questioning, applied at four different scales, each smaller one nested inside a bigger one. Using a pattern once doesn't prove much. Finding it show up again and again, nested inside the very same project, is what proves you've actually grasped the skeleton of the model — not just noticed a coincidence.

---

## 4. Why this isn't specific to this repo

[The previous part](../05-answering-follow-up-questions/README.md) already transplanted this model twice on its own: once into content tracking, and once into something with zero connection to Claude Code — building a personal Scrum Master expert for every member of an agile team. Both transplants used the exact same line of questioning; only the end goal and the final buildable step changed.

The reason this transplants so cleanly is that the model isn't keyed to "Claude Code" or even to "coding agents." It's keyed to three more abstract situations: the end goal keeps changing, so memorizing today's answer is guaranteed to go stale; there's a large amount of nearly identical, only-the-details-differ work sitting in front of the end goal, so doing it by hand will eventually drift out of sync; or building the end goal directly is simply too big a lift, while building a mechanism that keeps churning out that end goal is a manageable scope instead. These three situations show up in essentially every industry, at every scale of problem — which is exactly why [Part 1](../01-why-this-repo-matters/README.md) opens by establishing that a coding agent is, at bottom, a general-purpose productivity engine that can be pointed at any domain. This mental model is how you drive that engine. It isn't some feature bolted onto the engine itself.

---

## 5. Back to the opening line of Part 1 — this is the thing actually being tested

[Part 1](../01-why-this-repo-matters/README.md) mentioned that when companies specifically screen for "AI proficiency," what they're really trying to confirm is whether a candidate's thinking has actually been rebuilt for the AI era. Now that claim can be stated more precisely: what's actually being tested is exactly this capacity for recursive decomposition — when you run into a problem where the end goal keeps shifting, keeps repeating, or is too big to tackle head-on, is your first instinct to ask "what mechanism should I build for this," or is it to roll up your sleeves and grind through it by hand?

Knowing how to use AI to write code only proves you can operate a tool. Understanding this line of questioning well enough to run it fresh on any new problem proves something else entirely: that this person has grown an AI-era thinking framework into their own instincts. That's the real point [Part 3](../03-the-interview-story/README.md) is making with the line from the interview script: "the way I use AI is what I call solving problems through unlimited recursive decomposition."

---

## 6. After finishing all six parts, the real task is making this yours

If, after reading all six parts, all you've retained is the name of this repo's three-layer architecture, you've read them for nothing. What you actually need to walk away with is the entire cycle — discover, verify, encode, test, and start-from-the-end-goal nested inside itself layer after layer — internalized as your own default reflex the moment you hit any problem, to the point where you can say "I built this myself" in an interview and mean it, rather than reciting a case study someone else wrote.

Being able to explain this on the spot in an interview, field the follow-up questions, and even proactively draw new parallels the way [the previous part](../05-answering-follow-up-questions/README.md) did — that alone is the strongest possible proof: proof that this person's habits and mental model for using AI let them decompose any problem, in any industry, at any scale, indefinitely, all the way down to a buildable first step, and then reassemble it back up layer by layer. What the person across the table takes away isn't "this person knows how to use Claude Code." It's that this person's ceiling with AI is effectively unlimited. That's where the reasoning chain [Part 1](../01-why-this-repo-matters/README.md) opened with finally pays off in full.
