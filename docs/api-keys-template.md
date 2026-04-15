# API Keys 模板

> ⚠️ 真实 key **不要** commit 到这个 repo。用 env var 或 `.env.local`（已 gitignore）。

## 必需

```bash
# SEO / SERP
export DATAFORSEO_B64="<basic-auth-b64>"   # iris.wei@gingiris.com:xxxx 的 base64

# GitHub 读写
export GITHUB_TOKEN="<ghp_xxx>"             # repo scope

# 默认仓库（可覆盖）
export GR_REPO="Gingiris/growth-tools"
export GR_SITE="gingiris.github.io/growth-tools"
export GR_GA4_ID="G-XXXXXXXXX"
```

## 可选（特定 skill 用）

```bash
# 内容发布
export DEV_TO_API_KEY="<xxx>"               # dev.to cross-post
export DEEPSEEK_API_KEY="<sk-xxx>"          # 翻译（日/韩）
export TEAMOROUTER_API_KEY="<sk-xxx>"       # 多模型路由

# 数据分析
export SERPAPI_KEY="<xxx>"
export BRAVE_SEARCH_API_KEY="<xxx>"
export APIFY_API_TOKEN="<apify_xxx>"

# 商业化
export POLAR_ACCESS_TOKEN="<polar_xxx>"     # 订阅变现
```

## Railway env vars

所有 Railway 项目的 env var 与本地一致。
新 skill 依赖新 key 时：
1. 本地 `.env.local` 加
2. Railway dashboard 加
3. 这份 template 加（名字，**不要加值**）

## 验证

```bash
python skills/gr-seo-patrol/scripts/daily-report.py 2>&1 | head -20
# 应看到 [serp] <keyword> ... 而不是 DATAFORSEO_B64 missing
```
