title:: [论文精读]07—BST：Transformer 在推荐领域的应用
tags:: [[简悦]] [[阿里技术]]  [[推荐系统]]  [[排序算法]]  [[精排]]  
source:: https://zhuanlan.zhihu.com/p/433145820
date:: 2022年05月17日 07:13:47


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=DIN%20%E7%9A%84%E7%BC%BA%E7%82%B9%EF%BC%9A%E8%99%BD%E7%84%B6%E4%BD%BF%E7%94%A8%20Attention%20%E8%8E%B7%E5%8F%96%E5%80%99%20item%20%E5%92%8C%E7%94%A8%E6%88%B7%E5%8E%86%E5%8F%B2%E7%82%B9%E5%87%BB%E7%9A%84%20item%20%E7%9A%84%E7%9B%B8%E4%BC%BC%E6%80%A7%EF%BC%8C%E4%BD%86%E6%98%AF%E5%8D%B4%E5%B9%B6%E6%9C%AA%E8%80%83%E8%99%91%E7%94%A8%E6%88%B7%E8%A1%8C%E4%B8%BA%E7%9A%84%E9%A1%BA%E5%BA%8F%E6%80%A7%E8%B4%A8%E3%80%82)
  -  DIN 的缺点：虽然使用 Attention 获取候 item 和用户历史点击的 item 的相似性，但是却并未考虑用户行为的顺序性质。

  - 📝 +[[DIN]]

- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=https://pic1.zhimg.com/v2-bd98c1865ac7f4c04c549835a8173b3c_r.jpg)
  -  ![](https://pic1.zhimg.com/v2-bd98c1865ac7f4c04c549835a8173b3c_r.jpg)

  - 📝 BST 的结构示意图：主体是 [[DIN]] + [[Transformer]]

- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=%E6%A8%A1%E5%9E%8B%E7%BB%93%E6%9E%84%E4%B8%8A%E5%B9%B6%E6%B2%A1%E6%9C%89%E5%8D%81%E5%88%86%E7%89%B9%E5%88%AB%E7%9A%84%E8%AE%BE%E8%AE%A1%EF%BC%8C%E5%B0%B1%E6%98%AF%20other%20Feature%20%E8%BF%9B%E8%A1%8C%20Embedding%E3%80%82User%20Behavior%20Sequence%20%E8%BF%9B%E8%A1%8C%20Transformer%20%E4%B8%AD%E7%9A%84%20encoder%20%E9%83%A8%E5%88%86%E6%93%8D%E4%BD%9C%E7%9A%84%E8%BF%87%E7%A8%8B%E3%80%82)
  -  模型结构上并没有十分特别的设计，就是 other Feature 进行 Embedding。User Behavior Sequence 进行 Transformer 中的 encoder 部分操作的过程。


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=User%20%E4%BE%A7%E7%89%B9%E5%BE%81%EF%BC%9A%E5%B9%B4%E9%BE%84%E3%80%81%E6%80%A7%E5%88%AB%E3%80%81%E6%89%80%E5%9C%A8%E5%9F%8E%E5%B8%82%E3%80%81...Item%20%E4%BE%A7%E7%89%B9%E5%BE%81%EF%BC%9A%E7%B1%BB%E5%88%AB%20id%E3%80%81%E5%BA%97%E9%93%BA%20id%E3%80%81%E6%A0%87%E7%AD%BE%E3%80%81...%E4%B8%8A%E7%BA%BF%E6%96%87%E7%89%B9%E5%BE%81%EF%BC%9A%E5%8C%B9%E9%85%8D%E7%B1%BB%E5%9E%8B%E3%80%81%E5%B1%95%E7%A4%BA%E4%BD%8D%E7%BD%AE%E3%80%81%E6%89%80%E5%9C%A8%E9%A1%B5%E6%95%B0%E3%80%81...%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%EF%BC%9A%E4%B8%8A%E8%BF%B0%E7%89%B9%E5%BE%81%E7%9A%84%E4%BA%A4%E5%8F%89)
  -  *   User 侧特征：年龄、性别、所在城市、...
  -  *   Item 侧特征：类别 id、店铺 id、标签、...
  -  *   上线文特征：匹配类型、展示位置、所在页数、...
  -  *   交叉特征：上述特征的交叉

  - 📝 常规的特征分类

- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=%E7%94%A8%E6%88%B7%E5%8E%86%E5%8F%B2%E8%A1%8C%E4%B8%BA%E7%89%B9%E5%BE%81%E5%88%99%E5%8C%85%E5%90%AB%E4%B8%A4%E9%83%A8%E5%88%86%EF%BC%8C%E5%88%86%E5%88%AB%E4%B8%BA%E5%BA%8F%E5%88%97%20Item%20%E7%89%B9%E5%BE%81%20(%E5%9B%BE%E4%B8%AD%E7%BA%A2%E8%89%B2)%20and%20%E4%BD%8D%E7%BD%AE%E7%89%B9%E5%BE%81%20(%E5%9B%BE%E4%B8%AD%E8%93%9D%E8%89%B2)%EF%BC%8C%E5%85%B6%E4%B8%AD%E5%BA%8F%E5%88%97%20item%20%E7%89%B9%E5%BE%81%E4%B9%9F%E5%92%8C%20DIN%20%E4%B8%AD%E4%B8%80%E6%A0%B7%E8%AE%BE%E5%AE%9A%EF%BC%8C%E5%8C%85%E5%90%AB%20item_id%20%E5%92%8C%20category_id%20%E4%B8%A4%E9%83%A8%E5%88%86%E3%80%82)
  -  **用户历史行为特征**则包含两部分，分别为序列 Item 特征 (图中红色) and 位置特征 (图中蓝色)，其中序列 item 特征也和 DIN 中一样设定，包含 item_id 和 category_id 两部分。


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=%E5%8F%A6%E5%A4%96%E8%BF%98%E5%BC%95%E5%85%A5%20Positional%20embedding%EF%BC%8C%E8%BF%99%E4%B8%AA%E7%89%B9%E5%BE%81%E7%94%B1%20Transformer%20%E6%A8%A1%E5%9E%8B%E4%B8%AD%E5%BC%95%E5%85%A5%E3%80%82%E6%AF%8F%E4%B8%AA%E7%89%B9%E5%BE%81%E5%90%91%E9%87%8F%E6%8B%BC%E6%8E%A5%E4%B8%8A%E7%89%B9%E5%BE%81%E4%BD%8D%E7%BD%AE%E4%BF%A1%E6%81%AF%E3%80%82)
  -  另外还引入 Positional embedding，这个特征由 Transformer 模型中引入。每个特征向量拼接上特征位置信息。


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=%E8%BF%99%E9%87%8C%E9%87%87%E7%94%A8%E8%AE%A1%E7%AE%97%E6%97%B6%E9%97%B4%E5%B7%AE%E4%BD%9C%E4%B8%BA%20Positional%20%E5%80%BC%E3%80%82)
  -  这里采用计算时间差作为 Positional 值。


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=Batch%20Normalization%20%E7%9A%84%E5%A4%84%E7%90%86%E5%AF%B9%E8%B1%A1%E6%98%AF%E5%AF%B9%E4%B8%80%E6%89%B9%E6%A0%B7%E6%9C%AC%EF%BC%8C%20Layer%20Normalization%20%E7%9A%84%E5%A4%84%E7%90%86%E5%AF%B9%E8%B1%A1%E6%98%AF%E5%8D%95%E4%B8%AA%E6%A0%B7%E6%9C%AC%E3%80%82Batch%20Normalization%20%E6%98%AF%E5%AF%B9%E8%BF%99%E6%89%B9%E6%A0%B7%E6%9C%AC%E7%9A%84%E5%90%8C%E4%B8%80%E7%BB%B4%E5%BA%A6%E7%89%B9%E5%BE%81%E5%81%9A%E5%BD%92%E4%B8%80%E5%8C%96%EF%BC%8C%20Layer%20Normalization%20%E6%98%AF%E5%AF%B9%E8%BF%99%E5%8D%95%E4%B8%AA%E6%A0%B7%E6%9C%AC%E7%9A%84%E6%89%80%E6%9C%89%E7%BB%B4%E5%BA%A6%E7%89%B9%E5%BE%81%E5%81%9A%E5%BD%92%E4%B8%80%E5%8C%96%E3%80%82)
  -  Batch Normalization 的处理对象是对一批样本， Layer Normalization 的处理对象是单个样本。Batch Normalization 是对这批样本的同一维度特征做归一化， Layer Normalization 是对这单个样本的所有维度特征做归一化。


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=https://pic4.zhimg.com/v2-5e02819da020fb24adb66ee002cd277f_r.jpg)
  -  ![](https://pic4.zhimg.com/v2-5e02819da020fb24adb66ee002cd277f_r.jpg)


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=LN%20%E4%B8%8D%E4%BE%9D%E8%B5%96%E4%BA%8E%20batch%20%E7%9A%84%E5%A4%A7%E5%B0%8F%E5%92%8C%E8%BE%93%E5%85%A5%20sequence%20%E7%9A%84%E6%B7%B1%E5%BA%A6%EF%BC%8C%E5%9B%A0%E6%AD%A4%E5%8F%AF%E4%BB%A5%E7%94%A8%E4%BA%8E%20batchsize%20%E4%B8%BA%201%20%E5%92%8C%20RNN%20%E4%B8%AD%E5%AF%B9%E8%BE%B9%E9%95%BF%E7%9A%84%E8%BE%93%E5%85%A5%20sequence%20%E7%9A%84%20normalize%20%E6%93%8D%E4%BD%9C%E3%80%82)
  -  LN 不依赖于 batch 的大小和输入 sequence 的深度，因此可以用于 batchsize 为 1 和 RNN 中对边长的输入 sequence 的 normalize 操作。


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=%E4%B8%80%E8%88%AC%E6%9D%A5%E8%AF%B4%EF%BC%8CBN%20%E6%9B%B4%E9%80%82%E5%90%88%E7%89%B9%E5%BE%81%E4%BE%9D%E8%B5%96%E4%BA%8E%E4%B8%8D%E5%90%8C%E6%A0%B7%E6%9C%AC%E9%97%B4%E7%9A%84%E7%BB%9F%E8%AE%A1%E5%8F%82%E6%95%B0%E3%80%82%E5%9B%A0%E4%B8%BA%E5%AE%83%E5%88%A0%E9%99%A4%E4%BA%86%E4%B8%8D%E5%90%8C%E7%89%B9%E5%BE%81%E4%B9%8B%E9%97%B4%E7%9A%84%E5%A4%A7%E5%B0%8F%E5%85%B3%E7%B3%BB%EF%BC%8C%E4%BD%86%E6%98%AF%E4%BF%9D%E7%95%99%E4%BA%86%E4%B8%8D%E5%90%8C%E6%A0%B7%E6%9C%AC%E9%97%B4%E7%9A%84%E5%A4%A7%E5%B0%8F%E5%85%B3%E7%B3%BB%E3%80%82%E6%89%80%E4%BB%A5%E5%9C%A8%20CV%20%E9%A2%86%E5%9F%9F%E6%9B%B4%E5%B8%B8%E7%94%A8%E3%80%82%E8%80%8C%E5%9C%A8%20NLP%20%E9%A2%86%E5%9F%9F%EF%BC%8CLN%20%E5%B0%B1%E6%9B%B4%E5%8A%A0%E5%90%88%E9%80%82%E3%80%82%E5%9B%A0%E4%B8%BA%E5%AE%83%E5%88%A0%E9%99%A4%E4%B8%8D%E5%90%8C%E6%A0%B7%E6%9C%AC%E9%97%B4%E7%9A%84%E5%A4%A7%E5%B0%8F%E5%85%B3%E7%B3%BB%EF%BC%8C%E4%BD%86%E4%BF%9D%E7%95%99%E4%BA%86%E4%B8%80%E4%B8%AA%E6%A0%B7%E6%9C%AC%E5%86%85%E4%B8%8D%E5%90%8C%E7%89%B9%E5%BE%81%E4%B9%8B%E9%97%B4%E7%9A%84%E5%A4%A7%E5%B0%8F%E5%85%B3%E7%B3%BB%E3%80%82%E5%AF%B9%E4%BA%8E%20NLP%20%E6%88%96%E8%80%85%E5%BA%8F%E5%88%97%E4%BB%BB%E5%8A%A1%E6%9D%A5%E8%AF%B4%EF%BC%8C%E4%B8%80%E6%9D%A1%E6%A0%B7%E6%9C%AC%E7%9A%84%E4%B8%8D%E5%90%8C%E7%89%B9%E5%BE%81%EF%BC%8C%E5%85%B6%E5%AE%9E%E5%B0%B1%E6%98%AF%E6%97%B6%E5%BA%8F%E4%B8%8A%E5%AD%97%E7%AC%A6%E5%8F%96%E5%80%BC%E7%9A%84%E5%8F%98%E5%8C%96%EF%BC%8C%E6%A0%B7%E6%9C%AC%E5%86%85%E7%9A%84%E7%89%B9%E5%BE%81%E5%85%B3%E7%B3%BB%E6%98%AF%E9%9D%9E%E5%B8%B8%E7%B4%A7%E5%AF%86%E7%9A%84%E3%80%82)
  -  一般来说，BN 更适合特征依赖于不同样本间的统计参数。因为它删除了不同特征之间的大小关系，但是保留了不同样本间的大小关系。所以在 CV 领域更常用。  
  -  而在 NLP 领域，LN 就更加合适。因为它删除不同样本间的大小关系，但保留了一个样本内不同特征之间的大小关系。对于 NLP 或者序列任务来说，一条样本的不同特征，其实就是时序上字符取值的变化，样本内的特征关系是非常紧密的。


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=%E7%BB%8F%E8%BF%87%E6%B5%8B%E8%AF%95%E5%8F%91%E7%8E%B0%E4%B8%80%E5%B1%82%E7%9B%B8%E6%AF%94%E4%BA%8E%E4%B8%A4%E5%B1%82%E5%92%8C%E4%B8%89%E5%B1%82%E6%95%88%E6%9E%9C%E6%9B%B4%E5%A5%BD%E3%80%82%E4%B8%AA%E4%BA%BA%E7%8C%9C%E6%B5%8B%E5%8F%AF%E8%83%BD%E6%98%AF%20%E7%94%A8%E6%88%B7%E5%8E%86%E5%8F%B2%E8%A1%8C%E4%B8%BA%E4%BF%A1%E6%81%AF%E5%AF%B9%E6%AF%94%20NLP%20%E7%9A%84%E6%95%B4%E5%8F%A5%E8%AF%9D%EF%BC%8C%E5%8C%85%E5%90%AB%E7%9A%84%E4%BF%A1%E6%81%AF%E6%9B%B4%E5%B0%91%EF%BC%8C%E6%B5%85%E5%B1%82%E7%BD%91%E7%BB%9C%E5%8D%B3%E5%8F%AF%E8%8E%B7%E5%8F%96%E5%A4%A7%E9%83%A8%E5%88%86%E4%BF%A1%E6%81%AF%E3%80%82)
  -  经过测试发现一层相比于两层和三层效果更好。个人猜测可能是 用户历史行为信息对比 NLP 的整句话，包含的信息更少，浅层网络即可获取大部分信息。


