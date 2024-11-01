# 机器学习算法部分

- 机器学习分为监督学习、非监督学习和半监督学习

## 监督学习


### 分类算法
**分类算法**是有监督学习

#### 支持向量机（SVM）
**SVM算法**是监督学习，用于解决二分类&多分类问题。
**核心思想**：找到一个超平面进行分类，并使间隔最大。
硬间隔和软间隔：
- 硬间隔：严格分隔实例到最大间隔之外且为正确的一边。
  - 缺点：只对线性可分离数据有效，且对于异常值非常敏感。
- 软间隔：在保持最大间隔宽阔和限制间隔违例（在间隔内甚至错误一侧）间找到平衡。
  - Scikit-learn中，通过超参数C控制，C越小，间隔越宽，违例越多，反之亦然。

优点：
1. 良好的鲁棒性，对未知数据有较强泛化性，在数据较少时相比传统机器学习算法有更优性能。

流程：
1. 对样本数据归一化。

## 无监督学习

### 聚类算法
**聚类算法**是无监督学习。
聚类算法有**Hierarchical Clustering（层次聚类）、Partitioning Clustering（分割聚类）、Density Based Clustering**

#### Partitioning Clustering
主要目的是把数据聚成多个簇


##### K-means
主要定义：K：分为**K**个类，mean是一个数据集的**质心**，有k个所以是means。
原理：K-means算法通过迭代，将数据点划分到最近（欧式距离、余弦相似...）的类簇中心点（mean）代表的簇中。随后根据簇中数据点重新计算质点。不断重复。
重点：
- K的选择：经验、统计技巧、领域知识...
- 距离度量：欧氏距离（Euclidean distance），或根据项目需求选择。
- 质心：簇内数据点均值。
- 优化目标：最小化每个数据点到簇中心点距离之和。

[K-Means可视化网站](https://www.naftaliharris.com/blog/visualizing-k-means-clustering/)


##### K-Medoids（或称PAM（Partioning Around Medoids））
主要定义：Partioning：分割聚类算法，Medoids是**K-Medoids（K个簇的唯一中心点）**。
与K-Means的区别：K—Means算法不具备

## 特征选择（Feature Selection）
特征选择作为特征工程的一部分，主要是去除不相关或冗余（**Irrelevant&Redundant**）的特征，防止产生影响.

### 过滤方法（Filter Method）
定义：利用统计学方法，**计算特征与目标变量之间的相关性**，评估特征的重要性，选择最佳特征子集。

#### 方差选择法（Variance Thresholding）
通过计算特征的方差选择特征，方差低于阈值（threshold）的往往不具备保留价值。
优点：简单、快速、适合大规模数据
缺点：只考虑特征的单变量分布，且有些特征虽小但重要。

#### 相关系数法（Pearson correlation）


#### 卡方检验（Chi-Square Test）


#### 互信息法（Mutual Information）


#### L1正则化（L1 Regularization）



### 包装方法（Wrapper Method）


## 半监督学习（Semi-Supervised Learning）
利用少量有标签数据和大量无标签数据训练网络，起因是手工标注数据过于困难。
情景：
- 直推半监督学习：利用有类标签和无类标签的样例进行训练，预测训练数据中无类标签的样例。
- 归纳半监督学习：有类标签、无类标签、以及未知的测试样例。最主要的是预测未知的测试样例。

> 三大假设：平滑假设、聚类假设、流形假设
三个假设本质上一致，我主要了解了聚类假设：当两个样例处于同一聚类簇，他们大概率有同一类标签
等价于低密度分离假设（Low Sensity Separation Assumption）：分类决策边界应尽量穿过稀疏数据区域，避免分割稠密数据区域。
通过该假设，可获得将有类标签尽量正确划分的分类超平面。

分类：
1. 半监督分类：在无类标签帮助下...
2. 半监督回归: 在无类标签帮助下...
3. 半监督聚类：**在有类标签帮助下...**
4. 半监督降维：**在有类标签帮助下...**

半监督学习算法：
自训练算法、基于图的半监督算法（代表：标签传播算法）、半监督支持向量机（S3VM）

### 半监督深度学习
定义：有标签数据+无标签数据混合的数据中使用的深度学习算法。

## 自监督学习（Self-supervised Learning）



## 集成学习（Ensemble Learning）
通过构建并结合多个个体学习器来完成任务
**同质集成和异质集成**：同质集成为使用相同算法的个体学习器（同质的又称为基学习器），异质则为不同算法的学习器。
同质集成中，要获得较好（至少要强于单一学习器吧），要满足两个条件：
1. 基学习器要有一定的性能，不能弱于随机预测。
2. 基学习器之间要有差异（**多样性**）
[推论](https://datawhalechina.github.io/pumpkin-book/#/chapter8/chapter8?id=_83)

分类：
- Boosting：学习器之间存在强依赖关系，必须串行。
- Bagging：不存强依赖关系，可以并行。
- Stacking： 

增强多样性的方式：
一般就是对**数据样本、输入属性、输出表示、算法参数**进行扰动。
1. 数据样本扰动
对决策树、神经网络这样的对数据敏感方法有效，对SVM等效果不佳。
2. 输入属性扰动
对于那种冗余属性较多的数据，通过提取不同的特征子集，能够训练多样的学习器，还能减少时间消耗。
3. 输出表示扰动
这类做法的基本思路是对输出表示进行操纵以增强多样性。比如可对训练样本的label稍作变动，比如“翻转法”随机改变一些训练样本的标记；也可以对输出表示进行转化，如“输出调制法”将分类输出转化为回归输出后构建基学习器。这一类貌似用的不多。
4. 算法参数扰动
深度学习这么多参数，调白

### Boosting
Boosting实际上是一个迭代学习的过程。
代表：AdaBoost和XGBoost
过程：初始学习-根据结果调整权重-重复学习直到达到预定轮数-结合基学习器，正确率大的权重大。

#### AdaBoost（Adaptive Boost & 自适应增强）
通过调整对数据样本的权重，新的基学习器对于权重较大的数据的正确率更高，由此，结合出一个强分类器。
[AdaBoosting推导与介绍](https://zhuanlan.zhihu.com/p/41536315)