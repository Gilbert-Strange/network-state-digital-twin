# Artificial intelligence advances in anomaly detection for telecom networks (Survey)

## 1. This paper is about
- 人工智能去做异常检测

## 2. Scope & positioning
- 覆盖哪些 anomaly detection 场景
- 偏 telecom / network / traffic

## 3. How the field is structured
### Supervised: 
 - SVM
 - Decision trees
 - Random forests
  **缺点：** 获取标签数据难且时间长

### Unsupervised：
 - **Center-based:**
   - k-means算法(距离判断离群值)
 - **Density-Based:**
   - Density-Based算法(是否合群判断离群值)
 - **Distance-based:**
   - k-Nearest Neighbors算法(KNN)(计算到k个最近点距离)
   - Local Outlier Factor算法(LOF)(比较自己局部密度和邻居密度)
 - **Dimensionality Reduction-based：**
   -  Principal Component Analysis(PCA)(找主成分投影)
   - t-distributed Stochastic Neighbor Embedding(t-SNE)(高维直接降到二维保持临近关系)
### Semi-supervised

## 4. Evaluation of AI techniques
- 传统方式如KNN,iforest,PCA可以简便地在低纬度结构化数据探测
- 高纬度大量数据可用如PCA来降维处理
- 对于线性时序数据,RNN和LSTM，自动解码器比较好，缺点是昂贵和长时，对超参数敏感故需要较精确的调优
- 
## 5. What I should take from this paper
- 对我现在项目最有用的是什么
- 哪些关键词/方向值得后续深挖
