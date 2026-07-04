# Concept Mapping 与它的 builder

有了三个文档 Skill 之后, 还缺一层东西: 同一个概念在不同 agent 里是怎么对应的. concept-mapping 这个 Skill 干的就是这件事. 它的做法是先锁定一个概念, 比如 hooks, MCP servers, subagents 或者 permissions, 然后去读三个 agent 的官方文档, 把 "同一个想法在 Claude Code, Codex, Antigravity 里各自长什么样" 写成一份对照的 mapping, 当作参考. 它以 Claude Code 为基准来命名和拆解每个概念, 另外两个工具的列则说明它们怎么实现同一个想法, 或者干脆没有对应物. 重点不是三份各自独立的词典, 而是它们之间的对齐, 外加把一套配置从一个工具搬到另一个工具时会踩到的坑.

这样就有了一条清晰的分流规则. 如果用户问的是某个特定 code agent 的东西, 就走对应的文档 Skill (docs). 如果问的是一个多个 agent 共有的概念, 想知道它们之间怎么对应, 就走 concept-mapping. 前者回答 "这个工具怎么做", 后者回答 "这几个工具之间怎么换算".

---

## 1. 配套的 builder

和文档 Skill 一样, concept-mapping 也有一个配套的 builder, 叫 concept-mapping-builder. 它负责维护 mapping 本身, 而不参与日常查询. 它读的是三个文档 Skill (claude-code-docs, codex-docs, antigravity-docs), 把每一条结论都落在官方文档上, 而不是凭训练记忆写. 新增一个概念, 某个工具改了文档需要刷新, 或者要把各个概念文件汇总成索引的时候, 都靠它来写, 保证 concept-mapping 那边始终一致, 只管在回答时读取.
