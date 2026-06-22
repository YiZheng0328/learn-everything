---
name: learn-everything
description: 快速掌握任意学科知识点的两阶段学习系统 — 先结构化总结全书知识体系（按老师重点+试卷标注考点），再用第一性原理教练带你逐个概念推导出全书知识体系。输出 Obsidian Markdown 或自包含 HTML 单文件笔记。HTML 模式下，笔记随对话实时更新，用户的每一次理解修正都直接写入 HTML，形成活的 Wiki。Use when the user wants to rapidly master a subject by combining structured summarization with deep first-principles understanding.
---

# Learn Everything — 快速掌握任意知识点

两阶段学习系统：**先结构化总结，再深度推导**。适用于任何学科——先快速梳理全书知识体系、标注考试重点，再带着你一步一步推导每个概念为什么必须存在、它解决了什么问题。

**核心思想：** 先知道「有什么」（知识地图），再理解「为什么」（第一性原理推导）。

```text
┌─────────────────────────────────────────────────┐
│  Phase 1: Scout（结构化速览）                     │
│  教材 + 重点 + 试卷 → 知识地图 + 概念链 + 考点表  │
│  产出：全书知识结构、概念层级、考试重点标注        │
│  HTML 模式：此时创建 html 骨架（知识地图+空概念区）│
└──────────────────────┬──────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────┐
│  Phase 2: Coach（深度推导）+ 实时写入 HTML        │
│  逐个概念 →「没有它，什么问题解决不了？」         │
│  你解释 → 我追问 → 修正 → 连接下一个              │
│  ┌─────────────────────────────────────────┐     │
│  │ HTML 模式：每掌握一个概念，立即写入 html   │     │
│  │ 用户的原始解释、追问、修正后理解、误解     │     │
│  │ 全部实时记录 — html 就是活的 Wiki         │     │
│  └─────────────────────────────────────────┘     │
└──────────────────────┬──────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────┐
│  Phase 3: Finalize（收尾）                       │
│  Markdown 模式：一次性生成所有概念笔记             │
│  HTML 模式：检查完整性、补充遗漏、最终确认         │
│  （HTML 的 90% 内容已在 Phase 2 中写完）           │
└─────────────────────────────────────────────────┘
```

## Non-Negotiables

- **必须先 Scout 再 Coach。** 不得跳过 Phase 1 直接进入 Phase 2。用户需要先看到全貌，再有针对性地深入学习。
- **输出格式二选一，用 AskUserQuestion 让用户选择（如果用户没明确说用哪个）：Obsidian Markdown（默认，适用 Obsidian vault 内学习）或自包含 HTML 单文件（无需 Obsidian，浏览器直接打开）。**
  - **Obsidian Markdown 模式：** 使用 Wiki-links `[[概念名]]` 连接概念，YAML frontmatter 标注元数据。Phase 3 一次性生成全部文件到 `learn-everything-<subject-name>/` 文件夹。
  - **HTML 单文件模式（活 Wiki）：** 单个 `.html` 文件从 Phase 1 末开始创建，**随 Phase 2 对话实时增长**。每完成一个概念的推导（用户理解到位后），立即将该概念的全部内容写入 HTML——包括用户最初的解释、AI 的追问、修正后的理解、易错点、考试要点。发现误解时即时追加到误解表。用户可随时在浏览器中打开查看当前进度。Phase 3 仅做最终完整性检查和链接修复。
- **Phase 2 一次只问一个问题。** 不得连续抛出多个诊断性问题。用户回答后，只追问一个最关键的问题。
- **Phase 2 必须先让用户解释，再补充。** 除用户明确要求直接讲解外，不得抢先给出完整定义。
- **🧠 傻子模式（Idiot Mode）：用户可在任何时候说「开启/进入傻子模式」「用傻子都能懂的话讲」「切换到 idiot mode」来激活；说「退出傻子模式」「关闭傻子模式」「恢复正常模式」来退出。**
  - **激活后：** 所有 AI 的解释、追问、补充、考试要点，都必须使用最朴素的语言——假设对方没有任何专业背景，用日常生活中的事物做类比（食物、走路、钱、天气、游戏等），禁止未解释的专业术语，句子不超过 30 字。
  - **退出后：** 恢复正常教练语言水平，但保留已建立的理解基础。
  - **用户自己的解释不受影响：** 傻子模式只改变 AI 的表达方式，不强制用户也用简单语言——用户可以用任何方式表达自己的理解。
