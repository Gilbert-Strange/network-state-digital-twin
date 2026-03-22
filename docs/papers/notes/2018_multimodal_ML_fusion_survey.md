
# Paper Notes

Title:
Multimodal Machine Learning: A Survey and Taxonomy

Year:
2018

---

## Goal

阐述当下的多模态情况下的机器学习

---

## Main Categories

当下多模态情况下的机器学习有五个难点：
- Representation 表示数据（eg:象征or信号）
- Translation 翻译数据到其它模态
- Alignment 对齐找关系
- Fusion
- Co-learning 一个模态的学习怎么帮到另一个

---

## Focus Section

Fusion

---

## Methods / Taxonomy

### Model-agnostic
- Early: 开始就拼接融合然后放进模型（难有好模型）
- Late: 先各自训练完之后融合
- Hybrid: 先从low-level每个part训练，之后交互数据融合，学到新东西再去别的level训练，之后再交换

### Model-based
- Kernel-based: MKL: 对齐和融合一块干了,但支持向量算法导致内存和训练时间长，强依赖数据
- Graphical models: 找关系概率云关系，但太靠经验需要灵光一现
- Neural networks: RNN, MV-LSTM等，大数据学习，性能好，十分流行，缺点是解释性差和依赖大量数据


---

## Key Insights

算力支持直接上神经网络，算力不支持或数据太小或需要解释性只能自主融合，感觉图模型有点抽象，以后再看，多核向量感觉也不错

---

