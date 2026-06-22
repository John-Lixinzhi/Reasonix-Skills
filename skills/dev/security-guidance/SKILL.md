---
name: security-guidance
description: [研发] 安全审查 — USE when 审核代码安全性/找漏洞/安全合规检查。DO 3层防护：模式警告→LLM审查→跨文件追踪。NOT for 常规代码审查（用superpowers-review）。Triggers: 安全检查/漏洞/渗透/安全审查/找风险
---

# Security Guidance — 安全审查

3 层安全防护体系，用于审查 AI 生成的代码。

## 三层防护
1. **模式警告** — 即时正则检查 25+ 危险模式（yaml.load、pickle.load、innerHTML、硬编码密钥等）
2. **LLM diff 审查** — 每次修改后发送 diff 给大模型做安全审查，高严重度问题自动修复
3. **Agentic 提交审查** — git commit 时跨文件追踪数据流，捕获多文件漏洞（IDOR、认证绕过、跨文件 SSRF）

## 覆盖范围
- SQL/命令注入
- XSS/CSRF
- SSRF
- 硬编码密钥/凭据
- IDOR/权限绕过
- 不安全反序列化
- 路径遍历
- 敏感数据泄露

## 工作流
1. 先跑 `/superpowers-review` 做常规代码审查
2. 再跑本 skill 做安全专项审查
3. 按严重度分级：Critical / High / Medium / Low
4. Critical 和 High 必须修复才能继续