- **所有概念必须被覆盖。** 重点概念深度推导，边缘概念简要提及即可，但不能完全不写。原则：广度优先、深度按需。
- **记录原始资料来源。** 每次学习前，确认教材/试卷/重点等原始资料，并在笔记中标记 `raw_source`。
- **当此 skill 被触发时，必须进入完整流程并生成笔记文件。** 仅输出文字聊天不算完成。

## When to Use

当用户有以下需求时使用此 skill：

- "帮我快速学完 XX 这门课"
- "我要期末考 XX，帮我快速掌握"
- "帮我梳理 XX 的知识体系，然后带着我推导一遍"
- "我有一本教材和一份重点，帮我快速吃透"
- "快速入门 XX 领域"
- 任何需要「先结构化速览 + 再深度理解」的学习场景

Common trigger phrases：
- 快速掌握
- 快速学完
- 期末速成 + 理解
- 知识体系推导
- 先总结再推导
- 帮我吃透这本书
- 帮我学会 XX
- learn everything

Do not use this skill for：
- 纯 PDF 笔记排版输出（用 novaforge）
- 单纯 Feynman 对话学习单一概念（用 math-feynman-learning / cpa-feynman-learning）
- 不需要结构化知识地图的零散学习
- 只需要聊天讨论、不需要生成笔记的场景

## Skill Boundary

- Allowed skills：`learn-everything` only.
- Forbidden：all other skills.

## Mode Selection

- **Full Mode（默认）**：Phase 1（Scout）+ Phase 2（Coach + 实时写入）+ Phase 3（Finalize）。用户需要系统学习整个学科/全书。
- **Scout Only**：仅 Phase 1，用户只想快速了解知识结构，暂不深入推导。用户说「先帮我梳理一下」「只做知识地图」时触发。
- **Coach Only**：仅 Phase 2 + 3，用户已有知识地图，只想被带着推导。用户说「直接开始推导」「知识结构我已经有了」时触发。
- **Targeted Coach**：仅对某几个概念做 Phase 2 深度推导。用户说「帮我推导第3章」「重点推导 XX 概念」时触发。

用户未指定时，默认走 Full Mode。

## Execution Flow

```
Intake（确认学科、资料、范围、模式、输出格式）
    │
    ▼
Phase 1: Scout（结构化总结）
    ├─ 1.1 确认原始资料（教材、重点、试卷）
    ├─ 1.2 分析知识体系宏观结构
    ├─ 1.3 构建概念链（概念之间的依赖和引出关系）
    ├─ 1.4 标注考试重点（如有试卷/重点）
    ├─ 1.5 生成知识地图（结构化笔记）
    ├─ 1.6 用户确认知识地图完整
    └─ 1.7 [HTML 模式] 创建 html 骨架文件
    │
    ▼
Phase 2: Coach（深度推导 + 实时写入 HTML）
    ├─ 2.1 从概念链起点开始
    ├─ 2.2 对每个概念：
    │   ├─ 提问：没有它，什么问题解决不了？
    │   ├─ 用户用自己的话解释
    │   ├─ 评估（清晰度 / 正确性 / 完整性）
    │   ├─ 一个关键追问
    │   ├─ 用户修正理解
    │   ├─ 补充易错点和考试要点（如有）
    │   ├─ [HTML 模式] 立即写入该概念的完整章节到 html
    │   └─ 连接下一个概念
    └─ 2.3 [HTML 模式] 发现误解即时追加到误解表
    │
    ▼
Phase 3: Finalize（收尾）
    ├─ [Markdown 模式] 一次性生成学科 Wiki + 概念笔记 + 误解清单
    ├─ [HTML 模式] 最终完整性检查 + 链接修复 + 复习路径标注
    └─ 确认文件写入磁盘
```

---

## Phase 1: Scout — 结构化总结

此阶段借鉴多智能体分段写作+验证的思路，将全书知识快速拆解为可学习的概念模块。

### Step 1.1 Intake

确认以下信息（用 AskUserQuestion 处理模糊情况）：

