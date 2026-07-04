# Project Overview: Distilling Agent Docs into a Skill

The core idea behind this project is to distill the official documentation of various coding agents into a Skill. These agents' commands, configuration, and workflows change fast, and training data goes stale just as fast — so instead of memorizing the docs, we turn the docs into a reusable Skill. With that Skill in hand, an agent can pull the latest knowledge from the relevant documentation on demand, giving answers that are grounded, current, and tied to the actual version in use, rather than guesses based on outdated memory.

On top of this capability, we then build a variety of other Skills around these agents, all standing on a foundation of accurate, up-to-date documentation. Three agents are currently supported: Anthropic's Claude Code (cc), OpenAI's Codex (cdx), and Google's Antigravity (ag).
