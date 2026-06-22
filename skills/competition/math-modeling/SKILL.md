---
name: math-modeling
description: [competition] Math modeling - USE when participating in math competition/need modeling. DO model selection, code, paper. NOT for daily analysis. Triggers: math modeling/competition/model building/regression
---

# 数学建模竞赛

覆盖国赛/美赛/华为杯/电工杯/Mathorcup等主流赛事。

## 一、模型分类速查

### 预测模型
- **回归分析**：线性/多元/Logistic回归
- **XGBoost**：极端梯度提升树，分类 + 回归 + 特征重要性分析
- **灰色预测 GM(1,1)**：小样本数据预测
- **时间序列**：AR/MA/ARIMA/LSTM
- **微分方程**：ODE/SDE/PDE 动态建模
- **马尔可夫预测**：状态转移预测
- **支持向量机回归（SVR）**：小样本非线性预测

### 评价模型
- **层次分析法 AHP**：主观赋权
- **熵权法**：客观赋权
- **TOPSIS**：逼近理想解排序
- **模糊综合评价**：多因素模糊评判
- **主成分分析 PCA**：降维+综合评价
- **数据包络分析 DEA**：效率评价
- **秩和比法 RSR**：统计评价

### 优化模型
- **线性/整数/非线性规划**：基础优化
- **遗传算法**：全局搜索优化
- **粒子群算法 PSO**：群体智能优化
- **模拟退火**：TSP/背包问题
- **多目标规划**：分层序列法/Pareto最优
- **动态规划**：多阶段决策
- **图论模型**：最短路径(Dijkstra/Floyd)/最小生成树/最大流

### 分类模型
- **SVM**：最优超平面分类
- **随机森林**：集成学习分类
- **XGBoost/LightGBM**：梯度提升分类
- **KNN**：最近邻分类
- **朴素贝叶斯**：概率分类
- **神经网络**：深度学习分类

## 二、Python 通用代码模板

### XGBoost 分类
```python
import pandas as pd
from sklearn.model_selection import train_test_split
from xgboost import XGBClassifier
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix

data = pd.read_excel("data.xlsx")
X = data.drop(columns=["label"])
y = data["label"]
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42, stratify=y)
model = XGBClassifier(n_estimators=100, max_depth=3, learning_rate=0.1, subsample=0.8, colsample_bytree=0.8, eval_metric="logloss")
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
print(accuracy_score(y_test, y_pred))
```

### XGBoost 回归
```python
from xgboost import XGBRegressor
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
model = XGBRegressor(n_estimators=200, max_depth=3, learning_rate=0.05)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

## 三、论文写作要点
- 结构：摘要→问题重述→模型假设→符号说明→模型建立→求解→结果分析→优缺点
- 摘要最重要！评审先看摘要
- LaTeX 模板：国赛/美赛各有专用模板
- 图表清晰，公式规范

## 四、常用软件
- MATLAB / Python + Jupyter
- SPSS / Stata 统计
- Lingo / Gurobi 优化求解
- LaTeX / Word 排版
- Visio / Origin / AxGlyph 绘图

## 五、参考资料
- GitHub 宝藏库：personqianduixue/Math_Model (4.6k⭐)
  - 包含国赛/美赛/研赛论文、算法代码、LaTeX模板、书籍100+本