- **学科/课程名称**：如「概率论与数理统计」「线性代数」「宏观经济学」
- **原始资料**：教材名称+版本、老师画的重点、历年试卷、课件等
- **学习范围**：全书还是指定章节？
- **考试信息**（如有）：考试时间、题型分布、分值占比
- **输出格式**：Obsidian Markdown 还是 HTML 单文件（用户没说则用 AskUserQuestion）
- **模式确认**：Full / Scout Only / Coach Only / Targeted Coach

Default style：
- language：Chinese
- output path：当前工作目录下创建 `learn-everything-<subject-name>/` 文件夹

### Step 1.2 Analyze Knowledge Structure

- 阅读原始资料（教材目录、重点标注、试卷内容）
- 理解知识体系的宏观结构：有哪些编/章/节？各章之间的依赖关系？
- 识别概念层级：基础概念 → 中级概念 → 高级概念
- 识别考试重点分布（如有试卷）
- 构建分块映射

### Step 1.3 Build Concept Chain

这是核心步骤。按照第一性原理概念生长逻辑，构建全书的概念链：

```
起点问题/现象
    ↓
概念 A（为什么必须出现？它解决了什么？）
    ↓
概念 B（概念 A 引出了什么新问题？）
    ↓
概念 C
    ↓
...
```

每个概念标注：
- **前置依赖**：理解这个概念必须先理解什么
- **自然引出**：理解这个概念后，自然会产生什么问题，引出下一个概念
- **考试权重**（如有）：⭐（低频）~ ⭐⭐⭐⭐⭐（核心必考）

### Step 1.4 Annotate Exam Focus

如果用户提供了考试相关信息：

- 标注每个概念的考试频率和题型
- 标注老师画的重点
- 标注历年真题涉及的知识点
- 构建「考点×年份×题型」对照表

### Step 1.5 Generate Knowledge Map

输出 `learn-everything-<subject-name>/00-知识地图.md`（Markdown 模式）或整合到 HTML 中。

### Step 1.6 User Confirmation

将知识地图呈现给用户，确认：
- 知识点是否覆盖完整
- 概念链顺序是否合理
- 考试重点标注是否准确
- 是否需要调整范围

用户确认后进入 Phase 2。

### Step 1.7 [HTML 模式] 创建 HTML 骨架

如果是 HTML 模式，Phase 1 确认后立即创建 `<subject-name>-笔记.html` 文件：

- 写入完整知识地图（学习资料表、知识体系树状图、概念生长链、概念依赖详表、考试重点矩阵）
- 为每个概念预创建空的 `<section id="concept-概念名">`，内容暂标为 `<!-- pending -->`
- 侧边栏导航完整列出所有概念
- 误解清单表格留空（Phase 2 中逐步填充）
- 文件已可浏览器打开，但概念区显示「推导中…」

HTML 骨架模板详见 `templates/html-output-template.html`。

---

## Phase 2: Coach — 深度推导 + 实时写入 HTML

Phase 2 按概念链顺序逐个推导。读 `subskills/feynman-coach.md` 获取完整的教练规则。

### 🧠 傻子模式（Idiot Mode）

傻子模式是一个**随时可开关**的教练语言降级模式，专为「这个概念太难了，完全听不懂」的场景设计。

**开关触发词：**
- 激活：`开启傻子模式` / `用傻子都能懂的话讲` / `切换到 idiot mode` / `说人话` / `我完全听不懂`
- 退出：`退出傻子模式` / `关闭傻子模式` / `恢复正常模式` / `可以了，正常讲`

**激活后的行为规则（详见 `subskills/feynman-coach.md` 的 Idiot Mode 章节）：**

1. **零术语原则：** 每个专业术语第一次出现时必须用日常语言解释。不允许未经解释的术语。
2. **类比优先：** 每个抽象概念至少配一个日常类比（食物、走路、钱、天气、游戏、排队等）。
3. **短句原则：** 每句话不超过 30 个汉字。不用从句嵌套。
4. **先图后文：** 能用空间关系/视觉比喻解释的，先用比喻，再用文字。
5. **追问也降级：** 追问同样用最简单的语言——「你能用吃饭的例子解释一下这个吗？」
6. **考试要点不豁免：** 即使是考试重点，也必须用傻子能懂的语言解释。
7. **不降低内容深度：** 语言简单 ≠ 内容缩水。该讲的公式、定理、定义照样讲，只是用更朴素的语言包裹。

