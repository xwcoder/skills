---
name: topic-diver
description: organize and deeply summarize any learning or research topic into a complete chinese markdown document. Use when the user wants to explore, brainstorm, map, grill, compare, or summarize a broad topic in any domain, including business, history, culture, science, productivity, product, management, or personal learning. Especially use when the user gives only a short topic and wants AI modelto expand the topic's full scope, ask targeted selection questions, and produce a structured markdown write-up rather than a simple outline or learning roadmap.
---

# Topic Diver

Use this skill to turn a short topic into a complete, structured Chinese Markdown summary. The goal is to help the user discover the full scope of a topic, decide which angles matter, and generate a coherent document that can be saved as a `.md` file.

Default output language: Simplified Chinese, unless the user asks otherwise.
Default final artifact: Markdown content suitable for saving as a `.md` file.

## Core behavior

When the user provides a topic, follow this workflow:

1. Clarify the topic frame
   - Restate the topic in precise terms.
   - Identify the domain and likely angles: historical, conceptual, practical, social, business, scientific, cultural, ethical, strategic, or personal.
   - If the topic is ambiguous, make a best-effort interpretation and state it briefly.

2. Build a topic coverage map
   - Expand the topic into major dimensions.
   - Include context, key concepts, stakeholders, history, frameworks, debates, examples, practical uses, risks, and open questions when relevant.
   - Avoid forcing technical sections onto non-technical topics.

3. Grill the user with targeted selection questions
   - Ask concise questions that help decide which angles deserve depth.
   - Offer selectable options instead of open-ended prompts.
   - Do not ask more than 6 questions at once.
   - If the user wants speed, skip questions and generate a reasonable default version.

4. Generate the Markdown summary
   - Produce a complete topic document, not merely a learning roadmap.
   - Include a learning path only as an optional section when useful.
   - Prioritize structure, explanation, comparison, examples, and judgment.
   - When a visual would materially improve understanding, include an appropriate diagram or image. The image may come from search or generation, and can be a panorama map, architecture diagram, timeline, sequence diagram, data-flow diagram, comparison matrix, or other topic-appropriate visual.

5. Offer follow-up expansion
   - Suggest one focused next step, such as expanding a section, adding examples, turning it into a checklist, or adapting it for a specific audience.

## Default general coverage map

Adapt this list to the topic. Do not force irrelevant sections.

- Topic overview: what it is, why it matters, and what questions it answers.
- Scope and boundaries: what is included and excluded.
- Background and evolution: history, milestones, changes in interpretation or practice.
- Core concepts: terms, categories, frameworks, models, and assumptions.
- Key actors or stakeholders: people, organizations, communities, customers, users, regulators, or systems.
- Main dimensions: social, economic, cultural, scientific, strategic, ethical, operational, or personal dimensions as relevant.
- Practical applications: how the topic appears in real life, work, policy, products, education, or decision-making.
- Examples and cases: representative cases that make the topic concrete.
- Comparisons: related concepts, alternatives, schools of thought, or competing approaches.
- Debates and controversies: disagreements, tradeoffs, risks, and unresolved issues.
- Common misconceptions: what people often get wrong.
- Frameworks for analysis: lenses or questions the user can use to reason about the topic.
- Optional learning path: suggested order to learn the topic.
- Further questions: high-quality follow-up questions.

## Markdown output template

Use this flexible structure for final summaries:

```markdown
# [Topic 名称]

## 0. 一句话概括
[用 2-4 句话说明这个 topic 是什么、为什么重要]

## 1. Topic 全景图
[用层级列表列出主要知识面]

## 2. 范围与边界
[说明本文讨论什么、不讨论什么]

## 3. 背景与演进
[历史、阶段、关键变化、为什么变化]

## 4. 核心概念
[术语、框架、分类、基本模型]

## 5. 主要维度
[按 topic 选择合适维度，例如经济、社会、文化、技术、组织、伦理等]

## 6. 代表性案例
[用案例让抽象内容具体化]

## 7. 对比与分析框架
[表格或结构化对比]

## 8. 常见误区
[列出容易误解的地方]

## 9. 现实应用 / 实践建议
[说明如何在真实场景中使用这套知识]

## 10. 争议、风险与开放问题
[不同观点、权衡、尚未解决的问题]

## 11. 可选学习路线
[如果用户确实需要学习路线，则给出学习顺序；否则保持简短]

## 12. 继续深入的问题
[列出 5-10 个高质量 follow-up questions]
```

## Selection-question pattern

When the topic is broad, ask questions like:

```markdown
我可以先把这个 topic 拆成完整 Markdown 总结。为了控制方向，请你选一下：

1. 你更关心哪种视角？
   A. 概念理解  B. 历史脉络  C. 实际应用  D. 争议与观点  E. 决策/行动建议

2. 你希望深度到哪里？
   A. 快速理解  B. 系统掌握  C. 能用于分析/决策  D. 能输出成文章/报告

3. 是否需要案例？
   A. 现实案例  B. 对比案例  C. 反例/失败案例  D. 不需要
```

If the user does not answer, proceed with balanced defaults: conceptual clarity + practical examples + common debates.

## Markdown file destination behavior

When the user wants the final summary written to a Markdown file:

1. If the user provides a target file path or filename, use that location directly.
2. If the user does not provide a target location, first generate or prepare the Markdown content, then ask where to write it: “要写入哪个 Markdown 文件？如果不需要写入，我也可以直接在聊天中输出。”
3. If the current environment cannot write to the requested location, do not fail silently. Instead, provide the complete Markdown content in chat or create a downloadable `.md` file when file creation is available.
4. Do not repeatedly ask for the file location when the user already provided it in the prompt or previous context.

Prefer this order: user-specified path → ask for missing path → fallback to copyable/downloadable Markdown.

## Quality rules

- Do not reduce the result to a simple study plan unless the user explicitly asks for one.
- Do not produce generic encyclopedia prose. Use structure, examples, and analysis.
- Explain why each major dimension matters.
- Prefer tables for comparison and bullet lists for maps, but use paragraphs for explanation.
- Use diagrams or images when they clarify structure, process, relationships, timelines, architecture, or flows better than text alone.
- For fast-changing or factual topics, verify current facts with web search when available or clearly mark uncertainty.
- Keep Chinese output natural, concise, and precise. Keep common English terms in parentheses when helpful.
