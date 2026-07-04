# 项目简介: 把 Agent 文档蒸馏成 Skill

这个项目的底层逻辑, 是把各种编程 Agent 的官方文档蒸馏成 Skill. 这些 Agent 的命令, 配置和工作流更新得很快, 训练数据很容易过时, 所以我们不去死记文档, 而是把文档变成一个可复用的 Skill. 用上这个 Skill, Agent 就能随时拿到对应文档的最新知识, 回答有据可查, 贴合当前版本, 而不是凭记忆瞎猜.

在这层能力之上, 我们再去构建围绕 Agent 的各种其他 Skill, 让它们都站在准确, 最新的文档之上. 目前支持三个 Agent: Anthropic 的 Claude Code (简称 cc), OpenAI 的 Codex (简称 cdx), 以及 Google 的 Antigravity (简称 ag).
