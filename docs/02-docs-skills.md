# The Three Docs Skills and Their Index Builder

The heart of this project is a set of three Skills, one for each agent's documentation: antigravity-docs for Google Antigravity (ag), claude-code-docs for Anthropic's Claude Code (cc), and codex-docs for OpenAI's Codex (cdx). What matters about them isn't that they copy documentation content into a file — it's that each one encodes the mechanism for how that agent's entire documentation index is organized, rather than hardcoding a fixed, frozen index. Every agent lays out its docs differently, so each Skill's mechanism has to be designed on its own terms; one template can't be stretched to fit all three.

That's exactly why simply loading one of these Skills is equivalent to gaining access to the corresponding agent's complete documentation. The trick is lazy loading combined with agentic search: a page only gets read when it's actually needed, with the agent following the index and searching its way there on its own, instead of stuffing the entire doc set into context up front. That keeps context usage low while guaranteeing the agent is always working from the current version of the docs.

---

## 1. The Companion Index Builder

Some of these documentation Skills ship with a companion index builder. Its job is narrow and specific: generate the index artifacts that the corresponding Skill depends on — it has no role in day-to-day documentation lookups. antigravity-docs-index-builder, for example, exists solely to produce the index that antigravity-docs relies on. When the upstream docs add, rename, or remove pages and the index falls out of date, this builder is what regenerates it, so the documentation Skill keeps pointing at the right pages.
