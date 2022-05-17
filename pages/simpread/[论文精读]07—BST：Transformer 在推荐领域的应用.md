title:: [论文精读]07—BST：Transformer 在推荐领域的应用
tags:: [[简悦]] [[阿里技术]]  [[推荐系统]]  [[排序算法]]  [[精排]]  
source:: https://zhuanlan.zhihu.com/p/433145820
date:: 2022年05月17日 07:13:47

- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652742827311>) DIN 的缺点：虽然使用 Attention 获取候 item 和用户历史点击的 item 的相似性，但是却并未考虑用户行为的顺序性质。
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652742885833>) 模型结构上并没有十分特别的设计，就是 other Feature 进行 Embedding。User Behavior Sequence 进行 Transformer 中的 encoder 部分操作的过程。
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652742923481>) *   User 侧特征：年龄、性别、所在城市、...
  *   Item 侧特征：类别 id、店铺 id、标签、...
  *   上线文特征：匹配类型、展示位置、所在页数、...
  *   交叉特征：上述特征的交叉
	- 常规的特征分类
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652742989181>) **用户历史行为特征**则包含两部分，分别为序列 Item 特征 (图中红色) and 位置特征 (图中蓝色)，其中序列 item 特征也和 DIN 中一样设定，包含 item_id 和 category_id 两部分。
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652743019396>) 另外还引入 Positional embedding，这个特征由 Transformer 模型中引入。每个特征向量拼接上特征位置信息。
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652743182499>) 这里采用计算时间差作为 Positional 值。
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652743406731>) Batch Normalization 的处理对象是对一批样本， Layer Normalization 的处理对象是单个样本。Batch Normalization 是对这批样本的同一维度特征做归一化， Layer Normalization 是对这单个样本的所有维度特征做归一化。
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652743262180>) ![](https://pic4.zhimg.com/v2-5e02819da020fb24adb66ee002cd277f_r.jpg)
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652743422007>) LN 不依赖于 batch 的大小和输入 sequence 的深度，因此可以用于 batchsize 为 1 和 RNN 中对边长的输入 sequence 的 normalize 操作。
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652743469907>) 一般来说，BN 更适合特征依赖于不同样本间的统计参数。因为它删除了不同特征之间的大小关系，但是保留了不同样本间的大小关系。所以在 CV 领域更常用。  
  而在 NLP 领域，LN 就更加合适。因为它删除不同样本间的大小关系，但保留了一个样本内不同特征之间的大小关系。对于 NLP 或者序列任务来说，一条样本的不同特征，其实就是时序上字符取值的变化，样本内的特征关系是非常紧密的。
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652743488587>) 经过测试发现一层相比于两层和三层效果更好。个人猜测可能是 用户历史行为信息对比 NLP 的整句话，包含的信息更少，浅层网络即可获取大部分信息。
- > [📌](<http://localhost:7026/pdf/[论文精读]07—BST：Transformer 在推荐领域的应用#id=1652743550336>) 1.position 函数怎么 embedding 化，文章中没有具体提及，源码论文中没有开源，这个我们不得而知，个人觉得可能进行分桶，如距购买 1 天内、3 天内、7 天内等等。如果数值型直接 embedding 参数会很大。