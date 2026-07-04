# examples 索引, 六篇故事讲透一个思维模型

仓库根目录的 README 说的是这个 repo 技术上做了什么: 一个教 coding agent 去发现, 组织, 学习其他 coding agent 官方文档的 Agent Skill, 面向的是要用它, 要维护它, 要基于它扩展的开发者. 这里的 `examples/` 是另一件事, 面向的是没读过 repo 任何其他文档的外部读者, 目的不是再讲一遍这个 repo 的技术实现, 而是把造这个 repo 的完整经历收拢成一个能在面试里讲出来的故事, 以及故事背后一套可以带着走, 用在任何行业任何问题上的思维模型. 六篇按顺序读, 后一篇都建立在前一篇讲过的事实上.

---

## 01-why-this-repo-matters

先纠正一个容易被误解的事: coding agent 表面上是写代码的工具, 骨子里是任何行业都能装上的通用生产力引擎. 在这个前提下, 说明学会造 agent 专家的人, 会跟不会的人产生两三代的代差, 再交代这个 repo 到底在做什么: 教你怎么自己造一个会持续学习的专家, 而不是把某几个工具的知识直接塞给你.

[这个 repo 到底要干一件什么事](./01-why-this-repo-matters/README-cn.md)

---

## 02-building-the-first-expert

只挖第一层, 而且只用 `claude-code-docs` 这一个专家举例. 从翻官方文档发现一个不起眼的 Copy page 按钮开始, 顺着线索找到全站的文档索引, 先验证这是不是一个官方可靠的机制, 再把发现写成一个 Skill 并测试, 完整看一遍造专家的过程长什么样.

[第一层专家, 是怎么被真的造出来的](./02-building-the-first-expert/README-cn.md)

---

## 03-the-interview-story

把前两篇收拢成一个能在面试里讲出来的故事, 说明为什么故事只需要第一层这一个例子就够, 讲的时候刻意不主动提二, 三层. 附上一份可以照读的讲稿, 从开场白到该在什么时候给面试官看什么, 都写清楚了.

[一个能在面试里讲出来的故事](./03-the-interview-story/README-cn.md)

---

## 04-building-layers-two-and-three

回头把二, 三层的底层实现完整摊开. 先讲清楚为什么要造它们, 一个是学习加速, 一个是企业级的跨 agent 迁移能力, 不怕被某个平台锁定, 再用具体例子走一遍这两层是怎么造出来的. 这是六篇里篇幅最长的一篇.

[第二, 三层, 是怎么被真的造出来的](./04-building-layers-two-and-three/README-cn.md)

---

## 05-answering-follow-up-questions

准备几个面试官大概率会问的追问, 每一个都先点破背后想考察的东西, 再给一段可以直接照讲的回答. 后半段是两个主动出击的例子, 证明这套方法能搬到跟这个 repo 毫无关系的场景上.

[面试官追问了, 该怎么接](./05-answering-follow-up-questions/README-cn.md)

---

## 06-the-mental-model-recursive-decomposition

跳出这个 repo 本身, 把撑住整个故事的思维模型单独讲清楚: 无限递归拆解. 说明这套模型不是这个 repo 的专利, 能用在任何行业任何规模的问题上, 也补上最后一块: 学完这六篇真正要做的, 是把它内化成自己的能力.

[撑住这整个故事的思维模型](./06-the-mental-model-recursive-decomposition/README-cn.md)
