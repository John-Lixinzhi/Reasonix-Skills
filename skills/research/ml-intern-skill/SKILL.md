---
name: ml-intern-skill
description: [research] ML Intern - USE when need to read papers/train ML models/do experiments. DO auto research, code, train, deploy. NOT for non-ML tasks. Triggers: read paper/train model/ML experiment
---

# ML Intern — 自治 ML 工程师

来源：huggingface/ml-intern (10.5k⭐)

一个自治的 ML 工程师，能读论文、写代码、训练模型、部署到 HuggingFace Hub。

## 核心能力
- 读论文并复现
- 搜索 HuggingFace 模型库/数据集
- 写训练脚本、调超参
- 创建 HF Spaces 做演示
- 自动上传 trace 到 HF 数据集

## 使用方式
```bash
ml-intern "fine-tune llama on my dataset"
ml-intern --model openai/gpt-5.5:fal-ai "your prompt"
```

## 关键设计（可借鉴）
- **Doom Loop 检测**：检测AI是否陷入重复调用工具的循环，自动纠正
- **自动压缩**：上下文超过170k tokens时自动压缩
- **审批门禁**：敏感操作（运行代码、写文件）需要用户确认

## 对我生态的价值
- doom loop 检测机制可以融入我的 skill 体系
- 参考它的 ToolRouter 设计优化我的 MCP 调度
