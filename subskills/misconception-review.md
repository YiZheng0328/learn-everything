# Misconception Review Subskill（通用版）

## Role

Track user misunderstandings during Phase 2 coaching and convert them into review prompts. Adapted from math-feynman-learning for general disciplines.

## Core Principle

Misunderstandings are **useful traces of knowledge growth**. Preserve them as material for review instead of treating them as failure. A corrected misconception is often more firmly understood than something learned correctly the first time.

## Misconception Table Format

Use this format in `08-误解清单.md`：

```markdown
| 概念 | 原始误解 | 为什么不准确 | 修正后理解 | 复习问题 | 相关笔记 |
|---|---|---|---|---|---|
|  |  |  |  |  |  |
```

## When to Record

Record a misconception when：

- The user explicitly says something factually wrong.
- The user gives an example that contradicts the concept.
- The user confuses two distinct concepts.
- The user omits a critical condition or assumption.
- The user cannot apply the concept to a simple case.
- The user's answer reveals a fundamental misunderstanding (not just a small slip).

Don't record minor wording imprecisions or nervous hesitations — focus on genuine understanding gaps.

## Review Prompt Rules

Good review prompts ask the user to：

1. Explain in their own words.
2. Compare two similar concepts.
3. Give an example.
4. Give a counterexample.
5. Explain why a condition is necessary.
6. Apply the concept to a new situation.

Avoid prompts that only ask for memorized definitions.

## Example Review Prompts（通用）

```text
请你用自己的话解释：为什么「XX」和「YY」不是一回事？举一个例子说明。
```

```text
你能想出一个情况，在这个情况下「XX 条件」不满足，所以结论不成立吗？
```

```text
如果去掉「XX 假设」，这个理论/公式/规则还会成立吗？为什么？
```

```text
请你用一个你生活中的例子，说明这个概念在现实中是怎么体现的。
```

## Review Workflow

1. **Select** one misconception from the table.
2. **Ask** the user to explain the corrected version.
3. **Ask** for an example or counterexample.
4. **Evaluate** the answer.
5. If still unclear，**ask one targeted follow-up**.
6. **Update** the misconception table if understanding improves.

## When to Schedule Review

Suggest review when：

- A concept was marked「模糊」in the subject Wiki progress.
- A misconception was recorded in the current session.
- The user hasn't revisited a concept for more than a week.
- The user is about to learn a concept that depends on a previously misunderstood one.

## Review Reminder Format

```text
上次学习「XX」时，你对「YY」的理解有一个需要修正的地方：

原始理解：...
为什么不准确：...
修正后理解：...

复习问题：请你现在用自己的话重新解释一遍，并给一个新例子。
```
