# Learn-Anything

**A universal AI skill that transforms any content into a complete, adaptive learning system.**

Works with any AI agent: Claude Code, Codex, Gemini, OpenClaw, or any LLM that accepts system prompts.

---

## What It Does

Give it a topic, URL, PDF, or pasted text. It will:

1. **Build a knowledge base** — actively collects multiple high-quality sources, filters by authority/recency/originality, and optionally uploads to NotebookLM to minimize hallucination
2. **Map the intellectual landscape** — queries expert mental models, field-level debates, and generates diagnostic questions *before* teaching begins
3. **Generate a learning map** — modules with weight, difficulty, dependencies, and consensus/debate annotations
4. **Teach each module** using a proven triple structure:
   - **Concept** — what it is, why it matters, real-world scenario anchor
   - **Anti-pattern** — common mistake, why it's tempting, correct approach
   - **Practice scenario** — realistic situation requiring judgment
5. **Calibrate your level** — self-assessment + optional 3-minute quiz to verify actual depth
6. **Make It Easier on demand** — analogies, historical context, simplified versions, prerequisite mini-lessons, 5-year-old explanations
7. **Diagnose errors** — 3-step diagnosis on every wrong answer: what assumption was wrong, what key premise was missing, which type of misconception
8. **Track progress** — persistent progress files across sessions, resume from any breakpoint
9. **Run spaced repetition** — Ebbinghaus-curve review schedule (R1/R2/R3/R4) per module
10. **Award achievements** — milestone celebrations after each module, randomized badge on knowledge base completion

---

## Why It Works

| Pattern | What It Does |
|---|---|
| **Multi-source knowledge base** | 4 source types (authoritative / deep / multi-perspective / applied) with quality grading (A/B/C/D) before admission |
| **Expert lens first** | Before any teaching: maps expert mental models, field debates, and generates diagnostic questions |
| **Adaptive depth** | Teaching depth adjusts per module based on calibrated level, not just self-rating |
| **Anti-pattern teaching** | Each concept is taught, then stress-tested with the most tempting wrong approach |
| **Make It Easier mode** | 5 strategies (analogy / history / minimal version / prerequisite patch / 5yo) for breaking through difficulty walls |
| **3-step error diagnosis** | Wrong answers reveal: false assumption → missing premise → misconception type |
| **Spaced repetition** | 4-round review schedule baked into every module's completion |
| **Session persistence** | Full progress state saved; resume from exact breakpoint across sessions |
| **Achievement system** | Per-module milestones + 8 randomized completion badges with learning stats |

---

## Learning Modes

| Mode | Triggered by |
|---|---|
| **Full deep dive** | All modules in sequence, complete assessment loop |
| **Quick review** | `faster` command or time budget ≤ 20 min |
| **Targeted** | Specify module numbers at start |
| **Exam sprint** | Re-study after completion, focuses weak modules |
| **Make It Easier** | Any time — triggered by command or repeated wrong answers |

---

## Installation

### Claude Code

```bash
# Personal
mkdir -p ~/.claude/skills/learn-anything
cp SKILL.md ~/.claude/skills/learn-anything/

# Project-level (shared with team)
mkdir -p .claude/skills/learn-anything
cp SKILL.md .claude/skills/learn-anything/
```

Invoke with:
```
/learn-anything Kubernetes networking
/learn-anything https://docs.example.com/guide
/learn-anything ~/papers/attention-is-all-you-need.pdf
/learn-anything resume
```

### Other AI Agents (Codex, Gemini, etc.)

Copy the contents of `SKILL.md` (everything after the YAML frontmatter `---`) into your agent's system prompt or custom instruction field. The skill uses no platform-specific syntax — pure Markdown that any LLM can follow.

---

## Optional: NotebookLM Integration

NotebookLM is used as a low-hallucination knowledge base backend and for per-module audio generation.

**Setup:**
```bash
pip install notebooklm-mcp-cli
nlm login
```

**With NotebookLM:**
- Sources are uploaded to a persistent notebook
- Expert-lens queries run against verified source content
- Per-module audio generated with custom focus prompts
- One audio per module by default (not one generic overview)

**Without NotebookLM:** All text features work fully. Audio is disabled. The skill auto-detects and degrades gracefully.

---

## Optional: Enhanced Search

