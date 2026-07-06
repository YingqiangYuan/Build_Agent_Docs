# Concept Mapping and Its Builder

Once you have three documentation Skills in place, one thing is still missing: how does the same concept show up across different agents? That's exactly what the coding-agent-concept-mapping Skill handles. It starts by picking a concept — say, hooks, MCP servers, subagents, or permissions — then reads the official docs for all three agents and writes up a side-by-side mapping of "what does this same idea look like in Claude Code, Codex, and Antigravity" for future reference. It uses Claude Code as the baseline for naming and breaking down each concept, while the columns for the other two tools describe how they implement the same idea, or note that there's simply no equivalent. The point isn't three separate glossaries — it's the alignment between them, plus a heads-up on the pitfalls you'll hit when porting a configuration from one tool to another.

That gives us a clean routing rule. If the user is asking about something specific to one coding agent, route to that agent's documentation Skill (docs). If the user is asking about a concept shared across multiple agents and wants to know how they map to each other, route to coding-agent-concept-mapping. The former answers "how does this tool do it"; the latter answers "how do these tools translate to one another."

---

## 1. The Companion Builder

Just like the documentation Skills, coding-agent-concept-mapping has its own companion builder: coding-agent-concept-mapping-builder. It's responsible for maintaining the mapping itself and stays out of day-to-day queries. It reads the three documentation Skills (claude-code-docs, codex-docs, antigravity-docs) and grounds every conclusion in the official docs rather than writing from memory. Whenever a new concept needs adding, a tool's docs change and the mapping needs refreshing, or the individual concept files need to be rolled up into an index, this is the builder that does the writing — keeping coding-agent-concept-mapping consistently up to date while it stays purely read-only at query time.
