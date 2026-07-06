# 用 generator 制造 Port 工具

有了文档 Skill 和 coding-agent-concept-mapping 之后, 真正要干的活是迁移: 把一个项目里针对某个 agent 的配置搬到另一个 agent 上. 这靠的是一族 port Skill. 每一对 agent, 每个方向, 都需要两个 Skill: 一个 port-<source>-to-<target> 负责真正执行迁移, 另一个 port-<source>-to-<target>-checker 只读地审查迁移得全不全, 把差距报告写到项目的 tmp/review-port-<source>-to-<target>.md. 三个 agent 两两互转是 6 个方向, 每个方向两个 Skill, 一共 12 个.

关键在于, 这 12 个 Skill 我们不手写, 而是用 port-coding-agent-skill-generator 来制造. 手工维护 12 份文件太容易走样, 所以 generator 只认两个模板, 一个 port 模板, 一个 checker 模板, 所有共有的行为都写在模板里. 开发者敲 /port-coding-agent-skill-generator cc to cdx (或者写全名 claude code to codex) 这样一条命令, generator 就解析出源和目标 agent, 套进模板, 把两个 SKILL.md 生成或覆盖出来. 要改所有 port Skill 的行为, 就改模板再重新生成, 绝不去手动改生成出来的文件.

这里有一条刻意画下的界线: agent 名单是 hardcode 的, 概念清单不是. 有哪几个 agent, 它们的规范名, slug 和对应的 docs Skill, 这份名单小而稳定, 加第四个 agent 是罕见的事, 可以写死在 generator 的对照表里. 但可迁移的概念 (project prompt, settings, skills, hooks, MCP servers, subagents, permissions 等等) 一直在长, 所以模板里绝不写死概念清单. 生成出来的 port 和 checker Skill 每次运行都从 coding-agent-concept-mapping 的索引里现读概念, 顺着它去查 docs, 再执行迁移或写审查报告. 这样一来, 加了新概念不用碰这 12 个 Skill, 只要 coding-agent-concept-mapping 更新了就自动生效.