- > [🌐原链接](https://zhuanlan.zhihu.com/p/433145820#js_content:~:text=1.position%20%E5%87%BD%E6%95%B0%E6%80%8E%E4%B9%88%20embedding%20%E5%8C%96%EF%BC%8C%E6%96%87%E7%AB%A0%E4%B8%AD%E6%B2%A1%E6%9C%89%E5%85%B7%E4%BD%93%E6%8F%90%E5%8F%8A%EF%BC%8C%E6%BA%90%E7%A0%81%E8%AE%BA%E6%96%87%E4%B8%AD%E6%B2%A1%E6%9C%89%E5%BC%80%E6%BA%90%EF%BC%8C%E8%BF%99%E4%B8%AA%E6%88%91%E4%BB%AC%E4%B8%8D%E5%BE%97%E8%80%8C%E7%9F%A5%EF%BC%8C%E4%B8%AA%E4%BA%BA%E8%A7%89%E5%BE%97%E5%8F%AF%E8%83%BD%E8%BF%9B%E8%A1%8C%E5%88%86%E6%A1%B6%EF%BC%8C%E5%A6%82%E8%B7%9D%E8%B4%AD%E4%B9%B0%201%20%E5%A4%A9%E5%86%85%E3%80%813%20%E5%A4%A9%E5%86%85%E3%80%817%20%E5%A4%A9%E5%86%85%E7%AD%89%E7%AD%89%E3%80%82%E5%A6%82%E6%9E%9C%E6%95%B0%E5%80%BC%E5%9E%8B%E7%9B%B4%E6%8E%A5%20embedding%20%E5%8F%82%E6%95%B0%E4%BC%9A%E5%BE%88%E5%A4%A7%E3%80%82)
  -  1.position 函数怎么 embedding 化，文章中没有具体提及，源码论文中没有开源，这个我们不得而知，个人觉得可能进行分桶，如距购买 1 天内、3 天内、7 天内等等。如果数值型直接 embedding 参数会很大。


