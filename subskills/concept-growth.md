# Concept Growth Subskill（通用版）

## Role

Guide concepts in any discipline to grow naturally from prior problems. Every concept should appear as a **necessary response** to a limitation in the previous conceptual system. Adapted from math-feynman-learning for general disciplines.

## Universal Template

For any concept in any subject, reconstruct using this sequence：

```markdown
## 当前问题

（我们最初要解决什么问题？）

---

## 旧概念的不足

（已有的概念/方法/理论为什么不够用？）

---

## 新概念为什么必须出现

（在什么意义上，不引入这个概念我们就「卡住」了？）

---

## 最小定义

（这个概念的最简形式定义是什么？）

---

## 最小例子

（用一个最简单的例子检验理解）

---

## 它自然引出的下一个问题

（掌握了这个概念后，自然而然会产生什么新问题？）
```

## Diagnostic Sequence（7 步推导链）

For each concept，ask these 7 questions in order：

1. **What problem were we originally trying to solve？**
2. **What concepts / methods / tools did we already have？**
3. **Why were those not enough？**（This is the most important question.）
4. **What new idea do we need？**（Object, operation, relation, rule, framework, etc.）
5. **What is the simplest version of this new idea？**
6. **How can we test it with a minimal example？**
7. **What new question does it create？**

## Building Subject-Specific Concept Chains

When the user brings a new subject，build the concept chain from the textbook/materials：

### Step 1：Find the Starting Problem

Every subject starts with a problem or question. Identify it：

- 数学类：「如何描述不确定性？」「如何精确描述变化？」
- 物理类：「物体为什么运动？」「光到底是什么？」
- 经济类：「资源有限时如何分配？」「市场如何协调分散决策？」
- 计算机类：「什么问题可以用算法解决？」「如何组织大量数据？」
- 语言类：「如何表达过去/现在/未来？」「不同语言如何组织信息？」

### Step 2：Trace the Chain from the Textbook

From the textbook's table of contents and teaching order，extract the natural concept chain：

```
起点问题
    ↓
概念 A（回答了起点问题的哪个方面？）
    ↓ 概念 A 产生了什么新问题？
概念 B
    ↓
概念 C
    ↓
...
```

For each link in the chain，answer：
- **Why must B appear after A？** What limitation of A does B address？
- **Could we learn B without A？** If not，why not？（This tests genuine dependency vs arbitrary ordering.）

### Step 3：Validate Against Exam Pattern

If exam papers / teacher's key points are available，cross-validate：
- Does the exam chain match the concept chain？
- Are there concepts that exam emphasizes more than the textbook suggests？
- Are there「bridge concepts」that link two seemingly unrelated topics？

## Expansion Rules

When building out from a single concept into a broader framework：

- Give a **concept chain**，not a chapter outline.
- Explain **why each next concept becomes necessary**.
- Mark the user's **current position** and the **next learning question**.
- Keep the chain compact unless the user asks for full notes.

## Concept Chain Validation Checklist

After building the chain，verify：

- [ ] Every concept has a clear「why must it exist」reason
- [ ] Every concept (except the first) has a clear predecessor that it depends on
- [ ] Every concept (except the last) has a clear successor that it naturally leads to
- [ ] No circular dependencies
- [ ] The chain covers all major topics in the textbook/scope
- [ ] Exam-important concepts are flagged
