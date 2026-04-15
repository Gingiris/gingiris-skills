# 原子库

> 灵感来自 dbskill `知识库/原子库/atoms.jsonl`

每一条是从 Gingiris 运营实战（发文、投流、访谈、对手复盘）里提炼的一条可复用知识点。

## 字段说明

```json
{
  "id": "2026Q2_001",
  "knowledge": "canonical 合并后 3-7 天排名才反应，不要当天就判失败",
  "source": "https://github.com/Gingiris/growth-tools",
  "date": "2026-04-14",
  "topics": ["seo", "canonical"],
  "skills": ["gr-seo-patrol", "gr-blog-post"],
  "type": "lesson",
  "confidence": "high"
}
```

## 字段

| 字段 | 说明 |
|---|---|
| `id` | `{YYYYQx}_{NNN}` 季度 + 编号 |
| `knowledge` | 提炼后的 1 句话 |
| `source` | 原始来源 URL（博客、截图、访谈） |
| `topics` | seo / geo / ph / oss / aso / blog / b2b / i18n |
| `skills` | 关联的 gr-* skill |
| `type` | `principle` / `method` / `lesson` / `anti-pattern` / `case` |
| `confidence` | `high` / `medium` / `low` |

## 使用方式

1. **给 AI 做 RAG**：`atoms.jsonl` 导向量库
2. **给 Skill 运行时参考**：运行 `gr-*` 时按 skill 过滤
3. **给人读**：过滤 `topics` 或 `type` 自己翻

---

## 增量规则

每周一 `weekly-growth-tools-update` scheduled task 自动从上周的运营日志提炼 3-10 条新原子，PR 到 `atoms.jsonl`。
