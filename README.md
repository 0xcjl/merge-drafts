# merge-drafts

[English](#english) | [中文](#中文)

---

## 中文

### 项目简介

多稿合并技能 - 一个智能将多份草稿合并为高质量文章的 AI 技能。基于 OpenClaw 平台运行，遵循专业的写作规范和质量评估标准。

### 核心功能

- **多格式支持**：支持 txt, md, docx, pdf, URL, 飞书文档链接等多种输入格式
- **智能评估**：从 5 个维度对每份稿件进行质量评估（结构清晰度、信息完整度、表达质量、独特亮点、主题契合度）
- **冲突检测**：智能识别并标记稿件间的观点冲突，提供解决方案
- **融合合并**：保留各稿亮点，融合为风格统一的高质量文章
- **智能润色**：消除拼接痕迹，统一风格，确保逻辑连贯
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
```

### 使用示例

```
用户：把这3篇关于AI Agent的稿子合并成一篇
AI：[稿1.md, 稿2.md, 稿3.md] → 合并 → 输出合并报告+文章
```

### 工作流程

1. **输入解析** - 识别格式，统一转为 Markdown
2. **独立评估** - 5维度打分，提取核心论点和亮点
3. **冲突检测** - 找出矛盾观点，标记冲突点
4. **选择基础稿** - 评分最高者为基础
5. **融合合并** - 提取各稿优点，融合到基础稿
6. **智能润色** - 消除拼接痕迹，统一风格
7. **输出** - 输出合并报告和最终文章

### 质量评估维度

| 维度 | 权重 | 说明 |
|------|------|------|
| 结构清晰度 | 20% | 段落组织、逻辑 flow |
| 信息完整度 | 25% | 覆盖主题程度 |
| 表达质量 | 20% | 语法、流畅度 |
| 独特亮点 | 15% | 独特视角/数据/案例 |
| 主题契合度 | 20% | 与最终目标匹配度 |

### 配置说明

本技能会自动读取同目录下的 `analysis.md`（如有）作为素材参考。

### 贡献指南

欢迎提交 Issue 和 Pull Request！

### License

MIT License

---

## English

### Overview

**merge-drafts** - An AI skill that intelligently merges multiple draft articles into a high-quality final piece. Built for OpenClaw platform, following professional writing standards and quality evaluation criteria.

### Features

- **Multi-format Support**: Supports txt, md, docx, pdf, URLs, Feishu document links, and more
- **Smart Evaluation**: Quality assessment across 5 dimensions (structure clarity, information completeness, expression quality, unique highlights, topic relevance)
- **Conflict Detection**: Intelligently identifies and marks conflicting viewpoints between drafts
- **Intelligent Merge**: Preserves highlights from each draft, merging into a unified, high-quality article
- **Smart Polishing**: Eliminates merge traces, unifies style, ensures logical coherence
- **Multi-format Output**: Supports Markdown, HTML, PDF, Feishu document formats

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
```

### Usage Example

```
User: Merge these 3 drafts about AI Agent into one article
AI: [draft1.md, draft2.md, draft3.md] → Merge → Output merge report + article
```

### Workflow

1. **Input Parsing** - Identify format, convert to Markdown
2. **Independent Evaluation** - 5-dimension scoring, extract core arguments and highlights
3. **Conflict Detection** - Find contradictory viewpoints, mark conflicts
4. **Base Draft Selection** - Highest scoring draft becomes the base
5. **Merge** - Extract advantages from each draft, merge into base
6. **Smart Polishing** - Eliminate merge traces, unify style
7. **Output** - Output merge report and final article

### Quality Evaluation Dimensions

| Dimension | Weight | Description |
|-----------|--------|-------------|
| Structure Clarity | 20% | Paragraph organization, logical flow |
| Information Completeness | 25% | Topic coverage |
| Expression Quality | 20% | Grammar, fluency |
| Unique Highlights | 15% | Unique perspective/data/cases |
| Topic Relevance | 20% | Match with final goal |

### Configuration

This skill automatically reads `analysis.md` in the same directory (if exists) as reference material.

### Contributing

Issues and Pull Requests are welcome!

### License

MIT License
