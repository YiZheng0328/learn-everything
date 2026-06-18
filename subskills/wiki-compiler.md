# Wiki Compiler Subskill（Learn Everything 版）

## Role

Transform Learn Everything learning sessions into structured notes. Supports two output formats with fundamentally different write strategies：
- **Obsidian Markdown**：多个 `.md` 文件，Wiki-links 连接。Phase 3 一次性批量生成。
- **Self-contained HTML（活 Wiki）**：单个 `.html` 文件。Phase 1 末创建骨架，Phase 2 每完成一个概念立即写入，Phase 3 仅收尾。

## Core Principle

笔记不是静态摘要，而是用户理解生长的**活记录**——用户自己的话、自己的困惑、自己的修正。

**HTML 模式的核心承诺：用户的对话直接变成 Wiki。** 不再有「先对话、后总结」的两段式体验——对话过程本身就是笔记的生成过程。

---

## 输出格式 A：Obsidian Markdown（Phase 3 批量生成）

### Subject Wiki Rules

Before compiling or updating any subject Wiki，the compiler **must**：

1. Read the subject Wiki homepage（如有）.
2. Read the `raw_source` field in the YAML frontmatter.
3. Read every `.md` document linked in `raw_source`.
4. Use these raw source documents as the primary factual baseline.

A subject Wiki should record：

1. **Learning goal**：为什么要学这门课
2. **Raw source documents**：教材、重点、试卷等原始资料列表
3. **Core starting problem**：这门课的起点问题是什么
4. **Current concept chain**：完整的概念生长链
5. **Current progress**：已掌握 / 仍模糊 / 下一步
6. **Concept nodes**：每个概念节点的摘要
7. **User's own explanation versions**：用户自己的解释（初始 → 修正 → 最终）
8. **Mistakes and confusions**：误解清单
9. **Next learning question**：下一步学什么

Use Obsidian links for concept notes：

```markdown
- [[concepts/样本空间]]
- [[concepts/事件]]
- [[concepts/概率]]
```

### Concept Note Rules（Markdown 模式）

Each concept note should focus on **one** concept and include（see `templates/concept-note-template.md`）：

1. **一句话解释**：最简的直觉理解
2. **为什么需要它**：没有它，什么问题解决不了
3. **它解决了什么问题**：直接回答
4. **定义**：形式化定义（可含公式）
5. **最小例子**：最简单能说明问题的例子
6. **反例或易错点**：常见的错误理解
7. **它自然引出什么**：下一个概念
8. **相关概念**：Wiki-links 链接

Preserve the user's **improved phrasing** when useful. Do not replace all reasoning with textbook prose.

Use LaTeX for mathematical notation（`$...$` inline，`$$...$$` display）. Do not leave formulas as plain text.

---

## 输出格式 B：自包含 HTML 单文件（活 Wiki，Phase 1-3 持续更新）

HTML 模式的核心不同点：**文件不在 Phase 3 一次性生成，而是从 Phase 1 末开始创建，Phase 2 中每完成一个概念就立即写入，Phase 3 仅做收尾检查。**

### 三步生命周期

#### 第一步：Phase 1 末 — 创建骨架

Phase 1 确认知识地图后，立即创建 HTML 文件并写入：

1. **完整知识地图**（`#knowledge-map`）：学习资料表、知识体系树状图、概念生长链、概念依赖详表
2. **空概念占位**：为每个概念创建一个 `<section id="concept-概念名" class="concept-note">`, 内容为 `<!-- pending: 概念名 -->`
3. **完整侧边栏导航**：列出所有概念（每个旁标状态图标 `⏳`）
4. **空误解清单表格**：`<section id="misconceptions">` 中的 `<table>` 仅有表头
5. **空复习路径**：`<section id="review-path">` 内容为 `（学习完成后填写）`

**此时 HTML 已可浏览器打开，显示知识地图和「概念推导中…」的占位 UI。**

#### 第二步：Phase 2 中 — 每完成一个概念立即写入

每当一个概念满足 SKILL.md Step 2.4 的五条「理解」标准后，**立即**：

1. **定位**：在 HTML 文件中找到 `<section id="concept-概念名">`
2. **替换**：将 `<!-- pending: 概念名 -->` 替换为完整的 8 段内容（见下方 HTML 概念笔记格式）
3. **同步状态**：侧边栏中该概念的图标从 `⏳` 改为 `✓`
4. **写入推导过程**：在 `<details class="derivation-log">` 中记录：
   - 用户的初始理解
   - AI 的关键追问
   - 用户修正后的理解
5. **保存文件**：用 Write 或 Edit 工具确认写入磁盘

