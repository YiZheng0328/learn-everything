# 🧠 Learn Everything — 快速掌握任意知识点

> **🚧 发布前请全局替换 `your-org/learn-everything` 为你的 GitHub 仓库路径。**

<p align="center">
  <em>两阶段 AI 学习系统：先画知识地图，再用第一性原理带你逐个概念推导到根。<br>
  你的每一句话都直接变成笔记 —— 对话即 Wiki。</em>
</p>

<p align="center">
  <a href="#demo">🎬 Demo</a> ·
  <a href="#核心设计">🏗️ 核心设计</a> ·
  <a href="#特性">✨ 特性</a> ·
  <a href="#安装">📦 安装</a> ·
  <a href="#快速开始">🚀 快速开始</a> ·
  <a href="#使用示例">📖 使用示例</a> ·
  <a href="#产出结构">📂 产出结构</a>
</p>

---

## 🎬 Demo

<p align="center">
  <em>完整学习流程演示：从零到掌握「微观经济学」核心概念</em>
</p>

<p align="center">
  <a href="https://github.com/your-org/learn-everything/releases" title="下载 Demo 视频">
    <img src="https://img.shields.io/badge/%F0%9F%93%B9_Demo_Video-75MB-terracotta?style=for-the-badge" alt="Demo Video" />
  </a>
</p>

<details>
<summary><strong>📺 点击查看 Demo 内容预览</strong></summary>

Demo 视频展示了一个完整的 Full Mode 学习流程：

1. **Intake** — 确认学科（微观经济学）、资料（范里安教材）、范围（1-8 章）
2. **Phase 1: Scout** — AI 分析全书知识结构，构建概念生长链，标注考试重点
3. **Phase 2: Coach** — 从「稀缺性」开始，AI 逐概念提问，用户解释 → AI 追问 → 修正
4. **实时 HTML 写入** — 每理解一个概念，立即写入 HTML 笔记
5. **Phase 3: Finalize** — 完整性检查，生成最终笔记文件

</details>

