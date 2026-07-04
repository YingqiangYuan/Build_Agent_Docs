# A Story You Can Actually Tell in an Interview

## 1. It Starts With "So, How Do You Actually Use AI Day to Day"

Sooner or later in an interview, someone asks this question, or some version of it: how do you actually use AI, walk me through an example. It sounds casual, but it's a filter.

Most people's first instinct is to give an answer that sinks: I use it to write code, I use it to look things up, I use it to polish some copy. None of these answers are wrong, but they all sink, because they describe a task AI did for you, not the actual relationship between you and the AI. [The previous post](../02-building-the-first-expert/README.md) already laid out a concrete example in full. This post takes that example and tightens it into a story you can pull out on the spot.

---

## 2. The Story Isn't an Architecture Overview — It's One Complete Run at Building an Expert

A common mistake is thinking the story should be about how big the repo is, how many layers it has, what each layer is called. That kind of telling sounds like reciting an architecture doc from memory, and the interviewer has no way to tell whether you actually did the work or just memorized someone else's write-up.

The story that actually holds up is the specific, complete, start-to-finish experience from [the previous post](../02-building-the-first-expert/README.md): opening Claude Code's official docs, noticing an easy-to-miss "Copy page" button, following a hint in the copied text to discover the site's full documentation index, `llms.txt`, not taking it at face value but first having Claude go online to confirm this was a recognized, official mechanism and not something made up, and only after confirming that, using [`write-agent-skill`](../../.claude/skills/write-agent-skill/SKILL.md) to turn that discovery into a Skill called [`claude-code-docs`](../../.claude/skills/claude-code-docs/SKILL.md), then testing it against pages never read before to confirm it actually worked. Every step of this was done firsthand, so no matter which step the interviewer probes, there's a real answer. That's what makes a story hold up, instead of leaving the interviewer half-convinced by a vague overview.

---

## 3. The Skeleton of the Story: Discover, Verify, Encode, Test

This experience holds up under questioning because it naturally has a clean skeleton, four moves, none of which can be skipped:

* Notice a detail nobody else paid much attention to — a button, a hint in some text
* Don't take it on faith — verify whether that detail points to something real, reliable, and durable
* Turn the verified mechanism into a reusable rule, not something you use once and throw away
* Test it against a new, unseen situation to confirm it actually holds up

When you tell the story this way, these four steps become the natural paragraphs. As the interviewer listens, it comes across as someone who works methodically, not someone who got lucky poking around. This skeleton isn't unique to this one story either — later posts in this series will reuse it again and again.

---

## 4. Why This Story Proves "You Know How to Use AI"

[The first post](../01-why-this-repo-matters/README.md) laid out a chain of reasoning: an agent's capabilities are close to unlimited, so mastering an agent deeply means indirectly mastering everything that agent can master, and deep mastery isn't about knowing a few good prompts, it's about knowing how to get the agent to teach itself something new. This experience is a complete, concrete instance of that reasoning chain: nobody spoon-fed you how Claude Code works, you discovered the mechanism behind its docs yourself, verified it, turned it into an expert that keeps itself current, and the whole process can be reused as-is on any third-party tool, not just Claude Code.

When an interviewer asks "how do you actually use AI," on the surface they're asking about a habit, but what they really want to know is whether your relationship with AI is active or passive. Once you've told this story, the answer is obvious: you're not passively waiting for AI to hand you answers, you're teaching it how to keep producing answers for you, and you know how to check whether it's trustworthy. That's exactly what the reasoning chain was meant to prove, and exactly what this line of questioning is really trying to surface.

---

## 5. What to Deliberately Leave Out

The fastest way to sink this story is to keep going and dump the entire repo's architecture on the table — volunteering that there's a second layer that aligns concepts across different tools, and a third layer that handles migration. Doing this only dilutes the story, turning one concrete experience into an incomplete architecture briefing. It comes across as rushing to show off how much you know, rather than recounting something you actually did.

When telling this story, deliberately stick to just how this one expert was built, and hold back layers two and three unless asked. This isn't because you haven't fully absorbed layers two and three — a later post will go through them in depth, and by then you'll genuinely understand them. The reason to hold back is this: dumping every detail up front doesn't make you look like you understand it more, it makes you look like you memorized a script. Letting the other person ask follow-up questions, and you catching each one as it comes, is itself what proves you actually think in an AI-native way — that you can naturally break any question down to whatever depth they push, instead of front-loading everything you know.

