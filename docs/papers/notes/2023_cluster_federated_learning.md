# Paper Notes

Title:
Clustered federated learning architecture for network anomaly detection in large scale heterogeneous IoT networks

Year:
2023

---

## Problem

解决当下异常检测中
- 传统异常检测要上传云端导致隐私和网络负担问题以及分块会导致孤岛问题 -- 用FL
- 传统FL面对极度异构网络导致的无法收敛问题 -- 在之前用聚类算法
- 聚类需要人工事先实现问题 -- 将无监督聚类完整融入FL流程

---

## Data / Input

- FL训练数据
- 正常运行数据和元数据

---

## Method

作者使用的方法：

clustered federated learning

主要结构：

client nodes
cluster heads
global aggregation

---

## Output

模型输出什么？

异常检测模型

---

## Key Idea

利用聚类算法加FL来消除隐私安全，数据传输问题，数据孤岛问题以及无法收敛问题

---

## Useful for My Project


federated architecture 可以用于分布式网络监控
数据融合可以交给无监督学习来做不一定必需自己设计向量，先无监督分组之后灰狼优化，随机森林等，但是实际特征工程提供好特证还是很重要

## Doubt

Method: How to choose features  
缺点：在这之前必须得有目标，可是攻击会更新，不可能有已经定好的目标  
解决（吗？）：先无监督聚类分组，然后灰狼优化目标设置为最能区分这一组和其他组的特征，之后利用训练好组识别异常，而其实如果要识别异常的话按照训练只能是已知攻击原则，可能训练随机森林决策权重只能在于已知攻击，万一新攻击对应权重大不相同就会废掉，一个想法就是只管正常，非正常都是异常，但是问题是聚合的时候单个部分是异常重不重要又是变成了从已知危险训练了