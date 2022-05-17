> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/433145820)

> 阿里的搜索团队在2019 DLP-KDD上发表的 《Behavior Sequence Transformer for E-commerce Recommendation in Alibaba》。文章的主要内容就是将近几年在NLP领域常用的Transformer模型迁移到推荐领域，利用Transform…

⚠️ 回答于 5 个月前

阿里的搜索团队在 2019 DLP-KDD 上发表的[《Behavior Sequence Transformer for E-commerce Recommendation in Alibaba》](https://dl.acm.org/doi/abs/10.1145/3326937.3341261)。

文章的主要内容就是将近几年在 NLP 领域常用的 Transformer 模型迁移到推荐领域，利用 Transformer 处理**用户行为序列信息。**模型已部署在淘宝推荐精排阶段，相比于 Wide&Deep 和 DIN 模型，CTR 有了进一步提升。

1. 介绍
-----

在深度学习时代，淘宝以 WDL(Wide&Deep 简称，下同) 为基础，构建 Rank 阶段模型。虽然 WDL 作为推荐领域影响深远的模型，但是现阶段在处理某些特征时却出现了瓶颈，即：**用户行为序列 (users’ behavior sequences 简称 UBS)**，即用户的 item 点击顺序。

该特征是对用户后续行为的点击预测非常重要的特征。近几年，越来越多的公司开始探索如何利用用户行为序列，以此来提高用户 CTR，从而带来收益。例如阿里妈妈团队: 经典的 [引入 Attention 机制的 DIN](https://zhuanlan.zhihu.com/p/425064402) 和 [GRU 结构的 DIEN](https://zhuanlan.zhihu.com/p/426670720) 和 以 Capsule network 为举出的 MIND。序列化推荐的常用建模方式可以参考

[DOTA：推荐算法炼丹笔记：序列化推荐系统](https://zhuanlan.zhihu.com/p/272862240)

文章同时也指出 DIN 的缺点：虽然使用 Attention 获取候 item 和用户历史点击的 item 的相似性，但是却并未考虑用户行为的顺序性质。+[[DIN]]

由于 Transformer 近几年在 NLP 领域的大获成功，从而将其引入处理 UBS 特征 (主要是 Multi-head Self-attention + Position embedding 结构)，经过文章的实验证明，BST 无论是离线还是在线效果均优于 WDL 和 DIN。

2. 模型
-----

**1>. 模型结构图**

![](https://pic1.zhimg.com/v2-bd98c1865ac7f4c04c549835a8173b3c_r.jpg)BST 的结构示意图：主体是 [[DIN]] + [[Transformer]]

模型结构上并没有十分特别的设计，就是 other Feature 进行 Embedding。User Behavior Sequence 进行 Transformer 中的 encoder 部分操作的过程。这里将其命名为 Transformer Layer。

**2>.Embedding Layer**

无需多言，将不同类型的 Feature 转化为 Embedding。

文中利用常规方法将**非用户历史行为特征**分为四类：

![](https://pic4.zhimg.com/v2-48e0ba7cae46ef68d594a7361e1f7f03_r.jpg)

*   User 侧特征：年龄、性别、所在城市、...
*   Item 侧特征：类别 id、店铺 id、标签、...
*   上线文特征：匹配类型、展示位置、所在页数、...
*   交叉特征：上述特征的交叉常规的特征分类

上面的四类特征在模型结构图中被归纳为 other Feature。

**用户历史行为特征**则包含两部分，分别为序列 Item 特征 (图中红色) and 位置特征 (图中蓝色)，其中序列 item 特征也和 DIN 中一样设定，包含 item_id 和 category_id 两部分。文中也提到，一个 item 包含上百个特征，全做为历史行为特征计算成本过高，只需要找到最能代表的即可，item_id 和 category_id 足够胜任。毕竟直接用 id 没有任何信息损失。

另外还引入 Positional embedding，这个特征由 Transformer 模型中引入。每个特征向量拼接上特征位置信息。但是计算方法上没有采用 Transformer 中的方法。文中说是试过，但效果不好。这里采用计算时间差作为 Positional 值。

![](https://www.zhihu.com/equation?tex=pos%28i%29+%3D+t%28v_t%29-t%28v_i%29)

其中 ![](https://www.zhihu.com/equation?tex=t%28v_i%29) 代表第 i 个 item 被点击的时间戳， ![](https://www.zhihu.com/equation?tex=v_t+) 代表候选的目标 item。值得注意的一点是并没有采用 Transformer 中的 Postional Embedding 相加，而是采用 concat(拼接)。

**3>.Transformer Layer**

1.Multi-head Self-attention

Transformer 最令人印象深刻的非 Multi-head Self-attention 莫属，在 BST 中 Multi-head Self-attention 结构完整的得到保留。Self-Attention 可以用一句话来概括：将输入转化为 K、Q、V 矩阵，使对应输出不在只包含对应输入信息，也包含了整个序列 Session 的信息。Multi-head Self-attention 则是构建多个 K、Q、V，多次利用 Self-Attention 从不同空间角度，更全面的获取有效信息。

这里只是抛转引入，网上对 Self-Attention 的解析已经十分全面，推荐看下面这篇博主记录的李宏毅老师对 Self-Attention 的讲解

[新一：李宏毅 - Attention，Self-Attention，Transformer](https://zhuanlan.zhihu.com/p/171875438)

给出文中公式：

![](https://pic1.zhimg.com/v2-63365e89a157a326cd50e16244d08ad0_r.jpg)

其中，![](https://www.zhihu.com/equation?tex=%5Cbm%7BW%7D%5EQ%2C%5Cbm%7BW%7D%5EK%2C%5Cbm%7BW%7D%5EV+%5Cin+%7BR%7D%5E%7Bd%5Ctimes+d%7D)， ![](https://www.zhihu.com/equation?tex=E) 是所有 item 的 embedding， ![](https://www.zhihu.com/equation?tex=h) 表示 head 的个数。

值得注意的是，Self-Attention 层的输入和输出必须维度相同，单头 attention 的 Q/K/V 的 shape 和多头 attention 的每个头的 Qi/Ki/Vi 的大小是不一样的，假如单头 attention 的 Q/K/V 的参数矩阵 WQ/WK/WV 的 shape 分别是 [512, 512](此处假设 encoder 的输入和输出是一样的 shape)，那么多头 attention (假设 8 个头) 的每个头的 Qi/Ki/Vi 的参数矩阵 WQi/WKi/WVi 大小是[512， 512/8]。

2.Point-wise Feed-Forward Networks

与 Transformer 中一致，加入 FFN 网络增强非线性，加入 LayerNorm、ResNet、dropout 结构，并将原始的 Relu 激活函数改为 leakyRelu。

![](https://pic2.zhimg.com/v2-cacc21ebebafef29deca8642a6ed8ccd_r.jpg)

这里回顾一下 LayerNorm 和 BatchNorm 的区别：

Batch Normalization 的处理对象是对一批样本， Layer Normalization 的处理对象是单个样本。Batch Normalization 是对这批样本的同一维度特征做归一化， Layer Normalization 是对这单个样本的所有维度特征做归一化。  

![](https://pic4.zhimg.com/v2-5e02819da020fb24adb66ee002cd277f_r.jpg)

LN 不依赖于 batch 的大小和输入 sequence 的深度，因此可以用于 batchsize 为 1 和 RNN 中对边长的输入 sequence 的 normalize 操作。

目的都是让该层参数稳定下来，避免梯度消失或者梯度爆炸，方便后续的学习。

  
一般来说，BN 更适合特征依赖于不同样本间的统计参数。因为它删除了不同特征之间的大小关系，但是保留了不同样本间的大小关系。所以在 CV 领域更常用。  
而在 NLP 领域，LN 就更加合适。因为它删除不同样本间的大小关系，但保留了一个样本内不同特征之间的大小关系。对于 NLP 或者序列任务来说，一条样本的不同特征，其实就是时序上字符取值的变化，样本内的特征关系是非常紧密的。(来自[红豆君：BatchNorm 与 LayerNorm 的异同](https://zhuanlan.zhihu.com/p/428620330))  

文中讨论了 Transformer 层需要重叠几次再输出的问题，Transformer 的原始论文中是 6 层 encoder 堆叠。经过测试发现一层相比于两层和三层效果更好。个人猜测可能是 用户历史行为信息对比 NLP 的整句话，包含的信息更少，浅层网络即可获取大部分信息。

**4>.MLP layers**

三层 MLP+Sigmod 输出。loss 取二分类经典交叉熵损失函数。Adagrad 为优化器。

3. 实验
-----

数据集

使用淘宝 App 某连续 8 天的日志构造数据集，过去 7 天作为训练，第 8 天测试。

![](https://pic4.zhimg.com/v2-f34356b8542944e27a0c3d103aaa36ab_b.jpg)

对比 WDL DIN 与不同数量 Transformer Layer 下的 BST。

实验参数设置

![](https://pic1.zhimg.com/v2-809e252153e39993903038ada08d2b1c_r.jpg)

实验结果

![](https://pic2.zhimg.com/v2-a9f0c9b1d847046b2181fe30e923baad_r.jpg)

离线使用 AUC 作为评价指标，在线 A/Btest 则使用 RT，即：响应时间（RTI）, 是为给定查询生成推荐结果的时间成本，即淘宝用户的一个请求。

4. 总结和思考
--------

个人有一些疑问：

1.position 函数怎么 embedding 化，文章中没有具体提及，源码论文中没有开源，这个我们不得而知，个人觉得可能进行分桶，如距购买 1 天内、3 天内、7 天内等等。如果数值型直接 embedding 参数会很大。

2. 把 target item embedding 在 Transformer Layer 上如何操作，是拼接在原始 User Behavior Sequence 后进入 self-Attention？在 self-Attention 后拼接？很多细节受限于 4 页表达并不清晰。

3. 论文没有在公有数据集上进行，例如经典的 Criteo 数据集，只用了内部数据集，那么内部数据集是否在行为特征上具有普适性，具体的数据分布，这里并没有详细去描述。

文章是 transformer 在推荐领域的迁移，对 transformer 的关键点 Positional Embedding 和 Multi-head Self-attention 进行了复用，如 position 函数和激活函数的更改。相比于阿里出品的其他论文，稍显寡淡。

随着 Transformer 和 Bert 在 NLP 领域效果上一枝独秀，推荐领域有越来越多的模型开始借鉴、迁移 NLP 中的优秀技术。如本篇的 BST、关注特征交叉的 AutoInt、还是下一篇要介绍的 BERT4Rec 都是典型代表。但是需要注意的是 NLP 领域更关注于时序这个性质，落地前需要衡量公司在这部分的数据积累是否充足，否则可能会出现事倍功半的效果。