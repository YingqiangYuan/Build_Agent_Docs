# learn_build_agent_docs_skill - 教自己造"文档专家"的项目

这个仓库教的是一件具体的事: 当你面对一个更新飞快的 AI 编程工具 (Claude Code, Codex, Antigravity...) 时, 怎么造一个**永远不会过时的文档专家** - 它每次都去读官方最新文档, 而不是靠训练数据里那份早就发霉的印象。仓库把这件事做成了三层: 第一层是三个文档专家, 第二层把同一个概念在三个工具之间对齐, 第三层能把一个项目的配置从一个工具搬到另一个工具。真正值钱的不是这三层本身, 而是贯穿始终的那套思路 - **不要直接造答案, 而是造一个能不断产出答案的机制**。

## What is this - 30 秒讲清楚方法论

这是一个 "learn-this-project" 仓库: 一个刻意做小, 边界清晰的代码库, 用来端到端地吃透一项垂直技能。重点不是把代码跑起来交付, 而是**通过运行它, 读它, 能为每一个设计决策辩护, 最后在自己的 GitHub 上留下一个作品集版本**来真正吸收这项技能。

整个过程由六个交互式 skill 组成:

- **`/learn-this-project-absorb`** - 仓库的随叫随到导师。多模式: Orient (给你全景图 + 一份 `files to READ` 和 `files to RUN/DO` 的清单), Context-dive (你带着 `file:line` 来, 它拆解那个具体位置), Next-step, Build (帮你扩展仓库)。它是导师, 不是课程 - 需要帮助时再叫它, 而不是从头到尾坐着听。
- **`/learn-this-project-quiz`** - 讨论式问答。每个回答都按三段标准打分: **去哪看 + 是什么 + 为什么**。一句话的正确答案不算过。两种模式: 预置题库 (保底检查) 和开放模式 (你点一个话题, 它现场出题)。
- **`/learn-this-project-elevate`** - 这个仓库当前状态之外还能做什么。对每个进阶方向, 它带你走一遍 current state -> senior target -> 备选方案 -> 前置知识, 并**收敛成一个具体的起步交付物**, 你可以把它交回 Absorb 的 Build 模式真正动手做。
- **`/learn-this-project-interview`** - 针对整个项目的模拟面试, 带 pushback。测你能不能向陌生人为这份工作辩护。
- **`/learn-this-project-demo`** - 给你的现场演示排练脚本; 最值钱的部分是那份 "不要展示教学痕迹" 的红线清单。
- **`/learn-this-project-publish`** - 把这个教学仓库转成你自己 GitHub 上的作品集版本。删掉教学痕迹, 生成让你复制粘贴的 commit 清单, 用你自己的口吻共写 README, 最后跑一遍敌意扫描审计。

**推荐顺序**: absorb -> quiz -> elevate -> interview -> demo -> publish。这些 skill 是随叫随到的导师 - 需要定位, 需要上下文, 需要帮助时再调用, 不是一条要线性走完的课程。

## 这个仓库里有什么

核心不是 Python 代码, 而是一堆 `.claude/skills/` 下的 Markdown skill, 按三层架构组织:

```
.claude/skills/
├── write-agent-skill/               # Layer 1 的"生成器": 写 Skill 的方法本身
├── claude-code-docs/                # Layer 1: Claude Code 文档专家
├── codex-docs/                      # Layer 1: Codex 文档专家
├── antigravity-docs/                # Layer 1: Antigravity 文档专家 (读本地 manifest)
├── antigravity-docs-index-builder/  # 重建 antigravity-docs 的 manifest
├── concept-mapping-builder/         # Layer 2 的"生成器" + mapping-file 标准
├── concept-mapping/                 # Layer 2: 跨工具概念对齐知识库 (01-08)
├── port-skill-generator/            # Layer 3 的"生成器": port + checker 两个模板
└── port-<源>-to-<目标>[-checker]/   # Layer 3: 6 个方向 x (执行 + 审计) = 12 个迁移 skill

docs/learn-this-project/             # 教学分析文档 (01 清单 -> 07 发布清单, 共 7 份)
examples/                            # 六篇面试故事 + "递归拆解"心智模型
```

每一层都遵循同一个套路: 先有一个 "生成器" (左), 再产出具体的东西 (右) - `write-agent-skill` -> 三个文档专家, `concept-mapping-builder` -> 概念文件, `port-skill-generator` -> 12 个迁移 skill。信息永远只向上流动一次, 且永远是一个新鲜的提问, 从不缓存旧答案。

## 核心思路 - discover, verify, encode, test

`examples/` 目录把整件事写成了六篇面试故事, 而三层架构底下其实只有一个可复用的四步骨架, 值得刻进肌肉记忆:

- **Discover** - 注意到别人一扫而过的机制 (那个 "Copy page" 按钮 -> 它背后的 `llms.txt` 索引)。
- **Verify** - 不轻信; 先确认 `llms.txt` 是被广泛采用的公开标准, 再在它上面搭东西。
- **Encode** - 把验证过的机制写成一个可复用的 skill (懒加载索引, 每次抓 1-3 页, 封顶 9 页, 引用来源)。
- **Test** - 拿它从没见过的页面去测, 确认每个回答都有据可依。

同一个骨架还会向上放大: 每一层都先定一个终点目标, 再倒推到一个自己能直接造出来的生成器 - 这正是为什么这套心智模型能搬到任何持续变动的工具上, 也能搬到跟编程毫无关系的问题上。

## 技术栈与准备

- **本体**: Agent Skills, 也就是一堆 `SKILL.md` (Markdown + YAML frontmatter)。真正的"运行"是在 Claude Code 里调用 skill, 不是执行代码。
- **抓文档**: `WebFetch` (Claude Code 内置); Antigravity 的索引由一个 Python 脚本 `build_manifest.py` 生成。
- **可选的 Python 脚手架**: Python 3.12 + uv (通过 mise 管理)。skill 本身不依赖它, 装不装都能用。

```bash
# 可选 - 只有你想跑 antigravity 索引脚本或碰 Python 时才需要
mise install            # 装 python 3.12 + uv (见 mise.toml)
mise run venv-create    # uv venv, 建 .venv/
mise run inst           # uv sync --all-extras
```

真正的入口是 `.claude/skills/` - 在 Claude Code 里直接问 `/claude-code-docs <问题>` 就能感受到第一层。

## 推荐学习流程

六个 skill, 按顺序调用 (它们是导师, 需要时才叫):

1. **`/learn-this-project-absorb`** - 先跑 Orient 模式拿到全景图和 READ / RUN 清单; 卡在某个 `SKILL.md` 或 `ref/` 文件时用 Context-dive。
2. **`/learn-this-project-quiz`** - 用题库自测, 目标是一轮 10 题不出现 partial / wrong; 薄弱处用开放模式加练。
3. **`/learn-this-project-elevate`** - 挑 1-2 个进阶方向 (测试, 漂移检测, 加第四个工具...), 收敛出一个起步交付物。
4. **`/learn-this-project-interview`** - 完整走一遍模拟面试, 重点练能不能扛住 pushback。
5. **`/learn-this-project-demo`** - 排练现场演示, 走一遍红线清单 (`examples/`, `docs/learn-this-project/`, `tmp/` 等绝不上屏)。
6. **`/learn-this-project-publish`** - 把仓库转成作品集版本。

> 说明: 这套方法论最近有更新 - absorb 现在是多模式 (Orient / Context-dive / Next-step / Build / Resume) 而非线性走一遍; quiz 按 "去哪看 + 是什么 + 为什么" 三段标准打分且有开放模式; elevate 结尾会收敛出一个起步交付物并交回 absorb Build 模式; publish 是新增的第六个 skill。下面的描述都是当前行为。

## 发布 (Publish) - 把它变成作品集

学完之后, `/learn-this-project-publish` 帮你把这个教学仓库转成你自己 GitHub 上的干净作品集。红线只有一条: **不能被看出来这是从教程里来的**。这个 skill 会带你走:

- 删除教学痕迹 (`examples/`, `docs/learn-this-project/`, 六个 `learn-this-project-*` skill, 所有 `README-cn.md`, `README-ORIGINAL.md` 等 - 删除动作由 skill 在你确认后执行);
- 生成 `tmp/publish-commit-plan.md` 这份按依赖顺序排好的 commit 清单, 由你自己复制粘贴执行 (skill 从不碰 git);
- 用 D 模式跟你共写英文 README (它问, 你答, 它起草, 你改), 最后跑一遍敌意扫描审计, 确认 0 个 HIGH RISK 才算过。

## 学到什么程度算掌握

当你能对着一个从没见过的、还在快速迭代的工具, 条件反射地问出 "我该给它造个什么机制", 然后走完 discover -> verify -> encode -> test 这四步造出一个自我更新的文档专家; 当你能解释为什么每一层都是 "先造生成器再产出结果", 为什么 porting-in notes 按目标而非方向组织; 当你能把这套 "递归拆解" 的思路原样搬到跟编程毫无关系的问题上 (追踪论文, 给团队每个人配一个 Scrum Master...) - 这时你掌握的就不是某一个工具, 而是"掌握工具"这件事本身。这才是这个仓库真正想留给你的东西。
