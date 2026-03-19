# Adaptive Learner

A universal AI skill that transforms any content into a structured, adaptive learning session.

Works with **any AI agent**: Claude Code, Codex, Gemini, OpenClaw, or any LLM that accepts system prompts.

## What It Does

Give it a topic, URL, PDF, or pasted text. It will:

1. **Analyze & decompose** the content into learning modules (no fixed limit on module count)
2. **Assess your level** per module (1-5 self-rating)
3. **Adapt teaching depth** based on your rating and chosen learning mode
4. **Teach each concept** using a proven triple structure:
   - **Concept** — what it is, why it matters, real-world example
   - **Anti-pattern** — common mistake, why it's tempting, correct approach
   - **Practice scenario** — realistic situation requiring your judgment
5. **Connect concepts** across modules to build a knowledge network
6. **Assess you** per module and comprehensively at the end
7. **Generate a hands-on exercise** combining multiple modules

## Why It Works

This skill is distilled from a set of exam-prep prompts that proved exceptionally effective. Analysis revealed 8 core pedagogical patterns:

| Pattern | What It Does |
|---|---|
| **Role anchoring** | AI adopts a domain-expert persona — direct, specific, grounded in production scenarios |
| **Adaptive depth** | Teaching depth adjusts per module based on student self-assessment |
| **Concept-Antipattern-Scenario triple** | Each concept is taught, then stress-tested with common mistakes and practice |
| **Cross-concept connections** | Explicitly links related ideas to build a knowledge network, not isolated facts |
| **Trap callouts** | Highlights common exam/interview/real-world pitfalls with specific explanations |
| **Built-in assessment loop** | Per-module quizzes + comprehensive final exam + gap analysis + remediation |
| **Hands-on exercise** | Practical capstone that synthesizes multiple modules |
| **Session state management** | Progress saves across sessions; resume from where you left off |

## Learning Modes

| Mode | Best For |
|---|---|
| **Deep Dive** | First-time learning, thorough preparation |
| **Quick Review** | Refreshing existing knowledge |
| **Targeted** | Known weak areas only |
| **Exam Prep** | Final push — heavy on traps and testing |

## Installation

### Claude Code

Copy `SKILL.md` to your skills directory:

```bash
# Personal (just you)
mkdir -p ~/.claude/skills/adaptive-learner
cp SKILL.md ~/.claude/skills/adaptive-learner/

# Project-level (shared with team)
mkdir -p .claude/skills/adaptive-learner
cp SKILL.md .claude/skills/adaptive-learner/
```

Then invoke with:
```
/adaptive-learner Kubernetes networking
/adaptive-learner https://docs.example.com/guide
/adaptive-learner ~/papers/attention-is-all-you-need.pdf
/adaptive-learner resume
```

### Other AI Agents (Codex, Gemini, OpenClaw, etc.)

Copy the contents of `SKILL.md` (everything after the YAML frontmatter `---`) into your agent's system prompt or custom instruction field. The skill uses no platform-specific syntax — it's pure Markdown instructions that any LLM can follow.

## In-Session Commands

| Command | Action |
|---|---|
| `module N` | Jump to module N |
| `skip` | Skip current concept or module |
| `deeper` | Go deeper on current topic |
| `faster` | Speed up, less detail |
| `pause` | Save progress, end session |
| `review` | Show progress overview |
| `assess` | Jump to module assessment |
| `map` | Show full learning map with progress |
| `connections` | Show cross-concept relationship map |
| `reset` | Reset current module, start over |

Natural language equivalents also work (e.g., "go deeper", "test me", "show the map").

## Examples

```
# Learn from a topic description
/adaptive-learner distributed systems consensus algorithms

# Learn from a document
/adaptive-learner ~/Downloads/system-design-primer.pdf

# Learn from a web page
/adaptive-learner https://kubernetes.io/docs/concepts/

# Resume a previous session
/adaptive-learner resume

# Jump to a specific module
/adaptive-learner module 3
```

## How It Teaches

For each concept, you get this cycle:

```
📖 Concept: [What it is + Why it matters + Real example]

❌ Common Mistake: [What people get wrong]
   Why it's tempting: [Why this mistake is appealing]
   ✅ Correct approach: [What to do instead]

🎯 Practice Scenario:
   [A realistic situation — what would you do?]
```

After every 2-3 concepts:
```
🔗 Connection: [How concept A relates to concept B in practice]
```

After each module:
```
📝 Module Assessment: [3-7 questions, 70% to pass]
```

## License

MIT

---

# Adaptive Learner (中文)

一个通用的 AI 学习辅助 skill，能将任何内容转化为结构化的自适应学习流程。

