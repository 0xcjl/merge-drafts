---
name: merge-drafts
description: Intelligent draft merging tool with quality assessment and conflict resolution. Merges multiple drafts into a high-quality article, supporting multiple input formats, intelligent evaluation, conflict detection, highlight fusion, and multi-format output. Use when user says "合并稿子", "合稿", "merge drafts", "把这几篇合成一篇", "综合这几份稿子".
---

# Merge Drafts Skill v2.0

## Writing Style

This skill follows the writing standards defined in the `writing-style` skill. Maintains consistent overall article style with natural and fluent language.

## Input

Supports the following input methods:
- File paths: txt, md, docx, pdf
- URLs: online document links
- Direct pasted text
- Feishu document links

Also reads analysis.md (if present) in the same directory as reference material.

## Quality Assessment Criteria

Assessment dimensions for each draft:

| Dimension | Weight | Description |
|------|------|------|
| Structural clarity | 20% | Paragraph organization, logical flow |
| Information completeness | 25% | Topic coverage |
| Expression quality | 20% | Grammar, fluency |
| Unique highlights | 15% | Unique perspectives/data/cases |
| Topic relevance | 20% | Match with final goal |

## Workflow

### Step 1: Input Parsing
- Identify input format
- Unify to Markdown processing
- Extract title, body, comments

### Step 2: Independent Assessment
- Score each draft across 6 dimensions
- Extract core arguments from each
- Mark unique highlights (golden sentences, data, cases)
- Identify potential issues (logical gaps, ambiguous expressions)

### Step 3: Conflict Detection
- Find contradictory viewpoints/data
- Mark conflict points, prioritize content with citations
- Present undecidable cases to user for selection

### Step 4: Select Base Draft
Highest-scoring draft becomes base, criteria:
1. Clearest structure
2. Most complete information
3. Best expression
4. Lowest modification cost

### Step 5: Fusion Merge
Extract from each draft:
- Missing content → supplement to corresponding position in base draft
- Better expressions → replace original expressions in base draft
- Unique perspectives → integrate as new paragraphs
- Data and cases → cite and mark sources

**Fusion Principles:**
- Fuse rather than concatenate, as if written by one person
- Preserve core thread, allow reasonable redundancy
- Prioritize content with sources

### Step 6: Intelligent Polishing
- Check for stitching marks → natural transitions
- Unify style → adjust inconsistencies
- Remove duplicates → merge repeated paragraphs
- Logical coherence → check smooth transitions
- Typo check
- Readability score (optional)

### Step 7: Output
- Default output: Markdown
- Supports: Markdown, HTML, PDF, Feishu documents
- Also output merge report

## Output Format

### Merge Report
```
📊 Merge Report

📝 Base Draft: [filename] (Score: XX)
Reason: [selection reason]

📄 Draft Contributions:
- Draft 1: [contribution summary]
- Draft 2: [contribution summary]
- ...

✏️ Main Modifications:
- [modification 1]
- [modification 2]

📈 Quality Score: XX/100
```

### Article Output
- Maintain Markdown format
- Add footnotes for important citations
- Clear section heading hierarchy

## Error Handling

| Situation | Handling |
|------|----------|
| Completely unrelated topics | Notify user, process separately |
| Excessive word count difference | Warning, may not be suitable for merging |
| Unable to read format | Prompt supported formats, request conversion |
| Content conflicts | Mark conflict points, ask user to decide |

## Usage Example
```
User: Merge these 3 drafts about AI Agent
Me: [draft1.md, draft2.md, draft3.md] → Merge → Output merge report + article
```