> 💡 **Demo 视频（~75MB）下载方式：**
> - **[GitHub Releases](https://github.com/your-org/learn-everything/releases)** — 下载最新版本附带的 `learn-everything-demo.mp4`
> - **克隆仓库** — `git clone` 后播放 `demo/learn-everything-demo.mp4`
>
> 建议下载到本地后用 VLC / mpv / QuickTime 等播放器打开。

---

## 这是什么？

**Learn Everything** 是 Claude Code 的一个 skill，帮你快速掌握任意学科 —— 无论你手里有教材、重点、试卷，还是只想入手一个新领域。

它不是一个「总结工具」。它是一个**两阶段学习教练**：

| 阶段 | 做什么 | 产出 |
|------|--------|------|
| **Phase 1: Scout** | 结构化速览全书 → 构建知识地图 + 概念生长链 + 考点矩阵 | 你看到「有什么」 |
| **Phase 2: Coach** | 按概念链顺序，逐个问你「没有它，什么问题解决不了？」→ 你解释 → AI 追问 → 修正 | 你理解「为什么」 |
| **Phase 3: Finalize** | 收尾检查，生成完整笔记 | 所有内容写入磁盘 |

**核心理念：先知道「有什么」（知识地图），再理解「为什么」（第一性原理推导）。**

---

## 核心设计

```text
┌─────────────────────────────────────────────────┐
│  Phase 1: Scout（结构化速览）                     │
│  教材 + 重点 + 试卷 → 知识地图 + 概念链 + 考点表  │
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

### 概念生长链（Concept Growth Chain）

每个概念不是孤立的知识点，而是从一个自然问题生长出来的：

```
起点问题/现象
    ↓
概念 A（为什么必须出现？它解决了什么？）
    ↓ 概念 A 引出了什么新问题？
概念 B（为什么必须出现？它解决了什么？）
    ↓
概念 C
    ↓
...
```

每个概念标注**前置依赖**、**自然引出**和**考试权重**（⭐～⭐⭐⭐⭐⭐）。

---

## ✨ 特性

### 🧠 傻子模式（Idiot Mode）

> 随时说「用傻子都能懂的话讲」，AI 会用最朴素的语言解释 —— 零术语、类比优先、每句话不超过 30 字。

| 正常模式 | 傻子模式 |
|----------|----------|
| 「随机变量是一个从样本空间映射到实数的可测函数」 | 「随机变量就是把『可能发生的事』变成一个『数字』。比如抛硬币：正面是 1，反面是 0。」 |
| 「导数刻画了函数在某点的局部线性变化率」 | 「导数就是『变化的速度』。你开车时，速度表上的数字就是你的位置在变快还是变慢。」 |

**不降低内容深度** —— 该讲的公式、定理照样讲，只是用日常语言包裹。

### 📝 活 Wiki（HTML 模式）

选择 HTML 输出后，你的学习笔记是**实时生长**的：

- **Phase 1 末**：创建 HTML 骨架（知识地图 + 所有概念占位）
- **Phase 2 中**：每理解一个概念，**立即写入** 8 段完整内容到 HTML
- **你最初的话、AI 的追问、修正后的理解**——全部保留在可折叠的推导记录中
- **发现误解**：即时追加到误解清单表格
- **随时打开浏览器**查看当前学习进度

> 💡 对话结束，笔记也写完了。不需要「先聊天，后总结」。

### 📋 四模式灵活切换

| 模式 | 用途 | 触发 |
|------|------|------|
| **Full** | 系统学习全书 | 默认 |
| **Scout Only** | 只画知识地图，不深入推导 | 「先帮我梳理一下」 |
| **Coach Only** | 已有知识地图，直接推导 | 「直接开始推导」 |
| **Targeted Coach** | 只深度推导某几个概念 | 「帮我推导第 3 章」 |

### 🎯 考试集成

如果你有教材、老师重点、历年试卷 —— skill 会：

- 标注每个概念的考试频率和题型
- 构建「考点 × 年份 × 题型」对照表
- 在每个概念推导后补充典型真题和常见陷阱

### 📐 双输出格式

| 格式 | 适用场景 | 写入策略 |
|------|----------|----------|
| **Obsidian Markdown** | Obsidian vault 内学习 | Phase 3 一次性批量生成 |
| **自包含 HTML** | 浏览器直接打开，活 Wiki | Phase 1 骨架 → Phase 2 实时逐概念写入 → Phase 3 收尾 |

---

## 📦 安装

### 前置条件

- [Claude Code](https://claude.ai/code) 已安装并登录

### 安装方式

**方法一：克隆到 Claude Code skills 目录**

```bash
# 进入你的 Claude Code skills 目录
cd ~/.claude/skills/

# 克隆本仓库
git clone https://github.com/your-org/learn-everything.git

# 或者如果你有自定义 skills 目录
cd /path/to/your/project/.claude/skills/
git clone https://github.com/your-org/learn-everything.git
```

**方法二：直接下载**

从 [Releases](https://github.com/your-org/learn-everything/releases) 下载最新版本，解压到 `.claude/skills/learn-everything/`。

### 验证安装

在 Claude Code 中输入：

```
/learn-everything
```

如果看到 Intake 确认流程启动，说明安装成功。

---

## 🚀 快速开始

### 30 秒上手

```
/learn-everything
```

然后告诉 AI：
- **你想学什么**（例如：「概率论与数理统计」）
- **你有什么资料**（例如：「浙大版教材，老师画了第 1-5 章重点」）
- **有考试吗**（例如：「期末考，选择+填空+计算+证明」）

AI 会先确认信息，然后自动进入 Phase 1，开始构建知识地图。

### 典型流程

```
用户：/learn-everything
AI： 你想学什么？有什么资料？
用户：帮我快速掌握微观经济学，范围是第 1-8 章，
      教材是范里安《微观经济学：现代观点》第九版
AI： 好的。[确认输出格式、模式...]
     进入 Phase 1...
     [输出知识地图 - 概念生长链 - 考点矩阵]
     确认完整吗？
用户：确认！
AI： 进入 Phase 2...
     我们先不背书上的定义。
     如果没有「稀缺性」这个概念，经济学在解释什么现象时会卡住？
用户：[用自己的话解释]...
AI： 你的回答里比较好的地方是...
     目前最需要修正的一点是...
     你想一下：「一个关键追问」
...
```

---

## 📖 使用示例

### 例子：概率论与数理统计（第 1-5 章）

**Phase 1 产出的概念生长链：**

```text
起点问题：如何描述和量化不确定性？
    ↓
随机试验 — 把不确定性转化为可重复讨论的对象
    ↓ 随机试验的所有可能结果怎么表示？
样本空间 — 列出所有可能结果
    ↓ 我们关心的往往是某些结果的集合而非单个结果
事件 — 样本空间的子集
    ↓ 如何比较事件发生的可能性大小？
概率 — 给每个事件赋一个数字
    ↓ 概率赋值需要规则避免矛盾
概率公理 — 非负性、规范性、可列可加性
    ↓ 有了新信息，概率判断会改变
条件概率 — P(A|B) = P(AB)/P(B)
    ↓ 有些信息改变概率，有些不改变
独立性 — P(AB) = P(A)P(B)
    ↓ 为了计算收益/风险/平均，需要把结果变成数字
随机变量 — 从样本空间到实数的函数
    ↓ ...
期望 → 方差 → 协方差 → 大数定律 → 中心极限定理
```

**Phase 2 推导片段：**

```
AI：我们先不背书上的定义。

    如果没有「随机试验」这个概念，我们在描述现实中的不确定性时，
    会遇到什么问题？

    请你用自己的话解释。

用户：我觉得随机试验就是为了把不确定的事情固定下来，
      比如抛硬币，虽然结果不确定，但我们能反复做，每次条件都一样。

AI：你的回答里比较好的地方是：
    - 抓住了「可以反复做」「条件一样」两个关键点
    - 用抛硬币做例子，很直观

    目前最需要修正的一点是：
    - 你只说了「可以反复做」，但没提到更基本的要求：
      做试验之前，我们必须知道所有可能的结果有哪些

    你想一下：
    > 如果一个人说做了一个试验，但试验前完全不知道可能的结果是什么，
    > 我们能对这个试验讨论概率吗？
```

完整示例见 [`examples/probability-full-example.md`](examples/probability-full-example.md)。

---

## 📂 产出结构

### Markdown 模式

```
learn-everything-<学科名>/
├── 00-知识地图.md              # 知识体系 + 概念链 + 考点矩阵
├── <学科名>-Wiki.md            # 学科 Wiki 主页
├── concepts/                   # 概念笔记（每个概念一个文件）
│   ├── 概念A.md                #   8 段结构
│   ├── 概念B.md
│   └── ...
├── 08-误解清单.md               # 记录每个误解和修正
└── 09-学习会话记录.md           # 每次学习的会话摘要
```

### HTML 模式（活 Wiki）

```
learn-everything-<学科名>/
├── 00-知识地图.md              # 内部参考
├── <学科名>-笔记.html          # 活的 Wiki 文件（浏览器打开）
└── 09-学习会话记录.md
```

> **HTML 文件包含：** 知识地图 → 侧边栏导航 → 每个概念的 8 段完整笔记 → 推导过程折叠区 → 误解清单 → 复习路径标注。MathJax 渲染公式。

---

## 🗺️ Skill 架构

```
learn-everything/
├── SKILL.md                         # 主 skill 定义（完整规则）
├── README.md                        # 👈 本文件
├── subskills/                       # 子技能
│   ├── feynman-coach.md             #   第一性原理教练规则 + 傻子模式
│   ├── concept-growth.md            #   通用概念生长链构建方法
│   ├── wiki-compiler.md             #   笔记输出规则（MD + HTML 双模式）
│   └── misconception-review.md      #   误解跟踪与复习提示
├── templates/                       # 输出模板
│   ├── knowledge-map-template.md    #   知识地图模板
│   ├── concept-note-template.md     #   概念笔记模板（8 段结构）
│   ├── subject-wiki-template.md     #   学科 Wiki 主页模板
│   ├── misconception-table-template.md  # 误解清单模板
│   ├── session-summary-template.md  #   学习会话摘要模板
│   └── html-output-template.html   #   HTML 单文件输出模板
├── agents/                          # 多智能体定义
│   ├── segment-writer.md
│   └── verifier.md
└── examples/                        # 使用示例
    └── probability-full-example.md  #   概率论完整示例
```

---

## ❓ FAQ

<details>
<summary><strong>Q: 这个 skill 和普通 AI 聊天学习有什么不同？</strong></summary>

普通聊天是「你问，AI 答」。Learn Everything 是结构化学习系统：

- **Phase 1** 先给你全局视野 —— 知道整个知识体系长什么样
- **Phase 2** 不是讲给你听，而是**反过来问你** —— 让你自己解释，AI 只追问最关键的一个问题
- 所有学习过程**自动写笔记** —— 不需要手动整理
</details>

<details>
<summary><strong>Q: 我只有教材，没有考试重点，能用吗？</strong></summary>

完全可以。考试集成是可选的。Skill 会基于教材目录构建知识体系，考试相关部分自动跳过。
</details>

<details>
<summary><strong>Q: 傻子模式什么时候用？</strong></summary>

任何时候觉得某个概念太抽象、听不懂，直接说「开启傻子模式」或「说人话」。AI 会用最朴素的语言（类比食物、走路、钱、天气等）重新解释，零专业术语。听懂后说「恢复正常模式」即可。
</details>

<details>
<summary><strong>Q: HTML 模式和 Markdown 模式怎么选？</strong></summary>

| 场景 | 推荐 |
|------|------|
| 用 Obsidian 管理知识库 | Markdown |
| 浏览器直接看笔记 | HTML |
| 想要「边学边写」体验 | HTML |
| 想要多文件、用 Wiki-links 连接 | Markdown |
| 只需最终笔记、不需要过程 | Markdown |

</details>

<details>
<summary><strong>Q: 适用于哪些学科？</strong></summary>

**所有学科。** 数学、物理、计算机、经济、管理、语言、医学、法律……概念生长逻辑是通用的。Skill 内置了分学科的混淆模式检测（见 `subskills/feynman-coach.md`）。
</details>

<details>
<summary><strong>Q: 能不能只做一个部分？</strong></summary>

可以。四种模式：

- **Scout Only**：只画知识地图
- **Coach Only**：直接推导
- **Targeted Coach**：只推导某几个概念
- **Full**：完整流程（默认）

</details>

---

## 🤝 贡献

欢迎提交 Issue 和 PR。

### 贡献方向

- 📝 **模板改进**：优化概念笔记模板或 HTML 样式
- 🔬 **学科适配**：为特定学科添加混淆模式检测规则
- 🐛 **Bug 修复**：概念链依赖错误、输出格式问题等
- 🌐 **英文适配**：添加英文模板和教练规则

---

## 📄 许可

MIT License

---

<p align="center">
  <em>Built with ❤️ for learners who want to understand, not just memorize.</em>
</p>
