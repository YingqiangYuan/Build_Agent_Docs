# 三个文档 Skill 与配套的索引构建器

这个项目最核心的三个 Skill 是三个 agent 的文档 Skill: antigravity-docs 对应 Google Antigravity (ag), claude-code-docs 对应 Anthropic 的 Claude Code (cc), codex-docs 对应 OpenAI 的 Codex (cdx). 它们的精髓不在于把文档内容抄进来, 而在于描述 "整套文档索引是怎么组织的" 这套机制本身, 而不是 hardcode 一份写死的索引. 每个 agent 的文档结构都不一样, 所以每个 Skill 的机制都得单独设计, 不能一套模板套到底.

正因为如此, 这几个 Skill 只要一打开, 就相当于掌握了对应 agent 的全部文档. 它靠的是 lazy load 加载配合 agentic search: 需要哪一页才去读哪一页, agent 自己顺着索引去检索, 而不是一次性把所有内容塞进 context. 这样既省 context, 又保证拿到的永远是当前版本的文档.

---

## 1. 配套的 index-builder

其中一部分文档 Skill 会带一个配套的 index-builder. 它的职责很单一: 生成对应 Skill 所依赖的 index artifacts, 而不参与日常的文档查询. 比如 antigravity-docs-index-builder 就是专门用来产出 antigravity-docs 那份索引的. 当上游文档新增, 改名或删除页面, 导致索引过时的时候, 就靠它把索引重新生成一遍, 让文档 Skill 继续指向正确的页面.
