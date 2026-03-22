# Paper Notes

Title:
Deep Multimodal Data Fusion

Year:
2024

---

## Goal

阐述当下利用人工智能进行深度多模态融合的方法分类，人工智能已深刻改变了数据融合的步骤边界，故而需重新提出分类

---

## Main Categories

根据当前主流情况，深度融合算法可分为五类：
- Encoder-Decoder methods
- Attention Mechanism methods
- Graph Neural Network methods
- Generative Neural Network methods
- Other Constraint-based method

---

## Focus Section

All

---

## Methods / Taxonomy

### Encoder-Decoder methods
- Raw-data-level Fusion 原始数据放一起送编码器里面
- Hierarchical Feature Fusion 一边编码一边融合
- Decision-level Fusion 最后融合
- 自动编码器

### Attention Mechanism methods（自动分配权重）
- Intra-modality Self-attention 自管自最后合
- Inter-modality Cross-attention 互相有影响
- Transformer-based Methods

### Graph Neural Network methods(擅长找关系，显式)
- Representation Learning for Individual Modalities
- Representation Learning for the Fused Data

### Generative Neural Network methods（可防过拟合，但关系隐式）

### Other Constraint-based method
- Coordinated representation architecture 分别解码但是加约束诸如对齐，不同于前面的关系在概率，这里是直接对齐
- Tensor fusion mechanism 张量，全部相乘组成高维信息（有点像叉乘，诸如三个向量乘扩出一个三维空间然后就可以找关系）

### 表格1：A Comparison among the Five Categories of Fusion Methods

| 方法                                 | 泛化能力（模态数量 ≥ 3，Easy, Medium, Hard）                                |
| ---------------------------------- | ---------------------------------------------------------------- |
| **Encoder-Decoder-based Methods**  | Easy。易于为新组件添加子分支。                                                |
| **GenNN-based Methods**            | Hard。添加新模态通常需要集成额外的生成组件。平衡和训练包含多个此类组件的网络会变得越来越复杂且计算量巨大。          |
| **Attention-based Methods**        | Easy。无论输入模态数量多少，都易于采用此类方法探索多模态间的模态内与模态间关系。                       |
| **GNN-based Methods**              | Medium。添加一个新模态将导致图结构数据的重构，网络的聚合函数也可能需要修改。                        |
| **Other Constraint-based Methods** | Hard。易于为新模态添加子分支，以学习各模态分离但协调的表示。子网络的权重无法共享，因此计算成本会随着子分支的增加而急剧上升。 |

### 表格2：A Quantitative Comparison among the Fusion Methods（特定任务分别得分）

| Tasks | Dataset | Encoder-Decoder | Attention Mechanism | Graph Networks | Generative Networks |
|-------|---------|-----------------|---------------------|----------------|---------------------|
| Referring Image Segmentation | ReferIt [80] | IoU: 52.81 [119]−63.63 [98] | IoU: 63.80 [211]−72.97 [104] | IoU: 65.53 [67] | IoU: 60.31 [143] |
| Video Captioning | YouCookII [242] | METEOR: 19.91 [117]<br>BLEU-4: 11.43 [117] | METEOR: 18.23 [138]−27.09 [155]<br>BLEU-4: 9.82 [138]−21.88 [155] | METEOR: 21.77 [74]−22.1 [54]<br>BLEU-4: 11.74 [74]−14.0 [54] | METEOR: 19.77 [225]<br>BLEU-4: 12.14 [225] |
| Visual Question Answering | VQA 2.0 [53] | ACC: 68.14 [125] | ACC: 67.34 [156]−71.94 [157] | ACC: 65.89 [132]−71.29 [205] | ACC: 57.87− [25] |
| Object Recognition | SUN RGB-D [164] | ACC: 54.60 [240]<br>mIoU: 42.8 [240]−50.7 [64] | ACC: 60.8 [236]−61.4 [238]<br>mIoU: 47.8 [236]−51.8 [238] | ACC: 57.0 [141]−64.4 [206]<br>mIoU: 45.9 [141]−51.8 [206] | — |
| Face Anti Spoofing | CASIA-SURF [230] | ACER(%): 3.8 [232] | ACER(%): 0.74 [32]−0.20 [180] | — | ACER(%): 2.4 [103] |
| Person Re-Identification | RGBD-ID [13] | mAP(%): 14.42 [212]−15.95 [196] | mAP(%): 27.91 [76]−40.52 [140] | mAP(%): 53.02 [213] | mAP(%): 29.2 [191]−31.49 [29] |

**评价指标**：  
BLEU-4 [136], METEOR [12], CIDEr [178], Accuracy (ACC), Intersection over Union (IoU), Average Classification Error Rate (ACER), mean Average Precision (mAP)

### 表格3：Public Datasets for Common Multimodal Data Fusion Tasks（可用数据集）

| Tasks | Data Type | Dataset |
|-------|-----------|---------|
| Referring Image Segmentation | Image + Text | ReferIt [80], Google-Ref [118], UNC [219], CLEVR-Ref+ [106], VGPhraseCut [197], ScanRefer [21], ClevrTex [79] |
| Video Captioning/Retrieval | Video + Text | Howto100M [122], Alivol-10M [89], YouCookII [242], Charades [160], TGIF [99], MSR-VTT [202], Didemo [6] |
| Visual Question Answering | Vision + Text | video-text: TVQA [91], VQA 1.0 [7], VQA 2.0 [53]; image-text: DAQUAR [116], COCO-QA [150], FM-IQA [44], Visual Genome [86], CLEVR [78], FVQA [184] |
| Object Recognition | RGB + Depth | SUN RGB-D [164], NYU Depth V1 and V2 [130, 161], RobotPKU [105], B3DO [71], BIWI [127] |
| Object Detection / Semantic Segmentation | RGB + LiDAR | KITTI [49], Urban [17], KAIST [72], RobortCar [114], US3D [40], College [146], H3D [84] |
| Human Action Recognition | RGB + Inertial Sensors | MHAD [133], C-MHAD [192], UTD-MHAD [20], CAS-MHAD [55], NCTU-MFD [166] |
| Face Anti Spoofing | RGB + Thermal | CASIA-SURF [230], CASIA-SURF Cefa [102], Speakingfaces [1], ThermalFace [8], TTVF [63], UL-FMTV [52] |
| Person Re-Identification | RGB + Thermal | RegDB [131], SYSU-MM01 [196], BIWI RGBD-ID [127], RGBD-ID [13], SUCVL RGBD-ID [120], RobotPKU [105], KinectREID [135] |

---

## Key Insights

总体来讲用人工智能进行深度数据融合的话确实效果会十分不错，各有优点缺点也可以互相融合，对于我目前的网络可定绝佳的就是GNN，GenNN，也可考虑引入注意力机制对于多特征多连接情况。