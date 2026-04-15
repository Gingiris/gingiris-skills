# Iris 文风指南

> 来源：用户反馈 `feedback_iris_writing_style.md`（见 MEMORY.md）
> 用途：所有 gr-blog-post 产文本、gr-ph-launch maker comment、gr-seo-patrol 报告都应遵循

---

## 5 大核心要素

### 1. 时间锚定开场
**❌**：SEO 对独立开发者很重要。
**✅**：2026-04-10，凌晨 3 点，后台流量归零。

让读者立刻知道「这是一个真实场景在展开」。

### 2. 括号旁白
正文一句，括号里塞"只有圈内人懂"的私货。
例：
- "我们发了第 30 篇（是的，疯了）"
- "canonical 没改对（这个坑踩过三次）"

### 3. em-dash 转折
不用"但是"、"然而"，用 `——`。
例：
- "一切看起来都好 —— 直到 Google 一次更新吃掉 50% 流量。"
- "这个 framework 在美国有效 —— 日本完全不行。"

### 4. Key Stats 表格
文章开头或第一个 H2 下，立刻放硬数据：

| 指标 | 数字 |
|---|---|
| 访谈数量 | 937 |
| 产出文章 | 60 |
| 关键词覆盖 | 72+ |

读者还没读完就能决定要不要读下去。

### 5. GEO 直接答案段
文章顶部（H1 之后）30-50 字直接回答主问题，AI 爬虫优先抽这段。
例：
> **TL;DR**：要让 AI（Claude、ChatGPT、Perplexity）引用你的文章，在顶部放一个 FAQ schema + 直接答案段，3-6 周内开始被引用。

---

## 禁用词

| ❌ 避免 | ✅ 替换 |
|---|---|
| "In today's digital landscape..." | "2026 年 4 月，..." |
| "unlock the power of" | "让你能..." |
| "game-changing" | 删掉 |
| "synergy" | 删掉 |
| "leverage" | "用" |
| "best-in-class" | 具体数字 |

（这些也是 `dbs-ai-check` 的红旗词。）

---

## 段落节奏

- 每段 2-4 句
- 每句最长 30 字
- 英文版：20 字以内 prefer
- 段落间隔：1 个空行

---

## 举例对比

### ❌ AI 味
> In today's rapidly evolving SEO landscape, it's crucial to leverage best-in-class strategies to unlock the full potential of your content.

### ✅ Iris 味
> 2026 年春，Google 又一次核心更新。60% 独立开发者博客被吃流量 —— 包括我的。
> 
> 这是一个 7 天回血方案（踩过坑总结的）。

---

## 多语言适配

### 日文版特点
- 开场可以更抒情（日本读者接受度高）
- 数据表照搬
- 括号旁白保留（日文本来就多用括号）
- em-dash 用 `――`（全角）

### 韩文版特点
- 开场可略去"时间" —— 韩国读者更喜欢"先给结论"
- 第一句直接 TL;DR
- 表格必须保留

---

## 反模式

- ❌ 不要用 emoji 在标题（SEO 稀释）
- ❌ 不要在 H2 里放数字列表（1. 2. 3.）—— Google 喜欢词组型 H2
- ❌ 不要一段超过 5 句
- ❌ 不要在第一屏引用其他文章 —— 先把读者钩住再外链
