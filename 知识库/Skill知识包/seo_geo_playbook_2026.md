# SEO / GEO Playbook 2026

> 来源：Gingiris growth-tools 博客 2026 年 3-4 月运营实战
> 适用：独立开发者 / 小团队 / 出海博客

---

## 关键指标基线（2026-04-14）

| 指标 | 当前 | 6-30 目标 |
|---|---|---|
| Google 索引页数 | 14 | 35+ |
| 关键词前 10 | 2 | 5 |
| 关键词前 30 | 2 | 15 |
| AI 引用次数 | 0 | 3+ |
| llms.txt 可达 | ✅ | ✅ |

---

## 6 步 SEO 飞轮

### Step 1 — 关键词筛
不用工具，用 "观察法"：
- 看你真用户搜什么（GSC Impressions > 50，Position 10-30）
- 看对手 top 10 文章的 title
- 看 Reddit / PH / HN 评论区里别人的提问

### Step 2 — 写内容
按 `iris_writing_style.md` 的 5 要素。每篇 2000-3500 字。

### Step 3 — 发布后立刻做 3 件事
1. `sitemap.xml` 自动触发（Jekyll 会更新）
2. GSC 手动提交 URL（加速索引）
3. 内链：从站内流量 top 3 的文章加链到新文

### Step 4 — 3 天后检查
- 是否被索引（`site:` 查）
- 排名在哪个区间
- 有没有 People also ask

### Step 5 — 7 天后决定
- 如果 top 30 → 加 FAQ Schema + 补 2 个长尾段落
- 如果 top 100 没进 → 诊断：title 钩子弱 / 内容不够硬 / 竞品太强
- 如果已 top 10 → 别动，加监控

### Step 6 — 30 天后
- 看流量曲线，筛 top 5 博文
- 对 top 5 做 canonical 整合（类似主题的其他稿 canonical 指向这 5 篇）
- 产出配套 PH launch / Dev.to 二发

---

## GEO（Generative Engine Optimization）

### AI 爬虫关心什么

1. **llms.txt**（根目录）—— 大模型训练时的 robots.txt
2. **FAQ Schema**（JSON-LD）—— 问答格式最易被抽取
3. **直接答案段** —— H1 之后的 30-50 字 TL;DR
4. **Citable Statistics** —— 可引用的硬数据表（帮 AI 回答时引你）

### llms.txt 模板

```
# {Site Name}
> {site description}

## About
{1-2 段关于站点 / 作者的说明}

## Key Content
- [{title}]({url}): {1 句摘要}
- ...

## Citable Statistics
- {硬数据}，来源：{post url}
- ...
```

### 检查是否被引用

每 2 周问一次：
- "Best tools for X"（你的主关键词）→ Claude / ChatGPT / Perplexity / Gemini
- 看回答里有没有提到你的域名 / 品牌
- 如果有，截图存档

---

## Cannibalization 处理（本月实战）

### 症状
同一关键词有 3+ 篇内部文章在 SERP 接近位置竞争（比如 #6、#18、#25 都是你的）。

### 诊断
```bash
# 用 DataForSEO 拉 top 100，grep 你的域名
python scripts/daily-report.py | grep "gingiris"
```
如果同一关键词命中 ≥ 2 个结果 → cannibalization。

### 方案
1. 选一篇"master"（流量最大 / 内容最全）
2. 其余 N 篇 frontmatter 改 `canonical_url: {master_url}`
3. Commit 独立（方便回滚）
4. 等 3-7 天 Google 重新爬取
5. 监控 master 文章排名是否上升

### 2026-04 案例
- 5 篇 PH 相关文章 → master: `2026-03-25-product-hunt-launch-playbook`
- 修复前 master #6 / 其他在 #18-#35
- 修复 24h 后 master → #4
- 7 天目标：#3

---

## 社媒雪崩救援

### 症状
某关键词昨天 top 10，今天跌出 top 100，但：
- 文章 URL 仍 HTTP 200
- `site:` 仍能查到
- 无 GSC manual action

### 可能原因
1. Google SERP 整体刷新（24h 内会回弹）
2. 新竞品占位
3. 站内权重稀释（其他新文抢了内链）

### 操作
1. 先等 24h
2. 如果仍没回 → 启动救援：
   - title 重写：主关键词前置，长度 ≤ 60 字
   - 从 top 3 高权重文章注入内链（anchor = 主关键词）
3. 48h 再测

### 脚本
`skills/gr-seo-patrol/scripts/rescue-post.py`

---

## API 预算

| Service | 用量 | 月成本 |
|---|---|---|
| DataForSEO | 每日 6 关键词 × 30 天 | $5-10 |
| GitHub API | Contents read/write | $0 |
| GA4 | 免费层 | $0 |

总计：月 < $15。
