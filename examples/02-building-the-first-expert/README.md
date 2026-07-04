# How the First-Layer Expert Actually Gets Built

## 1. This Post Only Digs Into Layer One

The previous post explained that this repo has already used one consistent method to build three expert agents, [`claude-code-docs`](../../.claude/skills/claude-code-docs/SKILL.md), [`codex-docs`](../../.claude/skills/codex-docs/SKILL.md), and [`antigravity-docs`](../../.claude/skills/antigravity-docs/SKILL.md) — experts on Claude Code, Codex, and Antigravity respectively. But that post stayed at a pretty high level. It stopped at "there are three experts now" without actually opening one up to show how it gets built from scratch.

This repo is really three layers stacked on top of each other. The expert layer is just the bottom layer. Above it sits a second layer that aligns concepts across tools, and above that a third layer that actually carries out migrations. Trying to explain all three layers at once means none of them get explained well. So this post deliberately digs into only the first layer, using a single expert as the example — [`claude-code-docs`](../../.claude/skills/claude-code-docs/SKILL.md) — and walks through its entire journey from discovery to finished product, step by step. Layers two and three each get their own dedicated post later.

---

## 2. It Starts With a Web Page, and an Easy-to-Miss Button

The story starts with opening Claude Code's official documentation site. Navigate to the Quickstart page under Getting Started, and in the top-right corner there's a button that's easy to overlook: Copy page.

[Image: The Quickstart page on Claude Code's official documentation site, with the Copy page button highlighted in the top-right corner]

Most people skimming documentation do nothing more than read the rendered text on the page. But that button hints at something: behind this page there's a structured, raw version of the content that corresponds to what's rendered. What exactly gets copied when you click that button is worth digging into.

---

## 3. A Clue Hidden Inside the Copied Content

Clicking Copy page grabs the raw Markdown behind that page. The full content is saved in [claude-code-quick-start.md](./claude-code-quick-start.md). The first few lines look like this:

```markdown
> ## Documentation Index
> Fetch the complete documentation index at: https://code.claude.com/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# Quickstart

> Welcome to Claude Code!
```

These few lines look unremarkable, but they carry a lot of information. They're telling anyone reading this Markdown — human or agent — that this site has a dedicated index file listing every single page, located at `https://code.claude.com/docs/llms.txt`. This isn't part of the page's actual content; it reads more like a signpost the site left behind on purpose, pointing to a more complete map.

---

## 4. Following the Clue to the Site's Full Index

Following that signpost and fetching `llms.txt` gives content saved in [claude-code-llm.txt](./claude-code-llm.txt). Here's a short excerpt to get a feel for it:

```markdown
- [Explore the .claude directory](https://code.claude.com/docs/en/claude-directory.md): Where Claude Code reads CLAUDE.md, settings.json, hooks, skills, commands, subagents, workflows, rules, and auto memory.
- [Authentication](https://code.claude.com/docs/en/authentication.md): Log in to Claude Code and configure authentication for individuals, teams, and organizations.
```

Opening it up reveals that the entire site's several hundred documentation pages — every title, every summary, every link — have been flattened into a single list. And every link ends in `.md`, meaning these links don't point to rendered web pages but to raw Markdown text that can be fetched directly. No need to spin up a browser to render JavaScript, no need to painstakingly scrape the actual content out of HTML.

The reaction at this point was immediate: isn't this exactly the mechanism you'd want? A single index, covering the whole site, machine-readable, where every entry can be turned into one clean fetch. If an agent has this index in hand, it can in principle look up any page on demand, without needing to memorize the entire site.

---

## 5. Verify First, Build Second

Finding a mechanism that looks this good can't just be taken at face value and used right away. What if it's a one-off coincidence on this single page, or a temporary artifact left behind by some redesign? If so, anything built on top of it would be standing on sand from day one.

So the next move wasn't to rush into writing a Skill — it was handing this discovery to Claude to search the web and confirm: is `llms.txt` a widely adopted, officially recognized public convention, or something the Claude Code docs site made up on its own? The search confirmed it's a real standard, increasingly adopted across websites, aimed at AI agents — a way of telling visiting agents "there's a complete index here, look things up as needed, no need to crawl the whole site." With that confirmation in hand, the mechanism holds up and is worth turning into a capability you can depend on long-term, rather than a one-time stroke of luck.

---

## 6. Turning the Discovery Into a Skill, Testing It, and Now It's My Expert

Once the mechanism was confirmed reliable, it was time to actually build something. Using [`write-agent-skill`](../../.claude/skills/write-agent-skill/SKILL.md) — a tool built specifically for writing Agent Skills — the whole mechanism just discovered got written up as the [`claude-code-docs`](../../.claude/skills/claude-code-docs/SKILL.md) Skill.

What got encoded wasn't a handful of specific facts from the docs — it was a set of behavioral rules, the logic of agentic search: first read `llms.txt` to get the index, match the most relevant entries against the question at hand, fetch only 1 to 3 pages at a time in each batch, and after each batch check whether that's enough to answer the question. If not, fetch the next batch. If the total reaches 9 pages fetched and it's still not enough, stop and honestly tell the user what's been found so far, what's still missing, and ask whether to keep going. The reasoning behind this rule is straightforward: a site with hundreds of pages of documentation doesn't need to be dumped into context all at once. Fetching on demand saves tokens and guarantees what gets read is always the current version.

Writing the Skill doesn't mean trusting it works — it has to be tested. Pick a few pages on the docs site that had never been looked at before, ask the newly written [`claude-code-docs`](../../.claude/skills/claude-code-docs/SKILL.md) a handful of questions completely unrelated to Quickstart, and see what happens. Every time, it correctly used the index to locate the right page, fetched it, and gave a well-grounded answer.

At this point, the thread that started with a Copy page button has really run its full course: discover a mechanism, verify it's reliable, encode it as a set of rules that can be invoked repeatedly, then test whether it actually works. Once that whole process is done, what you're left with isn't a pile of copied documentation — it's a portable Claude Code expert you can carry around and query anytime. This is exactly what the previous post meant by "teach you to build the expert that teaches you," fully realized at this first layer — and it's what actually gets built at the bottom layer of this repo. How the second layer teaches these three experts to cross-reference each other, and how the third layer puts that cross-referencing to work in real migrations, are covered in detail in the next post.
