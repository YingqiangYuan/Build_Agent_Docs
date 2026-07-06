# The Mental Model Holding This Whole Story Together

## 1. Stepping outside this repo to see what's actually holding the story up

The first five parts stayed inside this one repo: why it's worth learning, how the first layer got built, how it all rolled up into an interview story, how layers two and three actually work under the hood, and how to handle follow-up questions about it. This part does something different. It steps outside the repo entirely and pulls out, on its own, the mental model that's been holding the whole story together — and makes the case that this model isn't just a trick that happens to work for this one repo.

If this mental model only worked for telling this one story, its value would be capped at that one story. What actually makes it valuable is that it transfers, unmodified, to any problem that has nothing to do with Claude Code or this repo. [The previous part](../05-answering-follow-up-questions/README.md) already showed two of these transfers near the end. This part is going to spell out the general rule behind that transfer — and then, at the end, show you the two concrete ways to *use* all of this in an interview.

---

## 2. What this mental model actually is: recursive decomposition, taken as far as it needs to go

The name sounds abstract, but broken down it's just a handful of very concrete moves, taken one at a time — the same three-layer ladder [Part 1](../01-why-this-repo-matters/README.md) opened with:

* First ask yourself what the real end goal is — not the step in front of you, but the outcome you actually need at the end.
* Ask whether you can build that end goal directly and reliably. If yes, just build it. Done. (This is Layer 1 — hand it straight to the agent.)
* If not, don't grind through it manually one layer at a time. Instead, step back and ask: can I build a mechanism — an expert — that keeps producing this end goal, reliably, on an ongoing basis? (Layer 2.)
* If you can't even build that expert yet, step back again and ask whether you can build a mechanism whose job is to build that mechanism. (Layer 3.)
* Keep stepping back until you hit a point where you genuinely can just build the thing with your own hands. That point is your foundation.
* Once the foundation is built, assemble back upward in the reverse order: use the bottom layer to build the layer above it, use that layer to build the one above it, and keep going until you're back at the original end goal.

That's the full meaning of "start from the end goal" combined with "recursion." Starting from the end goal decides where the stepping-back should stop; recursion is what tells you that each step back lands you in a smaller version of the exact same problem, solved with the exact same line of questioning, just at a smaller scale.

---

## 3. This model runs four times inside this repo — the "1 + 3"

[Part 1](../01-why-this-repo-matters/README.md) planted this and promised to pay it off here: the same recursive move doesn't show up once in this repo, it shows up **four** times, each smaller one nested inside a bigger one. [Part 2](../02-building-the-first-expert/README.md) and [Part 4](../04-building-layers-two-and-three/README.md) already walked all four in concrete detail:

* It ran once **inside layer one**: the end goal was a Claude Code expert that wouldn't go stale, so the plan stepped back to build `write-agent-skill`, a method for writing Skills, and then used that method to build `claude-code-docs`.
* It ran again **inside layer two**: the end goal was a reliable concept-alignment knowledge base, so the plan stepped back to build `concept-mapping-builder`, and then used that to produce concrete alignment files like `03-skills.md`.
* It ran again **inside layer three**: the end goal was twelve migration tools that stay faithful to the source, so the plan stepped back to build `port-skill-generator`, and then used that to stamp out all twelve Skills.
* And then it ran **once more across all three layers stitched together**, at an even bigger scale: the end goal was enterprise-grade cross-agent migration capability. Working backward, that required layer three, which required layer two, which required layer one.

That's the **1 + 3**: three inner recursions (one per layer), all wrapped inside a single larger recursion whose sub-steps are exactly those three layers. The same line of questioning, applied at four different scales, each smaller one nested inside a bigger one. Using a pattern once doesn't prove much. Finding it show up again and again, nested inside the very same project, is what proves you've actually grasped the skeleton of the model — not just noticed a coincidence.

---

## 4. Why this isn't specific to this repo

[The previous part](../05-answering-follow-up-questions/README.md) already transplanted this model twice on its own: once into content tracking, and once into something with zero connection to Claude Code — building a personal Scrum Master expert for every member of an agile team. Both transplants used the exact same line of questioning; only the end goal and the final buildable step changed.

The reason this transplants so cleanly is that the model isn't keyed to "Claude Code" or even to "coding agents." It's keyed to three more abstract situations: the end goal keeps changing, so memorizing today's answer is guaranteed to go stale; there's a large amount of nearly identical, only-the-details-differ work sitting in front of the end goal, so doing it by hand will eventually drift out of sync; or building the end goal directly is simply too big a lift, while building a mechanism that keeps churning out that end goal is a manageable scope instead. These three situations show up in essentially every industry, at every scale of problem — which is exactly why [Part 1](../01-why-this-repo-matters/README.md) opens by establishing that a coding agent is, at bottom, the one skill that sits above all other skills. This mental model is how you wield that meta-skill. It isn't some feature bolted onto the skill itself.

---

## 5. How to actually use this in an interview — two plays

