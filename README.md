# laoli-paper

`laoli-paper` 是一个面向学术论文写作的 Codex skill。当前包含一个核心模块：`introduce`，用于根据用户提供的论文 Methods / 方法部分，反推出论文 Introduction 的研究背景、研究空白、方法动机和贡献列表。

这个 skill 的写作风格来自一类固定的论文引言套路：不是泛泛地写“背景-不足-本文方法”，而是把问题组织成“复杂任务压力 -> 两类已有方法 -> 双瓶颈或核心矛盾 -> 双模块方法对位 -> 贡献闭环”。

## 本次版本更新

- **压缩第一段**：开头默认控制在 `80-110 words`，通常写 `3-5` 句，并以 `120 words` 为上限。第一段只负责建立任务压力，不再展开应用清单或提前介绍技术细节。
- **减少罗列式表达**：避免反复使用逗号三连和 `A, B, and C` 句型。每句话承担一个主要论证动作，多项信息优先改写为因果、转折或递进关系。
- **保留必要枚举**：方法分类、贡献列表和正式定义的独立变量仍可明确列举，避免为了反罗列而损失技术准确性。
- **调整整体篇幅**：Introduction 正文默认约 `580-680 words`，含贡献列表约 `650-780 words`，通常不超过 `850 words`。
- **加强完稿检查**：新增首段删减检查与 enumeration-overuse 检查，要求删除不影响第二段衔接的泛泛背景句。

## 适合场景

- 你已经写好了 Methods，但 Introduction 还没有思路。
- 你希望从方法部分反推出 research gap、study objective 和 contribution。
- 你的论文属于 AI、NLP、RAG、机器学习、算法、方法学或计算框架类工作。
- 你想写出三段正文加贡献列表的 Introduction，而不是松散的文献综述。

## 当前模块

### `introduce`

从 Methods 写 Introduction。

默认输出包括：

- `Inferred argument`：一句话概括论文核心论证。
- `Author-style contradiction`：提炼两个瓶颈或一个核心 trade-off。
- `Gap-module alignment`：把已有方法局限与本文方法模块对齐。
- `Paragraph blueprint`：三段式引言蓝图。
- `Word budget`：按作者习惯分配字数。
- `Draft Introduction`：正式英文 Introduction 草稿。
- `Contribution list`：2-4 条贡献，默认 3 条。
- `Assumptions or missing inputs`：缺失信息或推断假设。
- `Self-check`：检查过度声称、证据缺口和贡献闭环。

## 写作结构

默认采用：

1. **第一段：紧凑的任务合法性与复杂场景压力**
   用 `80-110 words` 定义任务，说明目标场景为什么更难，并引出核心需求。除非某个应用直接构成研究问题，否则不铺陈应用背景。

2. **第二段：已有方法进展、两类方法 taxonomy 与核心矛盾**  
   先肯定已有方法贡献，再把现有工作分成两类，分别指出它们的残留瓶颈，最后压缩成双瓶颈或一个 trade-off。

3. **第三段：本文方法、模块对位与验证引出贡献**  
   把本文方法作为一个 conceptual shift 提出，并说明每个方法模块如何回应前文的瓶颈。

4. **Contribution list**  
   每条贡献都要对应前文的 gap、方法模块或实验验证。

## 默认长度

- Introduction 正文：约 `580-680 words`
- 含贡献列表：约 `650-780 words`
- 正文结构：`3` 个大段 + contribution list
- 贡献列表：默认 `3` 条
- 第一段：约 `80-110 words`，默认不超过 `120 words`
- 默认不超过 `850 words`

如果 Methods 信息不足，skill 会写较短版本，并列出缺失信息，而不是硬凑字数。

## 安装方式

将仓库克隆到 Codex 的 skills 目录：

```bash
git clone https://github.com/xieyu-wlj/laoli-paper.git ~/.codex/skills/laoli-paper
```

Windows 用户也可以克隆到：

```text
C:\Users\<你的用户名>\.codex\skills\laoli-paper
```

安装后重新打开或刷新 Codex 会话，即可使用 `laoli-paper`。

## 使用示例

你可以这样请求：

```text
使用 laoli-paper 的 introduce 模块。
下面是我的 Methods，请根据它写 Introduction。
要求：三段正文 + contribution list，按双瓶颈/双模块对位的写法。
```

或者：

```text
用 laoli-paper 帮我从方法部分反推 Introduction。
```

## 目录结构

```text
laoli-paper/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── method-to-introduction.md
```

## 注意

这个 skill 会尽量从 Methods 中推断研究问题和方法贡献，但不会主动编造结果、实验提升、样本特征或引用。如果需要真实文献引用，应额外提供参考文献，或配合文献检索类 skill 使用。
