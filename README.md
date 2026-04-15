# gingiris-skills

Iris / Gingiris 的出海增长工具箱 —— 把 6 个 gingiris-* playbook repo + 每日运营脚本 + 60 篇博客实战经验，打包成 Claude Code skills。

**作者**：[Iris](https://x.com/iris__wei) · [Gingiris 博客](https://gingiris.github.io/growth-tools/)

**所有内容开放**，可以整套装，也可以只拿一部分。Skill、知识包、原子库、单个脚本都能单独用。

---

## 工具箱（MVP 0.1.0）

| Skill | 做什么 |
|---|---|
| `/gr` | 主入口，根据你的问题自动路由 |
| `/gr-seo-patrol` | 每日 SEO/GEO 巡逻 — SERP 追踪、canonical 修复、社媒雪崩救援 |
| `/gr-blog-post` | Jekyll 博客发布 — Iris 文风 + hreflang 中英日韩 + FAQ Schema |
| `/gr-ph-launch` | Product Hunt 发布剧本 — 30x 日冠经验 |

### Roadmap（0.2-0.3）

| Skill | 来源 |
|---|---|
| `/gr-oss-marketing` | 从 `Gingiris/gingiris-opensource` 提炼 |
| `/gr-b2b-growth` | 从 `Gingiris/gingiris-b2b-growth` 提炼 |
| `/gr-aso` | 从 `Gingiris/gingiris-aso-growth` 提炼 |
| `/gr-user-interview` | 从 `Gingiris/gingiris-user-interview` 提炼 |
| `/gr-competitor` | 包装 `Gingiris/Competitor-analysis-tool` |
| `/gr-ph-comment` | 包装 `Gingiris/ph-comment-generator` |
| `/gr-gh-outreach` | 包装 `Gingiris/github-issue-generator` |

---

## 工作流

```
gr-competitor（看对手在做啥）
    ↓
gr-ph-launch / gr-oss-marketing / gr-b2b（选打法）
    ↓
gr-blog-post（产内容）
    ↓
gr-seo-patrol（上线后监控）
    ↓ cannibalization           ↓ 雪崩
gr-seo-patrol canonical-fix   gr-seo-patrol rescue
    ↓
gr-user-interview（用户反馈）
```

Skill 之间会自动推荐下一步。比如：
- `gr-ph-launch` 发布 24h 后 → 推荐 `gr-seo-patrol` 加监控
- `gr-seo-patrol` 发现 cannibalization → 自动跳到 canonical 修复流程
- `gr-blog-post` 发布后 → 自动加入 `gr-seo-patrol` 监控名单

---

## 安装

**推荐：Claude Code 插件市场**

```bash
claude plugin marketplace add Gingiris/gingiris-skills
claude plugin install gr@gingiris-skills
```

装完在 Claude Code 里输入 `/gr` 即可。

**单独装某个 skill**：

```bash
claude plugin install gr-seo-patrol@gingiris-skills
```

---

## 知识库

所有方法论文档与原子知识点都开放，即使不装 skill 也能用。

### 目录结构

```
知识库/
├── 原子库/
│   ├── atoms.jsonl                    # 结构化知识原子（可 RAG）
│   └── README.md
└── Skill知识包/
    ├── iris_writing_style.md          # 文风指南（5 要素）
    └── seo_geo_playbook_2026.md       # SEO 飞轮 + GEO 三件套
```

### 怎么在你自己的项目里用

**场景 1：给你的 AI 加 SEO 诊断能力**
把 `知识库/Skill知识包/seo_geo_playbook_2026.md` 粘到 system prompt。

**场景 2：做 RAG**
`atoms.jsonl` 导向量库，每条带 `topics` 标签。

**场景 3：只要脚本**
`skills/gr-seo-patrol/scripts/*.py` 可独立跑，看 `docs/api-keys-template.md` 配 env。

---

## API 依赖

见 [`docs/api-keys-template.md`](docs/api-keys-template.md)。

核心：`DATAFORSEO_B64` + `GITHUB_TOKEN`，其他 skill 按需加。

---

## 许可证

MIT。

- 个人使用、学习、研究：随便
- 商业用途：随便
- 衍生作品：建议（不强制）注明来源

---

## 关联 repo

- [Gingiris/growth-tools](https://github.com/Gingiris/growth-tools) — 主 blog，所有 skill 的实战场
- [Gingiris/gingiris-launch](https://github.com/Gingiris/gingiris-launch) — PH launch playbook 内容源
- [Gingiris/awesome-agent-skills](https://github.com/Gingiris/awesome-agent-skills) — skills 生态索引
- [dontbesilent2025/dbskill](https://github.com/dontbesilent2025/dbskill) — 框架灵感来源

---

## 贡献

- 发 Issue 描述你的运营场景
- PR 加新 skill / 新原子 / 新方法论
- 跟 [@iris__wei](https://x.com/iris__wei) 聊