适用于**任何 AI agent**：Claude Code、Codex、Gemini、OpenClaw，或任何接受系统提示词的 LLM。

## 功能概述

输入一个主题、URL、PDF 或直接粘贴文本，它会：

1. **分析并拆分**内容为学习模块（模块数量不设限，由内容复杂度决定）
2. **评估你的水平**：每个模块自评 1-5 分
3. **自适应调整教学深度**：根据你的评分和学习模式动态调整
4. **用经过验证的三重结构教学**每个概念：
   - **概念讲解** — 是什么、为什么重要、真实场景
   - **反模式** — 常见错误、为什么有诱惑力、正确做法
   - **练习场景** — 需要你做判断的现实情境
5. **跨概念连接**：构建知识网络而非孤立知识点
6. **模块评估 + 综合评估**：内置测试、弱点分析、补救路径
7. **实操练习**：综合多模块知识的动手任务

## 为什么有效

这个 skill 从一套被验证极其有效的考试备考提示词中提炼而来。分析发现了 8 个核心教学模式：

| 模式 | 作用 |
|---|---|
| **角色锚定** | AI 自动切换为该领域的资深从业者——直接、具体、基于真实场景 |
| **自适应深度** | 根据学生自评分，每个模块使用不同的教学深度 |
| **概念-反模式-场景三重结构** | 每个概念都经历讲解、误区揭示和实践检验 |
| **跨概念连接** | 显式建立概念间关联，构建知识网络 |
| **陷阱标注** | 高亮考试/面试/实战中的常见坑点 |
| **内置评估循环** | 模块测试 + 综合考试 + 弱点分析 + 补救 |
| **实操练习** | 综合多模块知识的实践任务 |
| **会话状态管理** | 跨会话保存进度，支持断点恢复 |

## 学习模式

| 模式 | 适用场景 |
|---|---|
| **全面深入** | 首次学习、系统备考 |
| **快速复习** | 刷新已有知识 |
| **针对性学习** | 已知薄弱模块 |
| **考前冲刺** | 最后阶段——大量陷阱标注和高强度测试 |

## 安装

### Claude Code

将 `SKILL.md` 复制到 skills 目录：

```bash
# 个人使用
mkdir -p ~/.claude/skills/adaptive-learner
cp SKILL.md ~/.claude/skills/adaptive-learner/

# 项目级（团队共享）
mkdir -p .claude/skills/adaptive-learner
cp SKILL.md .claude/skills/adaptive-learner/
```

调用方式：
```
/adaptive-learner Kubernetes 网络模型
/adaptive-learner https://docs.example.com/guide
/adaptive-learner ~/papers/attention-is-all-you-need.pdf
/adaptive-learner resume
```

### 其他 AI Agent（Codex、Gemini、OpenClaw 等）

将 `SKILL.md` 中 YAML frontmatter（`---`）之后的全部内容复制到你的 agent 的系统提示词或自定义指令中。这个 skill 不使用任何平台特有语法——纯 Markdown 指令，任何 LLM 都能遵循。

## 会话内命令

| 命令 | 作用 |
|---|---|
| `模块 N` / `module N` | 跳转到模块 N |
| `skip` / `跳过` | 跳过当前概念或模块 |
| `deeper` / `展开` | 加深当前话题 |
| `faster` / `快一点` | 加速，减少细节 |
| `pause` / `暂停` | 保存进度，结束会话 |
| `review` / `回顾` | 显示进度总览 |
| `assess` / `测试` | 进入当前模块评估 |
| `map` / `地图` | 显示完整学习地图 |
| `connections` / `关联` | 显示跨概念关联图谱 |
| `reset` / `重来` | 重置当前模块 |

也支持自然语言表达（如"讲深一点"、"考考我"、"看看地图"）。

## 使用示例

```
# 从主题描述学习
/adaptive-learner 分布式系统共识算法

# 从文档学习
/adaptive-learner ~/Downloads/system-design-primer.pdf

# 从网页学习
/adaptive-learner https://kubernetes.io/docs/concepts/

# 恢复上次学习
/adaptive-learner resume

# 跳转到特定模块
/adaptive-learner 模块 3
```

## 教学流程示意

每个概念的教学循环：

```
📖 概念: [是什么 + 为什么重要 + 真实场景]

❌ 常见错误: [大多数人怎么做错的]
   为什么诱人: [为什么这个错误很吸引人]
   ✅ 正确做法: [应该怎么做]

🎯 场景练习:
   [一个现实情境——你会怎么做？]
```

每 2-3 个概念后：
```
🔗 关联: [概念 A 和概念 B 在实践中如何关联]
```

每个模块结束后：
```
📝 模块评估: [3-7 题，70% 通过]
```

## 许可

MIT
