---
name: gr-blog-post
description: >
  Jekyll 博客发布流水线：按 Iris 文风（时间锚定开场、括号旁白、em-dash 转折、Key Stats 表格）生成文章，
  附带 frontmatter（title / date / canonical_url / hreflang_ja / hreflang_ko / FAQ schema）、
  多语言同步（en/ja/ko）、自动建内链。当用户说"写一篇博客"、"发新文章"、"同步日韩版本"时调用。
metadata:
  author: Iris / Gingiris
  version: "0.1.0"
---

# gr-blog-post — Jekyll 博客发布

## 产出的文章必须符合

### Iris 文风 5 要素（详见 `知识库/Skill知识包/iris_writing_style.md`）

1. **时间锚定开场** —— 不说"SEO 很重要"，说"2026-04-10，凌晨 3 点，后台流量归零"
2. **括号旁白** —— 正文一句，括号里挤私货（"...—— 别问怎么知道的"）
3. **em-dash 转折** —— 不用"但是"，用 `——`
4. **Key Stats 表格** —— 文章开头或 H2 下第一屏放一个硬数据表，3-5 行
5. **GEO 直接答案段落** —— 文章顶部一段 30-50 字直接回答主问题，方便 AI 爬虫抽取

### 技术 frontmatter 模板

```yaml
---
layout: post
title: "主关键词前置，副标题用冒号：不超过 60 字"
date: 2026-04-15 14:30:00 +0800
categories: [seo, growth]
tags: [...]
canonical_url: https://gingiris.github.io/growth-tools/blog/2026/04/15/slug/
hreflang_ja: /blog/2026/04/15/slug-ja/
hreflang_ko: /blog/2026/04/15/slug-ko/
description: "150-160 字 meta description，含主关键词"
faq:
  - q: "直接问句"
    a: "30-50 字硬答案"
---
```

---

## 发布流程

### 1. 选题
- 读 `gr-seo-patrol` 输出，找"top 30 但没 top 10"的关键词
- 或读 `gr-competitor`，找对手新打法
- ❌ 不做重复主题（先 `site:` 查站内是否已有）

### 2. 写初稿
- 时间锚定开场（当前日期 + 具体场景）
- 第一屏：GEO 直接答案段（30-50 字）+ Key Stats 表（硬数据）
- H2 结构：问题 → 框架 → 案例 → 陷阱 → 下一步
- 每个 H2 下 200-400 字，不超过 600 字

### 3. 内链
- 向前：链接 2-3 篇已发布的同主题文章（用主关键词作 anchor）
- 向后：站内 index / hub 页
- 权重传导：从流量最大的 3 篇文章加内链到新文

### 4. FAQ Schema
- 3-5 个问答
- 问句必须是用户真实搜索句（从 GSC / People also ask 抓）
- 答案硬、短、可引用

### 5. Canonical 策略
- **默认 self-canonical**
- 如果是同主题系列的分篇 → canonical 指向 master
- ja/ko 翻译版 → 自身 canonical + hreflang 互指

### 6. 多语言同步
- 用 `scripts/sync-i18n.py`（roadmap）从英文自动产日韩草稿
- 人工过一遍（机翻硬伤 + 文化适配）
- 日韩版本独立 slug，不复用英文 slug

### 7. 发布
- GitHub Contents API PUT（不要 `git push`）
- Commit message: `post: {slug} ({lang})`

### 8. 发布后 24h
- 加入 `gr-seo-patrol` 监控名单
- Google Search Console 手动提交
- 社交平台分发（推特 / LinkedIn / dev.to）

---

## 反模式

- ❌ 不要用 AI 味重的模板（"In today's digital landscape..."）—— 过不了 `dbs-ai-check`
- ❌ 不要 H1 堆关键词
- ❌ 不要忘记 hreflang —— 已发布的旧文补翻译时要回改原文 frontmatter
- ❌ 不要同一关键词发 3 篇 —— cannibalization 立刻找上门

---

## 级联推荐

- 写完 → `gr-seo-patrol` 加监控
- 发现是系列稿 → `gr-blog-post` 继续产第 2 篇并设 canonical
- 英文发完 24h → 手动触发日韩翻译

---

## API 依赖

| Service | Env var |
|---|---|
| GitHub PAT | `GITHUB_TOKEN` |
| DeepSeek / Teamo（翻译） | `DEEPSEEK_API_KEY` / `TEAMOROUTER_API_KEY` |