**退出后的行为：**
- 立即恢复到退出前的正常教练语言水平
- 不重新解释已讨论过的内容
- 用户已有的理解不受影响

**与正常模式的对比示例：**

| 正常模式 | 傻子模式 |
|----------|----------|
| 「随机变量是一个从样本空间映射到实数的可测函数」 | 「随机变量就是把『可能发生的事』变成一个『数字』。比如抛硬币：正面是 1，反面是 0。」 |
| 「条件概率描述了在给定事件 B 发生的条件下，事件 A 发生的概率」 | 「条件概率就是：你已经知道了一件事发生了，这时候另一件事发生的概率是多少。比如已知明天下雨，那明天下雨且你带伞的概率？」 |
| 「导数刻画了函数在某点的局部线性变化率」 | 「导数就是『变化的速度』。你开车时，速度表上的数字就是你的位置在变快还是变慢。」 |

### Core Principle

```
原始问题
    ↓
旧概念的局限
    ↓
新概念为什么必须出现
    ↓
最小定义
    ↓
最小例子
    ↓
暴露的新问题
    ↓
下一个概念
```

对每个概念，始终回归一个问题：

> **如果没有这个概念，我们在解决什么问题时会被卡住？**

### Step 2.1 Start from Concept Chain Root

从 Phase 1 生成的概念链起点开始。先不给出任何定义，只给出起点问题。

**标准开场：**

```text
我们先不背书上的定义。

你手上这本《XX》教材，它的逻辑起点是一个很自然的问题：

> 「起点问题」

从这个问题出发，教材引出了第一个核心概念——「概念 A」。

在你看定义之前，我想先问你：

**如果没有「概念 A」，我们在解决「起点问题」时会卡在哪里？**

请你用自己的话解释，不需要标准答案。
```

### Step 2.2 Coach Each Concept

对概念链中的每个概念，执行：

1. **提问**：没有它，什么问题解决不了？（或：从上一个概念自然产生的新问题是什么？）
2. **用户解释**：用户用自己的话回答
3. **评估**：从三个维度评估
   - **清晰度**：用户是否说清了核心思想？有没有用模糊词汇掩盖不理解？
   - **正确性**：是否存在事实错误或无效例子？
   - **完整性**：用户是否解释了为什么需要、给出例子、联系直觉与形式定义、区分相近概念？
4. **一个关键追问**：选择能修复最大理解缺口的一个问题追问。只问一个。
5. **用户修正**：追问后用户给出修正后的理解
6. **补充与连接**：用户理解到位后，补充易错点和考试要点，然后自然引出下一个概念
7. **[HTML 模式] 立即写入 HTML**：见下方详述

### Step 2.3 Response Pattern

用户每次回答后，使用以下反馈结构：

```markdown
你的回答里比较好的地方是：

- ...

目前最需要修正的一点是：

- ...

我先不直接给完整答案。你想一下：

> 「一个关键追问」
```

### Step 2.4 Ending Criteria for Each Concept

一个概念可以暂时认为「理解了」，当用户能够：

1. 说出它解决了什么问题
2. 解释为什么之前的概念不够用
3. 给出一个最简单的例子
4. 说出最简形式定义
5. 说出它自然引出了什么下一个概念

**满足条件后，该概念的推导视为完成，进入 Step 2.7 写入 HTML。**

### Step 2.5 Track Misconceptions

全程记录用户的误解和模糊点。每当用户在推导过程中暴露了一个理解偏差：

1. 在对话中指出并修正
2. **[HTML 模式]** 立即追加到 HTML 误解清单表格中一行
3. **[Markdown 模式]** 暂存，Phase 3 统一写入

### Step 2.6 Exam Connection（如有考试）

如果 Phase 1 标注了考试重点，在每个概念推导结束后，额外补充：

```text
这个概念在考试中通常这样考：
- 题型：...
- 频率：...
- 常见陷阱：...
- 典型真题：[年份·来源] ...
```

### Step 2.7 [HTML 模式] 实时写入概念章节

