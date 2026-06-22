---
name: skillopt-wrapper
description: [system] SkillOpt skill optimizer - USE when need to auto-improve skills. DO trajectory-driven edits, validation-gated updates. NOT for writing new skills. Triggers: optimize skill/improve quality/skill training
---

# SkillOpt 技能优化

微软研究院出品（8.6k⭐），像训练神经网络一样自动优化 skill 文本。

## 核心能力
- 把 skill 文档当作"可训练参数"
- optimizer 模型自动加/删/改 skill 内容
- 验证门控：只有严格提升才采纳
- 产出 compact best_skill.md（300-2000 tokens）

## 使用方式
```bash
skillopt-train --config configs/my_config.yaml
skillopt-eval --skill best_skill.md --benchmark my_benchmark
```

## 效果
- 6个基准测试52个实验全部最优
- GPT-5.5准确率提升 +23.5分
- 跨模型/跨平台迁移有效

## 安装状态
已通过 pip install skillopt 安装
需要配置 LLM API 密钥才能使用训练功能
