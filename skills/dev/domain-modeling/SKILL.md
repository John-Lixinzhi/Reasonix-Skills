---
name: domain-modeling
description: [dev] Domain modeling - USE when project terminology unclear/AI-user language mismatch. DO build shared glossary, challenge term consistency. NOT for implementation. Triggers: terminology/domain model/glossary/shared language
---

# 领域建模 (Domain Modeling)

来源：mattpocock/skills (140k⭐)

通过建立项目共享语言，让AI和人类说同一种话，大幅减少沟通成本和token浪费。

## 工作方式
1. 主动识别项目中使用的关键术语和概念
2. 挑战术语一致性——同一个意思是不是用了不同词？
3. 构建领域词汇表（Glossary）
4. 用边界场景压力测试术语
5. 更新 CONTEXT.md 和 ADR 文档

## 为什么有效
- 没有共享语言时，AI用20个词说1个意思
- 有共享语言后，变量/函数/文件命名一致
- 代码库更易导航
- 每次会话节省大量token

## 触发场景
- 项目刚启动，术语还没定义
- 发现AI和用户对同一个词理解不同
- 代码中出现多个同义词表达同一个概念
