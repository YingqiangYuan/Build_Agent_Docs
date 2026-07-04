---
name: chinese-english-punctuation
description: Punctuation convention for mixed Chinese and English documents. Use when writing or revising any .md file whose narrative is mainly Chinese but whose technical terms stay in English, to keep every punctuation mark in its English (ASCII) form rather than the Chinese full width form. Trigger phrases include "写中文文档", "中英混排", "标点规范", "normalize punctuation", "fix Chinese punctuation", or any request that produces or edits Chinese narrative with English technical terms.
---

当你写的文档满足这样的风格时，本规范生效：叙述主要用中文，但专业术语名词 (如 Claude Code, hooks, MCP servers, Python) 保留英文。在这种风格里，所有标点符号一律使用英文 (ASCII) 标点，而不是中文全角标点。这样做的原因是：中英混排时全角标点和英文术语搭配显得突兀，英文标点渲染更一致，跨平台 (PDF, Lark Docs, Confluence) 转换也不会出现宽度错乱。

---

## 1. Punctuation Mapping

下面是核心对照表。左边是不要用的中文标点，右边是而要用的英文标点。

| 名称 | 不要 (中文全角) | 而要 (英文 ASCII) | 示例 |
| :--- | :--- | :--- | :--- |
| 逗号 | `，` | `,` | 它支持 hooks, skills 和 MCP servers |
| 顿号 | `、` | `,` | 支持 Claude Code, Codex, Antigravity |
| 句号 | `。` | `.` | 这是一个完整的句子. |
| 冒号 | `：` | `:` | 注意: 这里有个坑 |
| 分号 | `；` | `;` | 先做这个; 再做那个 |
| 问号 | `？` | `?` | 你确定吗? |
| 感叹号 | `！` | `!` | 真的很好用! |
| 圆括号 | `（ ）` | `( )` | 这是一个 AI 工具 (由 Anthropic 出品) |
| 双引号 | `“ ”` | `" "` | 我们把它叫做 "skill" |

顿号是一个容易忽略的点：中文习惯用 `、` 分隔并列项，但在这个风格里它也统一转成英文逗号 `,`。

---

## 2. Spacing Conventions

除了替换标点本身，这个风格还有几条配套的空格规范。它们都由本 skill 附带的脚本自动处理，理解它们有助于你在写作时就一次到位。

- 句内标点后面加一个空格。逗号, 句号, 冒号, 分号, 问号, 感叹号之后都跟一个空格 (行尾除外)。
- 中文与英文之间加一个空格。中文字符和相邻的英文单词或数字之间留一个空格, 例如 "使用 Python 3.12" 而不是 "使用Python3.12"。
- 圆括号贴合内容。左括号前留一个空格, 右括号后留一个空格; 但右括号后面若紧跟另一个标点, 则不加空格。
- 连续相同标点合并处理。`。。。` 转成 `...`, `？？？` 转成 `???`, `！！！` 转成 `!!!`, 中间不插空格。
- 成对 `**` 加粗标记内侧不留空格。`** 粗体 **` 规范为 `**粗体**`。

---

## 3. Lint After Writing

每当你写完或改完一个符合这个风格的 `.md` 文件, 用本 skill 附带的脚本 lint 一遍, 让标点和空格一次到位。脚本是纯标准库实现, 无需安装任何依赖, 直接原地修改文件 (类似 `lint --fix`)。

```bash
python "${CLAUDE_SKILL_DIR}/scripts/chinese_to_english_punctuation.py" path/to/doc.md
```

想先看看会不会改动而不真正写入 (例如在 CI 里做检查), 加上 `--check`。此时若有文件需要修改, 进程返回码为 1。

```bash
python "${CLAUDE_SKILL_DIR}/scripts/chinese_to_english_punctuation.py" --check path/to/doc.md
```

脚本可以一次处理多个文件, 把它们依次作为参数传入即可。它逐行套用第 1 节和第 2 节的全部规则, 所以运行之后文档就符合本规范了。