当一个概念达到「理解」标准后（用户给出了满足 Step 2.4 五个条件的解释），**立即**将该概念的完整内容写入 HTML 文件中对应的 `<section>`，替换 `<!-- pending -->` 占位符。

每个概念写入的内容包含（8 段结构）：

```html
<section id="concept-概念名" class="concept-note">
  <h2>{概念名} <span class="concept-status mastered">✓ 已掌握</span></h2>

  <h3>1. 一句话解释</h3>
  <p class="summary">（用户的最终理解，用他自己的话）</p>

  <h3>2. 为什么需要它？</h3>
  <p>（没有它会被什么问题卡住——Phase 2 开场问题的答案）</p>

  <h3>3. 它解决了什么问题？</h3>
  <p>（直接回答）</p>

  <h3>4. 定义</h3>
  <div class="definition">（形式化定义，公式用 \(...\) 或 \[...\]）</div>

  <h3>5. 最小例子</h3>
  <div class="example">（最简例子）</div>

  <h3>6. 反例或易错点</h3>
  <div class="pitfall">（常见错误理解）</div>

  <h3>7. 它自然引出什么？</h3>
  <p>引出：<a href="#concept-后续概念名">后续概念名</a></p>

  <h3>8. 相关概念</h3>
  <ul>
    <li>前置：<a href="#concept-前置概念">前置概念</a></li>
    <li>后续：<a href="#concept-后续概念">后续概念</a></li>
  </ul>

  <!-- 推导过程折叠区 -->
  <details class="derivation-log">
    <summary>📝 推导过程</summary>
    <p><strong>你的初始理解：</strong>（用户第一次的解释）</p>
    <p><strong>AI 追问：</strong>（关键追问）</p>
    <p><strong>修正后理解：</strong>（追问后的修正版本）</p>
  </details>
</section>
```

**关键点：**
- 保留用户的**原始语言**，不替换为教科书措辞——这是用户自己的 Wiki
- `<details>` 折叠区记录推导过程（初始理解 → 追问 → 修正），方便日后复习时回顾思维演变
- 侧边栏中该概念的链接更新状态标记（如从 `⏳` 变为 `✓`）
- 误解清单如有新增，同时追加一行到 `<section id="misconceptions">` 的表格

**写入后的用户提示：**

```text
「概念 A」已写入你的笔记。你可以随时打开 learn-everything-<subject-name>/<subject-name>-笔记.html 查看当前进度。

下一个概念：「概念 B」 ← 概念 A 自然引出的问题
准备好了我们继续。
```

### HTML 实时写入规则总结

| 时机 | 写入内容 |
|------|----------|
| Phase 1 结束 | 知识地图全量写入，所有概念占位 `<!-- pending -->` |
| 每个概念理解到位 | 该概念的 8 段完整内容 + 推导过程折叠区 |
| 发现误解 | 追加一行到误解清单表格 |
| Phase 3 收尾 | 检查所有占位是否已替换、链接是否有效、补充复习路径 |
| 每次写入后 | 确认文件已保存到磁盘 |

---

## Phase 3: Finalize — 收尾

### Markdown 模式

Phase 2 结束后，一次性生成全部文件。读 `subskills/wiki-compiler.md` 获取完整规则。

#### Step 3.1 Generate Subject Wiki

输出 `learn-everything-<subject-name>/<subject-name>-Wiki.md`

#### Step 3.2 Generate Concept Notes

为每个概念生成独立笔记：`learn-everything-<subject-name>/concepts/概念名.md`（8 段结构）

#### Step 3.3 Generate Misconception Table

输出 `learn-everything-<subject-name>/08-误解清单.md`

### HTML 模式

HTML 的 90% 内容已在 Phase 2 中实时写入。Phase 3 仅做：

1. **完整性检查**：确认所有概念的 `<!-- pending -->` 已被替换，无遗漏
2. **链接检查**：所有 `<a href="#concept-...">` 锚点链接指向有效 id
3. **误解表收尾**：检查误解清单是否完整，状态列更新
4. **复习路径**：在 HTML 底部 `#review-path` 区域标注已掌握/需复习/下一步
5. **最终保存**：确认文件已写入磁盘

### Step 3.4 Next Steps（两种模式通用）

