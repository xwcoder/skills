---
name: tech-topic-diver
description: organize and deeply summarize technical learning topics into a complete chinese markdown document. Use when the user wants to learn, explore, brainstorm, drill into, map, compare, or summarize a technical topic such as programming languages, frameworks, infrastructure, databases, AI/ML, security, developer tools, package management, architecture, or engineering practices. Especially use when the user gives only a short topic and wants AI model to expand the topic's full scope, ask targeted questions, let them choose depth, and produce a structured markdown write-up rather than a simple study plan.
---

# Tech Topic Diver

Use this skill to turn a short technical learning topic into a complete, structured Chinese Markdown summary. The goal is not merely to create a learning roadmap. The goal is to help the user discover the full scope of the topic, choose what matters, and then generate a well-organized technical document.

Default output language: Simplified Chinese, unless the user asks otherwise.
Default final artifact: Markdown content suitable for saving as a `.md` file.

## Core behavior

When the user provides a technical topic, follow this workflow:

1. Normalize the topic
   - Restate the topic in precise technical terms.
   - Identify likely subdomains, e.g. language feature, tool ecosystem, infrastructure, architecture pattern, protocol, library, or workflow.
   - If the topic is ambiguous, make a best-effort interpretation and state it briefly.

2. Build a topic coverage map
   - Expand the topic into major dimensions.
   - Prefer technical depth over generic encyclopedia coverage.
   - Include history, concepts, internals, ecosystem, tools, workflows, tradeoffs, production practices, common pitfalls, and current best practices when relevant.

3. Grill the user with targeted selection questions
   - Ask concise questions that help decide which areas deserve depth.
   - Offer selectable options instead of open-ended prompts.
   - Do not ask more than 6 questions at once.
   - If the user wants speed, skip questions and generate a reasonable default version.

4. Generate the Markdown summary
   - Produce a complete technical document, not just a study plan.
   - Include a learning path only as an optional section when useful.
   - Prioritize explanation, comparison, examples, and practical judgment.

5. Offer follow-up expansion
   - Suggest one focused next step, such as expanding a section, adding diagrams, adding examples, or converting to a study checklist.

## Default technical coverage map

Adapt this list to the topic. Do not force irrelevant sections.

- Topic overview: what it is, what problems it solves, and where it fits.
- Historical evolution: important milestones, why older approaches changed, and current direction.
- Core concepts and terminology: define terms precisely.
- Mental model: explain how to think about the topic.
- Architecture or internals: components, data flow, algorithms, protocols, dependency graph, lifecycle, or runtime model.
- Tool ecosystem: major tools, libraries, platforms, standards, and file formats.
- Practical workflows: how engineers use it in real projects.
- Environment and configuration: setup, isolation, versioning, compatibility, and reproducibility.
- Tradeoffs and decision criteria: when to choose which approach or tool.
- Common pitfalls: failure modes, confusing concepts, migration issues, security or operational risks.
- Best practices: modern recommendations and production-grade habits.
- Examples: commands, snippets, pseudo-code, config files, or mini case studies where relevant.
- Comparison tables: compare tools, concepts, approaches, or versions.
- Learning path: optional order for learning the topic after the summary.
- Further questions: advanced topics the user can ask next.

## Markdown output template

Use this flexible structure for final summaries:

```markdown
# [技术 Topic 名称]

## 0. 一句话概括
[用 2-4 句话说明这个 topic 是什么、解决什么问题、为什么重要]

## 1. Topic 全景图
[用层级列表列出这个 topic 覆盖的主要知识面]

## 2. 背景与演进
[解释历史、旧方案的问题、新方案为什么出现]

## 3. 核心概念
[术语、概念、关键对象、关系]

## 4. 工作原理 / 内部机制
[解释机制、流程、架构、生命周期；不适用时改成“核心机制”]

## 5. 主流工具 / 生态
[列出工具、标准、文件格式、平台，并解释定位]

## 6. 实际使用流程
[从真实工程场景出发说明怎么用]

## 7. 对比与选型
[表格对比不同工具/方案/模式]

## 8. 常见坑与误区
[列出新手和工程实践中容易踩的坑]

## 9. 最佳实践
[给出明确、可执行的建议]

## 10. 示例
[命令、代码、配置、案例；按 topic 适配]

## 11. 可选学习路线
[如果用户确实要学习路线，则给出学习顺序；否则保持简短]

## 12. 继续深入的问题
[列出 5-10 个高质量 follow-up questions]
```

## Selection-question pattern

When the topic is broad, ask questions like:

```markdown
我可以先把这个 topic 拆成完整 Markdown 总结。为了控制深度，请你选一下：

1. 你更关心哪种视角？
   A. 原理机制  B. 工程实践  C. 工具对比  D. 新手入门  E. 面试/知识体系

2. 你希望深度到哪里？
   A. 快速理解  B. 能实际使用  C. 能做技术选型  D. 能解释内部原理

3. 是否需要示例？
   A. 命令行/配置  B. 代码片段  C. 项目案例  D. 不需要
```

If the user does not answer, proceed with balanced defaults: engineering practice + conceptual clarity + practical examples.

## Markdown file destination behavior

When the user wants the final summary written to a Markdown file:

1. If the user provides a target file path or filename, use that location directly.
2. If the user does not provide a target location, first generate or prepare the Markdown content, then ask where to write it: “要写入哪个 Markdown 文件？如果不需要写入，我也可以直接在聊天中输出。”
3. If the current environment cannot write to the requested location, do not fail silently. Instead, provide the complete Markdown content in chat or create a downloadable `.md` file when file creation is available.
4. Do not repeatedly ask for the file location when the user already provided it in the prompt or previous context.

Prefer this order: user-specified path → ask for missing path → fallback to copyable/downloadable Markdown.

## Quality rules

- Do not produce generic motivational learning advice unless requested.
- Do not over-focus on chronology; explain why changes happened.
- Do not list tools without explaining their role, strengths, and tradeoffs.
- Avoid shallow summaries. Each major section should answer “why this matters” and “how it is used”.
- For fast-changing topics, verify current facts with web search when available or clearly mark uncertainty.
- When generating Markdown, use clean headings, concise paragraphs, tables where useful, and code blocks for commands/config.
- Keep Chinese output natural, technical, and precise. Keep common English technical terms in parentheses when helpful.
