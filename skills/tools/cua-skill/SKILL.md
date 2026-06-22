---
name: cua-skill
description: [工具] CUA电脑操控 — 触发条件：需要控制电脑桌面/自动化操作软件/模拟鼠标键盘时。开源计算机使用Agent基础设施。支持后台操控macOS/Windows/Linux桌面，不抢光标不抢焦点。自带MCP服务器可接入
---

# CUA — 计算机使用 Agent

来源：trycua/cua (18.6k⭐)

让 AI 能操控电脑桌面的基础设施——点鼠标、敲键盘、截图、运行命令。

## 核心组件
- **cua-driver**：后台桌面驱动（macOS/Windows/Linux），不抢光标不抢焦点
- **cua-sandbox**：沙箱环境 SDK，创建隔离的虚拟机/容器
- **cua-bench**：基准测试和强化学习环境
- **Lume**：macOS 虚拟机管理（Apple Silicon）

## 接入方式
```bash
# Windows 安装
irm https://raw.githubusercontent.com/trycua/cua/main/libs/cua-driver/scripts/install.ps1 | iex

# 接入 Claude Code 作为 MCP
claude mcp add --transport stdio cua-driver -- cua-driver mcp
```

## 对我生态的价值
- 如果接入，我可以直接操作你的电脑桌面
- 打开软件、点击按钮、截图验证、跨应用操作
- 配合 Scrapling 的截图功能可以实现完整的视觉闭环
