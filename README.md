# learn_build_agent_docs_skill-project

learn_build_agent_docs_skill is an Agent Skill designed to help coding agents discover, organize, and learn from the official documentation of other AI coding agents.

Modern coding agents evolve quickly. Their commands, configuration formats, built-in tools, permission models, extension systems, and recommended workflows may change frequently. Static knowledge embedded in a prompt, tutorial, or model training dataset can therefore become incomplete or outdated. This skill addresses that problem by providing a repeatable workflow for locating authoritative documentation, understanding its structure, identifying the most relevant pages, and turning that information into a practical documentation skill that an agent can use during future tasks.

The project is built around a simple principle: when an agent needs to understand another tool, it should rely on the tool’s current official documentation rather than assumptions, outdated examples, or unofficial summaries.

Instead of manually copying documentation into a large prompt, learn_build_agent_docs_skill teaches the agent how to discover the documentation dynamically. It can identify official documentation sources, map important sections, follow relevant links, extract operational knowledge, and organize the results into a reusable Agent Skill. The generated skill can then help answer questions about installation, authentication, configuration, commands, workflows, automation, troubleshooting, and advanced usage.

Three documentation targets are currently built:

* `claude-code-docs` — for Anthropic Claude Code (CLI, Agent SDK, hooks, MCP, skills, plugins, settings, subagents, admin). Anthropic API questions are deferred to the separate `claude-api` skill.
* `codex-docs` — for OpenAI Codex (CLI, IDE extension, app, cloud, sandboxing, skills, MCP, configuration, enterprise, integrations). Scoped to the Codex coding agent only; the general OpenAI API is out of scope.
* `antigravity-docs` (+ `antigravity-docs-index-builder`) — for Google Antigravity (the Antigravity 2.0 IDE, the Antigravity CLI, the SDK, agents/subagents, skills, rules/workflows, hooks, MCP, enterprise, migration).

The three share the same shape at answer time: pick the most relevant page(s) by description and fetch raw Markdown on demand — reading in small batches of 1–3 pages, evaluating whether that's enough, and continuing up to a 9-page cap before asking the user whether to keep going.

They differ in **how the docs are discovered**, because each platform serves them differently:

* Claude Code and Codex publish a machine-readable `llms.txt` index whose links resolve to raw `.md` twins, so those skills lazy-load the index and fetch pages directly.
* Antigravity's doc pages are a client-rendered single-page app with no fetchable page content, so its docs can't be discovered by fetching page URLs. Instead, `antigravity-docs-index-builder` extracts the doc map (`DOCS_STRUCTURE`) from the web app's JavaScript bundle, joins it with the titles/descriptions in `llms.txt`, and writes a local `docs-manifest.json`; the `antigravity-docs` skill then reads that manifest and fetches each page's separate `/assets/docs/....md` source. Splitting index-building from answering keeps the doc map refreshable (re-run the builder) without changing the lookup skill.

Each target follows this common methodology while preserving the terminology, documentation structure, and product-specific behavior of the original platform. This makes the project easier to maintain and extend without forcing all coding agents into a single generic documentation format.

The goal is not to create a permanent copy of every documentation page. Instead, the goal is to build a reliable discovery and learning process. Documentation URLs, page structures, commands, and features may change over time, so the skill prioritizes source verification, official references, and reproducible discovery steps. When possible, it should distinguish between stable concepts and version-sensitive details.

This project is useful for developers who work with multiple coding agents, educators who teach AI-assisted programming, teams that want standardized internal guidance, and Agent Skill authors who need a scalable way to package official product knowledge.

It can also serve as a reference implementation for building documentation-oriented skills for other tools. The same approach can be extended to programming frameworks, cloud platforms, developer tools, databases, command-line applications, SDKs, and APIs.

In summary, learn_build_agent_docs_skill provides a structured way to transform official documentation into reusable agent capability. It helps coding agents learn how a tool actually works, locate the right source when information changes, and produce more accurate, grounded, and maintainable answers.