Everything above is why the model matters. This section is about cashing it in. Once you've genuinely internalized this ability, what you're holding is not "I know Claude Code" — it's a general ability to **solve any problem, learn any field, and become a domain expert on demand.** The hard part in an interview is *proving* that, and this is where most people fall down. Be honest about the constraint: in any single interview your time and energy are limited, so you cannot possibly be an all-knowing expert on everything the interviewer might raise. Plenty of candidates say "I'm a fast learner" — but a claim with no evidence behind it doesn't stick. The whole game is to leave the interviewer with a *proven* impression: this person can learn any body of knowledge, become an expert in any field fast, and decompose and solve any problem. There are two situations where you cash this in, and they cover almost everything.

### Play A — they ask about a skill or field you already know

Do the prep work *before* the interview: take a skill you're already fluent in, and deliberately run this method over it — re-derive it end to end, and build the expert for it by hand (the discover → verify → encode → test pass). Now, when the interviewer brings up that skill, you don't just answer the question — you open it up: "let me actually show you how I learned this." You surface the ability naturally, and you tell the true story: the first time I used this method is the repo I'm about to show you; since then I've used it to learn countless other skills — and the one you just asked me about happens to be one I decomposed exactly the same way. What the interviewer sees is that you learned the skill *and* carried the method across into a different domain. The takeaway they're left with is the valuable part: any future field, skill, or problem you haven't met yet, you can handle. Ordinary candidates dread the thought "what if they ask about something I don't know?" and fall back on "I'd learn it quickly" — with nothing to back it. You've already backed it, live, with evidence — so the interviewer simply stops worrying about whether you can pick up new things.

> One boundary carried over from [Part 3](../03-the-interview-story/README.md): the thing you put on screen is always the **real, live Skill** you built (under `.claude/skills/`), never the `examples/` tutorial folder. You're showing a working artifact you produced, not the course you learned it from.

### Play B — they ask about a field you don't know at all

You can bring the exact same thing out here too. Say it plainly: "I don't know this specific thing yet, but I have a rough sense of what it is, and I'm confident I can get there — I have an AI-native method for becoming an expert in any field fast," and then walk them through the method. The impression you leave is identical in shape: the moment this interview is over, you'll point this exact method at the topic, decompose it, learn it, and become the expert — so the fact that you don't know it *right now* stops being a liability. Interviewers find that genuinely reassuring, because you've reframed "I don't know X" into "I have a reliable process for coming to know any X."

### And when they don't ask a concrete question at all

Put the two together. When the question is about a domain you know → flex the muscle and, in the same motion, *prove* you're a genuine quick learner. When it's about a domain you don't → still show the method, and convey the one message that matters: give me a little time and I can handle anything. And when they don't ask a specific technical question at all — a behavioral question meant only to size you up as a person — you can convey exactly the same thing, not by talking about yourself, but by *demonstrating*. Pulling up real artifacts you built has visual impact and is evidence-based; it lands orders of magnitude harder than a candidate simply asserting "I'm a fast learner." This is a long point, but it's the one you should walk away with: in an interview, this ability is not something you describe — it's something you *show*.

---

## 6. Back to the opening line of Part 1 — this is the thing actually being tested

[Part 1](../01-why-this-repo-matters/README.md) mentioned that when companies specifically screen for "AI proficiency," what they're really trying to confirm is whether a candidate's thinking has actually been rebuilt for the AI era. Now that claim can be stated more precisely: what's actually being tested is exactly this capacity for recursive decomposition — when you run into a problem where the end goal keeps shifting, keeps repeating, or is too big to tackle head-on, is your first instinct to ask "what mechanism should I build for this," or is it to roll up your sleeves and grind through it by hand?

Knowing how to use AI to write code only proves you can operate a tool. Understanding this line of questioning well enough to run it fresh on any new problem — and, as Section 5 showed, being able to *demonstrate* it on demand — proves something else entirely: that this person has grown an AI-era thinking framework into their own instincts. That's the real point [Part 3](../03-the-interview-story/README.md) is making with the line from the interview script: "the way I use AI is what I call solving problems through unlimited recursive decomposition."

---

## 7. After finishing all six parts, the real task is making this yours

If, after reading all six parts, all you've retained is the name of this repo's three-layer architecture, you've read them for nothing. What you actually need to walk away with is the entire cycle — discover, verify, encode, test, and start-from-the-end-goal nested inside itself layer after layer, the 1 + 3 — internalized as your own default reflex the moment you hit any problem, to the point where you can say "I built this myself" in an interview and mean it, rather than reciting a case study someone else wrote.

Being able to explain this on the spot in an interview, field the follow-up questions, proactively draw new parallels the way [the previous part](../05-answering-follow-up-questions/README.md) did — and, above all, *show* it with the two plays in Section 5 — that alone is the strongest possible proof: proof that this person's habits and mental model for using AI let them decompose any problem, in any industry, at any scale, indefinitely, all the way down to a buildable first step, and then reassemble it back up layer by layer. What the person across the table takes away isn't "this person knows how to use Claude Code." It's that this person's ceiling with AI is effectively unlimited. That's where the reasoning chain [Part 1](../01-why-this-repo-matters/README.md) opened with finally pays off in full.
