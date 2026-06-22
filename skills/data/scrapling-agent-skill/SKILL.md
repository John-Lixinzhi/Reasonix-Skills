---
name: scrapling-agent-skill
description: [data] Scrapling web scraping - USE when need to scrape data/web_fetch fails/Cloudflare bypass. DO get/fetch/stealthy_fetch via MCP. NOT for simple API calls. Triggers: scrape/crawl/extract/cloudflare bypass
---

# Scrapling 官方 Agent Skill

Scrapling 是一个自适应 Web Scraping 框架，处理从单次请求到全量爬取的一切需求。

**要求：Python 3.10+ | pip install "scrapling[all]>=0.4.9"**

## 快速判断用哪个工具

| 场景 | 用啥 |
|------|------|
| 静态页面，无反爬 | `get` — 最快，HTTP 请求 |
| 多个静态页面 | `bulk_get` — 并发 |
| JS 渲染/SPA 页面 | `fetch` — Playwright 浏览器 |
| Cloudflare/强反爬 | `stealthy_fetch` — 隐身 + 指纹伪装 |
| 批量带反爬页面 | `bulk_stealthy_fetch` |
| 同一站点多个页面 | `open_session` + session_id 复用 |
| 截图 | `open_session` + `screenshot` |

**原则：** 从 `get` 开始，被拦截了升到 `fetch`，再有 Cloudflare 就上 `stealthy_fetch`

## CLI 用法

`scrapling extract` 命令组：

```
scrapling extract get/put/post/delete/fetch/stealthy-fetch <url> <output>
```

输出格式由扩展名决定：`.md`=Markdown、`.html`=HTML、`.txt`=纯文本

关键参数：`--css-selector` 缩小内容省 tokens、`--solve-cloudflare` 过 CF、`--ai-targeted` 防注入、`--proxy` 代理

## MCP 工具（Reasonix 直接用）

我已对接好 Scrapling MCP 服务器，10 个工具可用：

- `get` / `bulk_get` — HTTP 请求（支持 TLS 指纹模拟、HTTP/3）
- `fetch` / `bulk_fetch` — 浏览器渲染（Playwright）
- `stealthy_fetch` / `bulk_stealthy_fetch` — 隐身模式（过 Cloudflare Turnstile）
- `open_session` / `close_session` / `list_sessions` — 会话管理
- `screenshot` — 页面截图

省 tokens 技巧：`css_selector` 参数提前筛选、`extraction_type="markdown"` 默认最省、`main_content_only=true` 去导航栏

## 安全规范
- 只爬有权限访问的内容
- 遵守 robots.txt（爬虫用 `robots_txt_obey=True`）
- 大爬虫加 `download_delay`
- 不爬敏感数据、不绕过付费墙
