---
name: skillspector-wrapper
description: [system] SkillSpector security scanner - USE before installing new skill. DO scan 64 vulnerability patterns. NOT for regular use. Triggers: scan skill/security check/is it safe
---

# SkillSpector 安全扫描

NVIDIA 出品的 AI Agent Skill 安全扫描器（9k⭐）。

## 功能
- 扫描 SKILL.md 或整个 skill 目录
- 检测 64 种漏洞模式，16 个类别
- 打分 0-100，给出安全建议
- 支持终端/JSON/Markdown/SARIF 输出

## 使用方式
```bash
skillspector scan ./my-skill/
skillspector scan ./SKILL.md --no-llm
skillspector scan ./my-skill/ --format json --output report.json
```

## 在 onboarder 中的位置
每次装新 skill 前先跑：
1. skillspector scan → 安全检查
2. 确认安全 → 继续安装
3. 发现高风险 → 拒绝安装并报告

## 安装状态
已通过 pip 安装，路径：Python312\Scripts\skillspector.exe