For better source collection during knowledge base construction, install [omni-search-skill](https://github.com/d-wwei/omni-search-skill). The skill will detect and use it automatically.

---

## In-Session Commands

| Command | Action |
|---|---|
| `更简单点` / `make it easier` | Activate Make It Easier mode |
| `skip` / `跳过` | Skip current concept or module |
| `deeper` / `展开` | Go deeper on current topic |
| `assess` / `测试我` | Jump to module assessment |
| `pause` / `暂停` | Save progress and end session |
| `map` / `进度` | Show learning map with progress |
| `复习计划` | View spaced repetition schedule |
| `导出笔记` | Export learning notes as Markdown |
| `切换音频` | Switch to audio mode (requires NotebookLM) |
| `connections` / `知识地图` | Show cross-concept relationship map |

Natural language equivalents work too (e.g., "go deeper", "I don't get this", "show my progress").

---

## Progress & Files

Progress is saved in `{SKILL_DIR}/progress/`:

```
progress/
  index.md              # Global index of all knowledge bases
  {kb-slug}.md          # Per-knowledge-base progress file
  {kb-slug}-notes.md    # Exported learning notes
```

Each progress file tracks: module status, self-rating vs actual score, calibration state, weak concepts, review schedule (R1–R4), study time, and session breakpoint.

---

## License

MIT

---
---

# Learn-Anything（中文）

**通用 AI 学习系统。将任何内容转化为结构化、自适应的完整学习体验。**

适用于任何 AI Agent：Claude Code、Codex、Gemini、OpenClaw，或任何接受系统提示词的 LLM。

---

## 功能概述

输入一个主题、URL、PDF 或粘贴文本，它会：

1. **构建知识库** — 主动采集多类高质量来源，按权威性/时效性/原创性分级过滤（A/B/C/D），可选上传到 NotebookLM 降低幻觉率
2. **建立领域智识地图** — 在开始教学**之前**，先查询专家心智模型、领域核心争议，并生成诊断性问题集
3. **生成学习地图** — 含权重、难度、前置依赖、共识/争议标注的模块化学习地图
4. **用三重结构教学**每个核心概念：
   - **概念讲解** — 是什么 + 为什么重要 + 真实场景锚定
   - **反模式** — 常见错误 + 为什么诱人 + 正确做法
   - **场景练习** — 需要你做判断的现实情境
5. **精准水平校准** — 用户自评 + 可选 3 分钟快速测验，以实际测验结果驱动教学深度
6. **Make It Easier 模式** — 类比 / 历史溯源 / 最小化版本 / 前置知识补课 / 5岁版解释，随时可触发
7. **三步错题诊断** — 每道错题：错误假设是什么 → 漏了什么关键前提 → 误区类型（概念混淆/前置缺口/场景判断）
8. **进度持久化** — 完整进度跨会话保存，随时从断点恢复
9. **间隔复习** — 基于艾宾浩斯曲线的 R1/R2/R3/R4 复习计划，内置于每个模块
10. **成就激励** — 每个模块完成后的里程碑庆祝 + 知识库完成时的随机勋章（含详细学习统计）

---

## 核心设计

| 机制 | 作用 |
|---|---|
| **多源知识库构建** | 4 类来源（权威基础/深度专业/多元视角/实践应用）+ 质量过滤，覆盖全面而非数量堆砌 |
| **专家视角优先** | 教学前先建立：专家心智模型 + 领域争议地图 + 诊断性问题集 |
| **自适应深度** | 教学深度由校准后的实际水平驱动，不完全依赖主观自评 |
| **反模式教学** | 每个概念：讲清楚什么是对的，也讲清楚什么是错的、为什么诱人 |
| **Make It Easier** | 5 种策略应对认知瓶颈，任何时候可触发 |
| **三步错题诊断** | 不只给答案，找到思维缺口的根源 |
| **间隔复习** | 每个模块完成后自动计算 4 轮复习时间，防止遗忘 |
| **进度持久化** | 全状态保存，跨会话断点续学 |
| **成就体系** | 里程碑数据 + 8 种随机勋章样式（含学习用时/正确率/自评准确度等） |

---

## 安装

### Claude Code

```bash
# 个人使用
mkdir -p ~/.claude/skills/learn-anything
cp SKILL.md ~/.claude/skills/learn-anything/

# 项目级（团队共享）
mkdir -p .claude/skills/learn-anything
cp SKILL.md .claude/skills/learn-anything/
```

调用方式：
```
/learn-anything 分布式系统共识算法
/learn-anything https://kubernetes.io/docs/concepts/
/learn-anything ~/papers/attention-is-all-you-need.pdf
/learn-anything resume
```

### 其他 AI Agent（Codex、Gemini 等）

将 `SKILL.md` 中 YAML frontmatter（`---`）之后的全部内容复制到你的 agent 的系统提示词中。本 skill 不使用任何平台特有语法，纯 Markdown 指令，任何 LLM 均可遵循。

---

## 可选：NotebookLM 集成

NotebookLM 作为低幻觉率的知识库后端，并支持按模块生成音频。

**配置方法：**
```bash
pip install notebooklm-mcp-cli
nlm login
```

**启用后：**
- 源材料上传到持久化 notebook，AI 基于真实内容作答
- 领域智识地图查询在 notebook 上执行，幻觉率更低
- 按模块生成定向音频（每个模块一个，含专属 focus_prompt）
- 默认不生成整合音频，除非用户明确要求

**未配置时：** 所有文字功能完全正常使用，音频功能自动禁用，无报错。

---

## 可选：增强搜索

知识库构建阶段的多源采集，可通过安装 [omni-search-skill](https://github.com/d-wwei/omni-search-skill) 增强。Skill 会自动检测并使用。

---

## 会话内命令

| 命令 | 动作 |
|---|---|
| `更简单点` / `make it easier` | 触发 Make It Easier 模式 |
| `跳过` / `skip` | 跳过当前概念或模块 |
| `展开` / `deeper` | 当前概念深入讲解 |
| `测试我` / `assess` | 立即进入当前模块测评 |
| `暂停` / `pause` | 保存进度，结束本次 session |
| `进度` / `map` | 显示整体学习进度 |
| `复习计划` | 查看复习队列和到期时间 |
| `导出笔记` | 导出学习笔记为 Markdown |
| `切换音频` | 切换到音频模式（需 NotebookLM）|
| `知识地图` / `connections` | 显示已学概念关联图谱 |

自然语言等效表达均可识别（如「讲深一点」「我听不懂」「给我看看进度」）。

---

## 进度文件

进度保存在 `{SKILL_DIR}/progress/`：

```
progress/
  index.md              # 全局知识库索引
  {kb-slug}.md          # 每个知识库的进度文件（含模块状态/得分/复习计划/断点）
  {kb-slug}-notes.md    # 导出的学习笔记
```

---

## 许可

MIT