---

## 6. Where You're Standing Once the Story Is Told

Once you've told this story, you're no longer just answering "how do you use AI" — you're demonstrating a method: observe, verify, encode, validate. This time the method was used to build a documentation expert for Claude Code, but it's clearly not limited to that one use case.

The more solid the story lands, the more likely it is to invite deeper follow-up questions. How to handle those follow-ups is what the next post covers.

---

## 7. What to Actually Say — A Script You Can Deliver As-Is

Everything above is the reasoning behind it. When you're actually in the interview, you need something you can just say out loud. Not every interview lets you share your screen — when you can, follow the stage directions below; when you can't, skip the stage directions and just say the line clearly, adapting as needed. One more boundary to keep in mind: the only thing you should ever show an interviewer is the actual, live Skill under `.claude/skills/` — never expose the `examples/` tutorial folder. That's where you rehearse the story, not the material for the story itself.

The opening line matters most — it sets the tone for everything that follows:

> The way I use AI is what I call infinite recursive problem solving. The approach is to work backward indefinitely — start from the goal and keep breaking it down until you hit something you can actually act on, then build back up from there one step at a time.

> For example, when I need AI to solve a problem, my first move isn't to solve it myself — it's to first build a super-agent that can solve it, and then let that agent solve the problem. If I find I can't build that agent yet, I step back further and build an agent that can build that agent.

> Here's a real example. At one point I needed an expert that could tell me, at any time, the latest way to use Claude Code. But Claude Code updates fast, and I didn't want to build an expert whose knowledge would go stale.

*(If screen sharing is available: open Claude Code's official Quickstart page, https://code.claude.com/docs/en/quickstart, so the interviewer can see this is the live official documentation, not your own notes.)*

> I was going through the official docs and noticed a "Copy page" button in the top right corner.

*(If screen sharing is available: click Copy page, and either read the first few lines of the copied content out loud or paste it so they can see it directly.)*

> The copied content opened with a note saying the entire site has a complete documentation index, called llms.txt.

*(If screen sharing is available: open https://code.claude.com/docs/llms.txt so they can see what this index looks like.)*

> I pulled down that index and found the whole site — hundreds of pages — compressed into one flat list, where every line could be turned into one clean fetch. I didn't just trust it — I first had Claude go online to confirm that llms.txt is a widely adopted, officially recognized public convention, not something this one site improvised on its own. Once that checked out, I used write-agent-skill to turn this discovery into a Skill.

*(If screen sharing is available: finally, open this repo and navigate to [`.claude/skills/claude-code-docs/SKILL.md`](../../.claude/skills/claude-code-docs/SKILL.md), so they can see that everything just described is now a real file that actually gets invoked — not a screenshot or a slide — and scroll to the Procedure section to point out the rule about reading one to three pages at a time, up to nine pages max.)*

> Inside this Skill, I defined a specific rule: read one to three pages at a time, check after each batch whether that's enough to answer the question, and if not, read the next batch. If it's still not enough after nine pages, stop honestly, tell the other party what was found, what's missing, and ask whether to keep going — instead of reading the entire site and wasting tokens. After writing it, I tested it against several pages it had never seen before, and confirmed it could reliably find the right page and give a well-grounded answer every time.

> Now this Skill is the Claude Code expert I carry around with me. It never goes stale, because it reads the live official docs fresh every time, instead of relying on some snapshot answer I once taught it. But this expert by itself isn't the end goal — as I put it to work on real problems, I keep running into new edge cases, and each time I do, I iterate on it again to make it more accurate. What's actually valuable isn't this one expert — it's that I now know how to build this kind of expert. From here on, whenever I run into a tool that changes over time, or any new problem, I can follow the same playbook and build a new expert to solve it. That's what I mean by infinite recursive problem solving: I didn't grind through learning how to use Claude Code myself — I built an expert that keeps itself fresh, and I know how to keep building more of them.

*(Stage direction: pause deliberately here and leave a hook. This has only covered how one expert was built. If they follow up by asking whether these experts might conflict with each other, or how you'd move a configuration from one agent to another, that's them asking about layers two and three — pick it up from there when it happens.)*

The script ends here, deliberately stopping at layer one. In the real system, two more layers support all of this — one that keeps concepts aligned across different agents, and one that actually moves configuration from one agent to another. How those two layers were built is what the next post will unpack, step by step, using the same approach.
