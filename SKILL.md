---
name: merge-drafts
description: Intelligent draft merging tool with quality assessment and conflict resolution. Merges multiple drafts into a high-quality article, supporting multiple input formats, intelligent evaluation, conflict detection, highlight fusion, and multi-format output. Use when user says "合并稿子", "合稿", "merge drafts", "把这几篇合成一篇", "综合这几份稿子".
---

# Merge Drafts Skill v2.0 / 多稿合并技能 v2.0

## Writing Style / 写作风格

This skill follows the writing standards defined in the `writing-style` skill. Maintains consistent overall article style with natural and fluent language.

本技能遵循 `writing-style` 技能定义的写作规范。保持文章整体风格统一，语言自然流畅。

## Input / 输入

Supports the following input methods / 支持以下输入方式：
- File paths: txt, md, docx, pdf / 文件路径：txt, md, docx, pdf
- URLs: online document links / URL：在线文档链接
- Direct pasted text / 直接粘贴的文本
- Feishu document links / 飞书文档链接

Also reads analysis.md (if present) in the same directory as reference material.

同时读取同目录下的 analysis.md（如有）作为素材参考。

## Quality Assessment Criteria / 质量评估标准

Assessment dimensions for each draft / 每份稿子评估维度：

| Dimension / 维度 | Weight / 权重 | Description / 说明 |
|------|------|------|
| Structural clarity / 结构清晰度 | 20% | Paragraph organization, logical flow / 段落组织、逻辑 flow |
| Information completeness / 信息完整度 | 25% | Topic coverage / 覆盖主题程度 |
| Expression quality / 表达质量 | 20% | Grammar, fluency / 语法、流畅度 |
| Unique highlights / 独特亮点 | 15% | Unique perspectives/data/cases / 独特视角/数据/案例 |
| Topic relevance / 主题契合度 | 20% | Match with final goal / 与最终目标匹配度 |

## Workflow / 工作流程

### Step 1: Input Parsing / 步骤一：输入解析
- Identify input format / 识别输入格式
- Unify to Markdown processing / 统一转为 Markdown 处理
- Extract title, body, comments / 提取标题、正文、注释

### Step 2: Independent Assessment / 步骤二：独立评估
- Score each draft across 6 dimensions / 对每份稿子按6个维度打分
- Extract core arguments from each / 提取每份的核心论点
- Mark unique highlights (golden sentences, data, cases) / 标记独特亮点（金句、数据、案例）
- Identify potential issues (logical gaps, ambiguous expressions) / 识别潜在问题（逻辑漏洞、表达歧义）

### Step 3: Conflict Detection / 步骤三：冲突检测
- Find contradictory viewpoints/data / 找出矛盾的观点/数据
- Mark conflict points, prioritize content with citations / 标记冲突点，优先保留有引用来源的
- Present undecidable cases to user for selection / 无法判断的呈现给用户选择

### Step 4: Select Base Draft / 步骤四：选择基础稿
Highest-scoring draft becomes base, criteria / 评分最高者为基础稿，标准：
1. Clearest structure / 结构最清晰
2. Most complete information / 信息最完整
3. Best expression / 表达最好
4. Lowest modification cost / 改动成本最低

### Step 5: Fusion Merge / 步骤五：融合合并
Extract from each draft / 从每份稿子提取：
- Missing content → supplement to corresponding position in base draft / 缺失内容 → 补充到基础稿对应位置
- Better expressions → replace original expressions in base draft / 更好表达 → 替换基础稿原有表达
- Unique perspectives → integrate as new paragraphs / 独特视角 → 融入作为新段落
- Data and cases → cite and mark sources / 数据案例 → 引用并标注来源

**Fusion Principles / 融合原则：**
- Fuse rather than concatenate, as if written by one person / 融合而非拼接，像一个人写的
- Preserve core thread, allow reasonable redundancy / 保留核心主线，允许合理冗余
- Prioritize content with sources / 优先使用有出处的内容

### Step 6: Intelligent Polishing / 步骤六：智能润色
- Check for stitching marks → natural transitions / 检查拼接痕迹 → 过渡自然
- Unify style → adjust inconsistencies / 风格统一 → 调整不一致处
- Remove duplicates → merge repeated paragraphs / 删除重复 → 合并重复段落
- Logical coherence → check smooth transitions / 逻辑连贯 → 检查跳转流畅度
- Typo check / 错别字检查
- Readability score (optional) / 可读性评分（可选）

### Step 7: Output / 步骤七：输出
- Default output: Markdown / 默认输出 Markdown
- Supports: Markdown, HTML, PDF, Feishu documents / 支持：Markdown, HTML, PDF, 飞书文档
- Also output merge report / 同时输出合并报告

## Output Format / 输出格式

### Merge Report / 合并报告
```
📊 Merge Report / 合并报告

📝 Base Draft / 基础稿：[filename] (Score / 评分: XX)
Reason / 原因：[selection reason / 选择理由]

📄 Draft Contributions / 稿件贡献：
- Draft 1 / 稿1: [contribution summary / 贡献内容概述]
- Draft 2 / 稿2: [contribution summary / 贡献内容概述]
- ...

✏️ Main Modifications / 主要修改：
- [modification 1 / 修改点1]
- [modification 2 / 修改点2]

📈 Quality Score / 质量评分：XX/100
```

### Article Output / 文章输出
- Maintain Markdown format / 保持 Markdown 格式
- Add footnotes for important citations / 重要引用添加脚注
- Clear section heading hierarchy / 章节标题层级清晰

## Error Handling / 错误处理

| Situation / 情况 | Handling / 处理方式 |
|------|----------|
| Completely unrelated topics / 主题完全不相关 | Notify user, process separately / 提示用户，分开处理 |
| Excessive word count difference / 字数差异过大 | Warning, may not be suitable for merging / 警告，可能不适合合并 |
| Unable to read format / 无法读取格式 | Prompt supported formats, request conversion / 提示支持格式，请转换 |
| Content conflicts / 内容冲突 | Mark conflict points, ask user to decide / 标记冲突点，请用户决定 |

## Usage Example / 使用示例

```
User / 用户：Merge these 3 drafts about AI Agent / 把这3篇关于AI Agent的稿子合并成一篇
Me / 我：[draft1.md, draft2.md, draft3.md] → Merge / 合并 → Output merge report + article / 输出合并报告+文章
```