**写入时机判断口诀：用户能用自己的话说出「它解决什么问题 + 为什么之前的不够 + 最简例子 + 定义 + 引出什么」，就立刻写。**

#### 第三步：发现误解时 — 即时追加到误解表

每当 Phase 2 中发现用户对某个概念存在理解偏差：

1. **定位**：HTML 文件中 `<section id="misconceptions">` 的 `<table>`
2. **追加一行**：`<tr>` 包含概念名（链接到对应章节）、原始误解、为什么不准确、修正后理解、状态（「已修正」或「待复习」）

#### 第四步：Phase 3 — 收尾检查

1. **完整性检查**：grep HTML 文件确认无残留 `<!-- pending -->`
2. **链接检查**：所有 `<a href="#concept-...">` 指向的 id 存在
3. **误解表收尾**：检查所有 Phase 2 中记录的误解是否已写入
4. **复习路径**：写入已掌握/需复习/下一步到 `#review-path`
5. **最终保存**

### HTML 概念笔记格式（实时写入用）

```html
<section id="concept-概念名" class="concept-note">
  <h2>{概念名} <span class="concept-status mastered">✓</span></h2>

  <h3>1. 一句话解释</h3>
  <p class="summary">（用户自己的最终理解，保留其语言风格）</p>

  <h3>2. 为什么需要它？</h3>
  <p>（没有它会被什么问题卡住）</p>

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

  <details class="derivation-log">
    <summary>📝 推导过程（点击展开）</summary>
    <div class="derivation-step">
      <strong>🔰 你的初始理解：</strong>
      <p>（用户第一次用自己的话解释的内容）</p>
    </div>
    <div class="derivation-step">
      <strong>❓ AI 追问：</strong>
      <p>（关键追问）</p>
    </div>
    <div class="derivation-step">
      <strong>✅ 修正后理解：</strong>
      <p>（追问后的修正版本——这是最终写入「一句话解释」的来源）</p>
    </div>
  </details>
</section>
```

**⚠️ 语言风格铁律：写入 HTML 的内容必须保留用户自己的措辞。** 不要替换为教科书表述。用户的「不准确但正在进步」的表达比完美的教科书定义更有价值——这记录的是理解的过程，不是最终答案。

### HTML 骨架中的占位符标记

```html
<!-- 概念未推导时的占位符 -->
<section id="concept-概念名" class="concept-note pending">
  <h2>{概念名} <span class="concept-status">⏳</span></h2>
  <p class="pending-msg">推导中…</p>
</section>
```

### HTML 误解清单表格行格式

```html
<tr id="misconception-1">
  <td>1</td>
  <td><a href="#concept-概念名">概念名</a></td>
  <td>（用户最初的理解偏差）</td>
  <td>（为什么不准确）</td>
  <td>（修正后的正确理解）</td>
  <td><span class="status-fixed">已修正</span></td>
</tr>
```

完整 HTML 模板详见 `templates/html-output-template.html`。

---

## Session Summary Rules

After each coaching session，append to `09-学习会话记录.md`：

```markdown
## 学习会话 #N — YYYY年M月D日

### 讨论的概念
- 概念 A
- 概念 B

### 用户的初始理解
...

### 关键追问
...

### 修正后的理解
...

### 新发现的概念联系
...

### 仍需复习的模糊点
...

### 下次学习入口
...
```

## Trigger Discipline

- **(Markdown 模式)** Only generate full output when the user says：整理成笔记 / 生成笔记 / 更新 Wiki / 总结本轮学习 / 沉淀成 Markdown / 生成概念笔记。During Phase 2 coaching，do NOT generate large notes after every small answer. Wait until Phase 3.
- **(HTML 模式)** 完全不同的规则：**每次概念推导完成后立即写入 HTML，不需要等用户说「生成笔记」。** 这是 HTML 模式的核心优势——对话即 Wiki。用户不需要额外触发词，写入是自动的、实时的。

## Output Format Rules

- **(Markdown 模式)** All notes use **YAML frontmatter** with at least `subject`，`concept`，`date`，`status` fields.
- **(Markdown 模式)** All concept-to-concept references use **Obsidian Wiki-links**：`[[concepts/概念名]]`
- **(HTML 模式)** All concept-to-concept references use **锚点链接**：`<a href="#concept-概念名">`
- All formulas use **LaTeX**：`$inline$` or `$$display$$`（Markdown）/ `\(...\)` or `\[...\]`（HTML）
- All dates use **中文完整格式**：`YYYY年M月D日`（如 `2026年6月18日`）
- Output directory：`learn-everything-<subject-name>/`
