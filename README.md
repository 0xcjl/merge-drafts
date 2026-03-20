# merge-drafts

[English](#english) | [中文](#中文)

---

## 中文

### 项目简介

多稿合并技能 - 一个智能将多份草稿合并为高质量文章的 AI 技能。基于 OpenClaw 平台运行，遵循专业的写作规范和质量评估标准。

> **优化历史**：本技能经过 `autoresearch-pro` 30 轮迭代优化，错误场景从 4 种扩展至 13 种，新增 10 条约束规则，工作流步骤全部打通。

### 核心功能

- **多格式支持**：支持 txt, md, docx, pdf, URL, 飞书文档链接等多种输入格式（含优先级排序）
- **智能评估**：从 5 个维度对每份稿件进行质量评估，支持评分等级计算（90-100优秀 / 70-89良好 / 50-69一般 / <50较差）
- **冲突检测**：智能识别并标记稿件间的观点冲突，优先保留有权威来源的数据
- **融合合并**：融合而非拼接，像一个人写的；保留各稿亮点，严格禁止直接删除
- **智能润色**：消除拼接痕迹，统一风格，确保逻辑连贯；最小必要润色边界明确
- **多格式输出**：支持 Markdown、HTML、PDF、飞书文档格式输出

### 使用场景

- 多人协作的文章整合
- 多版本文档的合并整理
- 多来源素材的融合写作
- 会议纪要的多角度整合

### 安装方法

```bash
# 使用 OpenClaw CLI 安装
openclaw skill install merge-drafts

# 或通过 ClawHub 安装
clawhub install merge-drafts

# 或手动克隆
git clone https://github.com/0xcjl/merge-drafts.git ~/.openclaw/skills/merge-drafts
```

### 使用示例

```
用户：把这3篇关于AI Agent的稿子合并成一篇
AI：[稿1.md, 稿2.md, 稿3.md] → 合并 → 输出合并报告+文章
```

### 工作流程（步骤七闭环）

```
输入解析 → 独立评估 → 冲突检测 → 选择基础稿 → 融合合并 → 智能润色 → 输出
```

1. **输入解析** - 识别格式，统一转为 Markdown，支持飞书文档
2. **独立评估** - 5维度打分，提取核心论点和亮点，评分结果决定后续步骤
3. **冲突检测** - 找出矛盾观点/数据，优先保留有引用来源的，无法判断时呈现用户选择
4. **选择基础稿** - 评分最高者为基础（评分最高 > 结构最清晰 > 信息最完整 > 表达最好）
5. **融合合并** - 提取各稿优点，融合到基础稿；**禁止**直接拼接，**禁止**自行删除亮点
6. **智能润色** - 消除拼接痕迹，统一风格；最小必要润色：仅修正语法/错别字/过渡，**禁止**重写表达
7. **输出** - 输出合并报告（必须）和最终文章

### 写作风格原则

融合时遵循以下原则：
- **语气一致**：以基础稿为准，通过过渡句调节全文基调
- **保留独特表达**：有生命力的词句或精准术语应保留，而非统一成平淡表达
- **术语统一**：同一概念不同表述时，优先保留基础稿用语，其余作脚注
- **行文节奏**：避免堆砌短句，注意段落内部的长短句搭配

### 质量评估标准

| 维度 | 权重 | 说明 |
|------|------|------|
| 结构清晰度 | 20% | 段落组织、逻辑 flow |
| 信息完整度 | 25% | 覆盖主题程度 |
| 表达质量 | 20% | 语法、流畅度 |
| 独特亮点 | 15% | 独特视角/数据/案例 |
| 主题契合度 | 20% | 与最终目标匹配度 |

**评分等级：** 90-100优秀 / 70-89良好 / 50-69一般 / <50较差

### 约束规则（10条）

| # | 规则 |
|---|------|
| 1 | **必须**在融合前完成冲突检测 |
| 2 | **必须**以评分最高稿为基础稿 |
| 3 | **禁止**直接拼接，必须进行语义融合 |
| 4 | **禁止**未告知用户丢弃任何稿件全部内容 |
| 5 | **必须**输出合并报告 |
| 6 | **必须**说明各稿贡献 |
| 7 | **禁止**修改原文，只能最小必要润色 |
| 8 | **必须**按质量评估标准权重计算评分 |
| 9 | **必须**对所有稿件采用统一的评分标准 |
| 10 | **禁止**仅凭主观偏好提升某稿评分 |

### 错误处理（13种场景）

| 情况 | 处理方式 |
|------|----------|
| 主题完全不相关 | 提示用户，分开处理 |
| 字数差异过大（>5倍） | 警告，说明风险，由用户确认是否继续 |
| 无法读取格式 | 提示支持格式列表 |
| 内容冲突 | 标记冲突点，请用户决定，**禁止**自行选择 |
| 稿子只有1份 | 提示至少需要2份，退出流程 |
| 稿子全部为空 | 提示检查文件路径或内容，退出流程 |
| 飞书文档无权限 | 提示确认分享权限 |
| 输出格式不支持 | 回退到默认Markdown |
| 某稿评估得分极低（<30） | 在报告中单独标注 |
| 融合后字数过长（>2万字） | 提示可分篇输出 |
| 多份稿子标题完全相同 | 保留基础稿标题 |
| 冲突过多（>5个） | 汇总一次性请用户确认，**禁止**自行处理超过5个冲突 |
| 润色后出现病句 | 标记"待确认"，保留原文和润色版供用户选择 |

### 配置说明

本技能会自动读取同目录下的 `analysis.md`（如有）作为素材参考。
飞书文档**必须**开启"任何人可查看"分享权限。

### 致谢

本技能优化方法论源自 [Karpathy/autoresearch](https://github.com/karpathy/autoresearch)，使用 [autoresearch-pro](https://github.com/0xcjl/openclaw-autoresearch-pro) 进行 30 轮迭代优化。

### License

MIT License

---

## English

### Overview

**merge-drafts** - An AI skill that intelligently merges multiple draft articles into a high-quality final piece. Built for OpenClaw platform, following professional writing standards and quality evaluation criteria.

> **Optimization history**: This skill was optimized via `autoresearch-pro` for 30 rounds. Error handling expanded from 4 to 13 scenarios, 10 constraint rules added, workflow steps fully cross-referenced.

### Features

- **Multi-format Support**: txt, md, docx, pdf, URLs, Feishu document links with priority ranking
- **Smart Evaluation**: 5-dimension quality assessment with tiered scoring (90-100 excellent / 70-89 good / 50-69 fair / <50 poor)
- **Conflict Detection**: Identifies conflicting viewpoints/data, prefers sourced data, escalates unresolved conflicts to user
- **Intelligent Merge**: Semantic fusion (not stitching); preserves highlights, strictly prohibits deletion without notice
- **Smart Polishing**: Eliminates merge traces, unifies style; minimum-necessary edits only
- **Multi-format Output**: Markdown, HTML, PDF, Feishu document

### Use Cases

- Article integration from multi-author collaboration
- Document version consolidation
- Multi-source content fusion
- Meeting minutes from different perspectives

### Installation

```bash
# Install via OpenClaw CLI
openclaw skill install merge-drafts

# Or via ClawHub
clawhub install merge-drafts

# Or manually
git clone https://github.com/0xcjl/merge-drafts.git ~/.openclaw/skills/merge-drafts
```

### Usage Example

```
User: Merge these 3 drafts about AI Agent into one article
AI: [draft1.md, draft2.md, draft3.md] → Merge → Output merge report + article
```

### Workflow (7-step closed loop)

```
Input Parsing → Independent Evaluation → Conflict Detection → Base Draft Selection → Merge → Polish → Output
```

1. **Input Parsing** - Identify format, convert to Markdown, Feishu supported
2. **Independent Evaluation** - 5-dimension scoring, extract core arguments, results inform subsequent steps
3. **Conflict Detection** - Find contradictory viewpoints/data, prefer sourced data, escalate to user if unresolved
4. **Base Draft Selection** - Highest scoring draft becomes base (score > structure > info completeness > expression quality)
5. **Merge** - Extract advantages from each draft, fuse into base; **never** stitch without fusion, **never** delete highlights without notice
6. **Smart Polishing** - Eliminate traces, unify style; minimum-necessary edits: grammar/typo/transitions only, **never** rewrite expressions
7. **Output** - Merge report (mandatory) + final article

### Writing Style Principles

When merging, follow these principles:
- **Tone consistency**: Base draft sets the tone, use transitions to modulate
- **Preserve unique expression**: Vivid phrases or precise terminology should be preserved, not flattened
- **Terminology consistency**: Prefer base draft's terms for the same concept, add footnotes for alternatives
- **Rhythm**: Avoid sentence fragmentation, vary paragraph length

### Quality Evaluation

| Dimension | Weight | Description |
|-----------|--------|-------------|
| Structure Clarity | 20% | Paragraph organization, logical flow |
| Information Completeness | 25% | Topic coverage |
| Expression Quality | 20% | Grammar, fluency |
| Unique Highlights | 15% | Unique perspective/data/cases |
| Topic Relevance | 20% | Match with final goal |

**Tiers:** 90-100 excellent / 70-89 good / 50-69 fair / <50 poor

### Constraint Rules (10 mandatory)

| # | Rule |
|---|------|
| 1 | **Must** complete conflict detection before merging |
| 2 | **Must** use the highest-scoring draft as the base |
| 3 | **Never** stitch — must semantic merge |
| 4 | **Never** discard any draft's content without informing user |
| 5 | **Must** output a merge report |
| 6 | **Must** explain each draft's contribution |
| 7 | **Never** modify original text — minimum-necessary edits only |
| 8 | **Must** calculate scores using quality evaluation weights |
| 9 | **Must** use uniform scoring standards across all drafts |
| 10 | **Never** boost scores based on subjective preference |

### Error Handling (13 scenarios)

| Scenario | Handling |
|---------|----------|
| Topics completely unrelated | Notify user, handle separately |
| Word count disparity (>5x) | Warn with risk explanation, get user confirmation |
| Unsupported format | Show supported format list |
| Content conflict | Mark conflicts, let user decide, **never** decide silently |
| Only 1 draft provided | Request at least 2 drafts, exit |
| All drafts empty | Request user check file paths/content, exit |
| Feishu doc no permission | Request sharing permission check |
| Unsupported output format | Fall back to default Markdown |
| Draft scores very low (<30) | Mark separately in report |
| Merged content >20k words | Suggest split output |
| Multiple drafts with identical titles | Keep base draft's title |
| Too many conflicts (>5) | Batch-confirm with user, **never** resolve >5 silently |
| Polishing produces broken sentence | Mark "pending review", keep both original and polished |

### Configuration

This skill reads `analysis.md` in the same directory (if exists) as reference.
Feishu documents **must** have "Anyone can view" sharing enabled.

### Credits

Methodology inspired by [Karpathy/autoresearch](https://github.com/karpathy/autoresearch), optimized via [autoresearch-pro](https://github.com/0xcjl/openclaw-autoresearch-pro) for 30 rounds.

### License

MIT License