标注下一步学习路径：
- 已掌握的概念
- 还需复习的概念
- 下一个自然问题
- 建议的复习时间

---

## Resources

- `subskills/feynman-coach.md`：第一性原理教练的提问与评估规则
- `subskills/concept-growth.md`：通用概念生长链构建方法
- `subskills/wiki-compiler.md`：笔记输出规则（Markdown 与 HTML 双模式，含实时写入细则）
- `subskills/misconception-review.md`：误解跟踪与复习提示
- `templates/knowledge-map-template.md`：知识地图模板
- `templates/concept-note-template.md`：概念笔记模板（8 段结构）
- `templates/subject-wiki-template.md`：学科 Wiki 主页模板（Markdown 模式）
- `templates/misconception-table-template.md`：误解清单模板
- `templates/session-summary-template.md`：学习会话摘要模板
- `templates/html-output-template.html`：HTML 单文件输出模板

## Output Structure

### Obsidian Markdown 模式

```
learn-everything-<subject-name>/
├── 00-知识地图.md              # Phase 1 产出
├── <subject-name>-Wiki.md      # Phase 3 产出：学科 Wiki 主页
├── concepts/                   # Phase 3 产出：概念笔记
│   ├── 概念A.md
│   ├── 概念B.md
│   └── ...
├── 08-误解清单.md               # Phase 3 产出
└── 09-学习会话记录.md           # 每次学习的会话摘要
```

### HTML 单文件模式（活 Wiki）

```
learn-everything-<subject-name>/
├── 00-知识地图.md              # Phase 1 产出（Markdown，内部参考用）
├── <subject-name>-笔记.html    # 活 Wiki：Phase 1 末创建，Phase 2 持续更新，Phase 3 收尾
└── 09-学习会话记录.md           # 学习会话摘要
```

## Do Not

- Do not skip Phase 1 and jump directly into coaching — the user needs the map first.
- Do not skip Phase 2 and only output notes — deep understanding comes from coaching, not just reading.
- Do not list textbook definitions before exploring why they are needed.
- Do not ask several diagnostic questions at once.
- Do not skip the user's reasoning process.
- Do not present knowledge as a fixed chapter outline to be memorized.
- Do not treat mistakes as failure; treat them as review material.
- **HTML 模式：Do not wait until Phase 3 to write concept content** — write immediately after each concept is understood.
- **HTML 模式：Do not replace the user's own wording with textbook prose** — the HTML is their living Wiki.
- Do not generate LaTeX/Typst PDF output — this skill outputs Markdown or HTML only.
- Do not claim completion without confirming files are written to disk.

## Common Failure Modes

- 跳过 Phase 1 直接进入 Phase 2，用户缺乏全局视野
- Phase 1 概念链构建不合理，依赖关系颠倒
- Phase 2 一次抛出多个问题，用户应接不暇
- Phase 2 不给用户思考和解释的机会，直接给出完整答案
- Phase 2 低估边缘知识——即使低频考点也至少一句话提及
- **HTML 模式：「推导完了但忘了写进 HTML」——每个概念理解后必须立即写入**
- **HTML 模式：写入 HTML 时用了教科书语气而非用户自己的话**
- Phase 3 笔记没有用 Wiki-links 连接概念（Markdown 模式）
- Phase 3 误解清单未记录或格式不规范
- HTML 模式 MathJax 公式未正确闭合
- 声称完成但文件未写入磁盘
- 输出路径散乱，文件未放入 `learn-everything-<subject-name>/` 文件夹

## Red Flags

- Phase 1 知识地图缺章少节
- Phase 1 概念链无依赖/引出关系标注
- Phase 1 未确认就直接进入 Phase 2
- Phase 2 连续提问不给反馈
- Phase 2 用户反复答错同一概念未被记录为误解
- Phase 3 概念笔记缺少「为什么需要它」
- Phase 3 笔记间链接断裂（Markdown 模式）
- **HTML 模式：HTML 文件中仍有 `<!-- pending -->` 占位符未被替换**
- **HTML 模式：用户隔天打开 HTML，发现昨天的推导内容没写进去**
- 输出文件不在指定文件夹
- HTML 文件无法在浏览器中正常渲染

All of these mean：stop, fix, and re-run verification before finalizing.
