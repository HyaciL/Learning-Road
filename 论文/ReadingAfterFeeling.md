## 软件缺陷预测 & Software Defect Prediction & SDP

### 软件缺陷预测技术
早期论文，讲解研究了软件缺陷预测技术的起源
从软件的诞生，就伴随着缺陷预测技术。
最早是统计学的方法。
从70年代起，大致分为了静态和动态两种缺陷预测技术。
**静态**：主要是基于缺陷相关的度量数据，对缺陷的数量和分布进行预测。
1. 基于度量元（Metric）的缺陷预测技术
   1. 基于软件规模（如代码行）
   2. 基于软件复杂度（如图理论、决策路径）
   3. 基于多维软件度量元
2. 缺陷分布预测技术
   要识别少量含有问题的模块
   1. 分类和回归技术
3. 缺陷预测模型技术
**动态**：主要是基于缺陷产生的时间，对缺陷的数量和分布进行预测。
如Rayleigh分布模型





### 基于支持向量机的软件缺陷预测模型
**摘要**：软件缺陷预测在软件系统开发的各个阶段发挥着极为重要的作用。利用机器学习的相关方法建立更好的预测模型已经被广泛研究。文章分析了支持向量机SVM作为二值分类模型应用到软件缺陷预测中的实现方法,构造了基于SVM的**可迭代增强**的缺陷预测模型SVM-DP。在13个基准数据集上开展比较实验,定量地分析了应用**各种核函数**对SVM-DP模型性能的影响。实验结果显示,应用线性内积核函数的SVM-DP具有最优的预测性能。同时,在与J48的比较实验中,最高超过J48预测模型20%的性能进一步证明了SVM-DP模型应用于软件缺陷预测的有效性。