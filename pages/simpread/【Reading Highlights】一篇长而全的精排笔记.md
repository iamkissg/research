title:: 【Reading Highlights】一篇长而全的精排笔记
source:: https://zhuanlan.zhihu.com/p/401775395
summary:: 
tags:: [[简悦]] [[精排]]  [[推荐系统]]   [[reading_highlights]]
date:: 20220523  

- > 现如今前沿的精排模型，大部分也是着重于以上三个部分：向量化、特征交叉和历史建模。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E7%8E%B0%E5%A6%82%E4%BB%8A%E5%89%8D%E6%B2%BF%E7%9A%84%E7%B2%BE%E6%8E%92%E6%A8%A1%E5%9E%8B%EF%BC%8C%E5%A4%A7%E9%83%A8%E5%88%86%E4%B9%9F%E6%98%AF%E7%9D%80%E9%87%8D%E4%BA%8E%E4%BB%A5%E4%B8%8A%E4%B8%89%E4%B8%AA%E9%83%A8%E5%88%86%EF%BC%9A%E5%90%91%E9%87%8F%E5%8C%96%E3%80%81%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%E5%92%8C%E5%8E%86%E5%8F%B2%E5%BB%BA%E6%A8%A1%E3%80%82))
  - 📝 精排优化的三个重点：向量化、特征交叉、序列建模

- > ![](https://pic2.zhimg.com/v2-ad27cfdca1668e96963a599abfbd0be9_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic2.zhimg.com/v2-ad27cfdca1668e96963a599abfbd0be9_r.jpg))
  - 📝 Wide and Deep 的示意图

- > ![](https://pic1.zhimg.com/v2-ecadf4abcd6ea22e94c7d891f55f3088_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic1.zhimg.com/v2-ecadf4abcd6ea22e94c7d891f55f3088_r.jpg))
  - 📝 DeepFM 的示意图

- > 就是把 WDL 的 LR 部分换成了 FM，简单吧，后面你会发现很多家的想法都非常类似，就是在 WDL 上，换 wide 换 deep，DeepFm 的优点在于，同时将 Raw feature 和二阶 inner product 的 raw feature 的作用，省去了 WDL 中的手工交叉特征的步骤，且这里 deep 层和 FM 层共用一套 embedding。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E5%B0%B1%E6%98%AF%E6%8A%8A%20WDL%20%E7%9A%84%20LR%20%E9%83%A8%E5%88%86%E6%8D%A2%E6%88%90%E4%BA%86%20FM%EF%BC%8C%E7%AE%80%E5%8D%95%E5%90%A7%EF%BC%8C%E5%90%8E%E9%9D%A2%E4%BD%A0%E4%BC%9A%E5%8F%91%E7%8E%B0%E5%BE%88%E5%A4%9A%E5%AE%B6%E7%9A%84%E6%83%B3%E6%B3%95%E9%83%BD%E9%9D%9E%E5%B8%B8%E7%B1%BB%E4%BC%BC%EF%BC%8C%E5%B0%B1%E6%98%AF%E5%9C%A8%20WDL%20%E4%B8%8A%EF%BC%8C%E6%8D%A2%20wide%20%E6%8D%A2%20deep%EF%BC%8CDeepFm%20%E7%9A%84%E4%BC%98%E7%82%B9%E5%9C%A8%E4%BA%8E%EF%BC%8C%E5%90%8C%E6%97%B6%E5%B0%86%20Raw%20feature%20%E5%92%8C%E4%BA%8C%E9%98%B6%20inner%20product%20%E7%9A%84%20raw%20feature%20%E7%9A%84%E4%BD%9C%E7%94%A8%EF%BC%8C%E7%9C%81%E5%8E%BB%E4%BA%86%20WDL%20%E4%B8%AD%E7%9A%84%E6%89%8B%E5%B7%A5%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%E7%9A%84%E6%AD%A5%E9%AA%A4%EF%BC%8C%E4%B8%94%E8%BF%99%E9%87%8C%20deep%20%E5%B1%82%E5%92%8C%20FM%20%E5%B1%82%E5%85%B1%E7%94%A8%E4%B8%80%E5%A5%97%20embedding%E3%80%82))
  - 📝 DeepFM 相对 Wide and Deep 的改进：LR -> FM

- > **FGCNN：Feature Generation by Convolutional Neural Network**

  
核心思想是通过 CNN 进行卷积，通过 CNN 提取 neighbor feature patterns，经过卷积层，池化层和重组层生成新的特征，将生成的特征和 raw features 最后合并一起进模型进行训练，相当于用 CNN 生成了新的特征。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=FGCNN%EF%BC%9AFeature%20Generation%20by%20Convolutional%20Neural%20Network%E6%A0%B8%E5%BF%83%E6%80%9D%E6%83%B3%E6%98%AF%E9%80%9A%E8%BF%87%20CNN%20%E8%BF%9B%E8%A1%8C%E5%8D%B7%E7%A7%AF%EF%BC%8C%E9%80%9A%E8%BF%87%20CNN%20%E6%8F%90%E5%8F%96%20neighbor%20feature%20patterns%EF%BC%8C%E7%BB%8F%E8%BF%87%E5%8D%B7%E7%A7%AF%E5%B1%82%EF%BC%8C%E6%B1%A0%E5%8C%96%E5%B1%82%E5%92%8C%E9%87%8D%E7%BB%84%E5%B1%82%E7%94%9F%E6%88%90%E6%96%B0%E7%9A%84%E7%89%B9%E5%BE%81%EF%BC%8C%E5%B0%86%E7%94%9F%E6%88%90%E7%9A%84%E7%89%B9%E5%BE%81%E5%92%8C%20raw%20features%20%E6%9C%80%E5%90%8E%E5%90%88%E5%B9%B6%E4%B8%80%E8%B5%B7%E8%BF%9B%E6%A8%A1%E5%9E%8B%E8%BF%9B%E8%A1%8C%E8%AE%AD%E7%BB%83%EF%BC%8C%E7%9B%B8%E5%BD%93%E4%BA%8E%E7%94%A8%20CNN%20%E7%94%9F%E6%88%90%E4%BA%86%E6%96%B0%E7%9A%84%E7%89%B9%E5%BE%81%E3%80%82))

- > 双塔模型的核心思想在于，许多相关的模型都具有不同层面个上的优势，简单的想法就是，合起来，WDL 就是 LR+DNN，deepFm 就是 FM+DNN，DCN 就是 cross network+DNN，xdeepFm 就是 CIN+DNN，两个子模型的 logit 合起来再进行 sigmoid  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E5%8F%8C%E5%A1%94%E6%A8%A1%E5%9E%8B%E7%9A%84%E6%A0%B8%E5%BF%83%E6%80%9D%E6%83%B3%E5%9C%A8%E4%BA%8E%EF%BC%8C%E8%AE%B8%E5%A4%9A%E7%9B%B8%E5%85%B3%E7%9A%84%E6%A8%A1%E5%9E%8B%E9%83%BD%E5%85%B7%E6%9C%89%E4%B8%8D%E5%90%8C%E5%B1%82%E9%9D%A2%E4%B8%AA%E4%B8%8A%E7%9A%84%E4%BC%98%E5%8A%BF%EF%BC%8C%E7%AE%80%E5%8D%95%E7%9A%84%E6%83%B3%E6%B3%95%E5%B0%B1%E6%98%AF%EF%BC%8C%E5%90%88%E8%B5%B7%E6%9D%A5%EF%BC%8CWDL%20%E5%B0%B1%E6%98%AF%20LR+DNN%EF%BC%8CdeepFm%20%E5%B0%B1%E6%98%AF%20FM+DNN%EF%BC%8CDCN%20%E5%B0%B1%E6%98%AF%20cross%20network+DNN%EF%BC%8CxdeepFm%20%E5%B0%B1%E6%98%AF%20CIN+DNN%EF%BC%8C%E4%B8%A4%E4%B8%AA%E5%AD%90%E6%A8%A1%E5%9E%8B%E7%9A%84%20logit%20%E5%90%88%E8%B5%B7%E6%9D%A5%E5%86%8D%E8%BF%9B%E8%A1%8C%20sigmoid))

- > ![](https://pic3.zhimg.com/v2-4521d28c8d731135865773c837e9e656_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic3.zhimg.com/v2-4521d28c8d731135865773c837e9e656_r.jpg))
  - 📝 GBDT+LR 的结构图

- > 这个方案其实本质是通过 GBDT 这种树模型来学习特征的交叉，然后通过 LR 来学习交叉特征的权重，相当于 GBDT 做了前续的特征组合工作，LR 做了最后的单层 MLP 工作，但是本身像 GBDT 这种树模型其实很难处理 id 类的特征（那就对 CTR 预估里面的历史兴趣建模无能为力了），只不过如果有一个项目需要快速上线的时候，GBDT 往往能得到一个快速的，接近 70 分的效果  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E8%BF%99%E4%B8%AA%E6%96%B9%E6%A1%88%E5%85%B6%E5%AE%9E%E6%9C%AC%E8%B4%A8%E6%98%AF%E9%80%9A%E8%BF%87%20GBDT%20%E8%BF%99%E7%A7%8D%E6%A0%91%E6%A8%A1%E5%9E%8B%E6%9D%A5%E5%AD%A6%E4%B9%A0%E7%89%B9%E5%BE%81%E7%9A%84%E4%BA%A4%E5%8F%89%EF%BC%8C%E7%84%B6%E5%90%8E%E9%80%9A%E8%BF%87%20LR%20%E6%9D%A5%E5%AD%A6%E4%B9%A0%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%E7%9A%84%E6%9D%83%E9%87%8D%EF%BC%8C%E7%9B%B8%E5%BD%93%E4%BA%8E%20GBDT%20%E5%81%9A%E4%BA%86%E5%89%8D%E7%BB%AD%E7%9A%84%E7%89%B9%E5%BE%81%E7%BB%84%E5%90%88%E5%B7%A5%E4%BD%9C%EF%BC%8CLR%20%E5%81%9A%E4%BA%86%E6%9C%80%E5%90%8E%E7%9A%84%E5%8D%95%E5%B1%82%20MLP%20%E5%B7%A5%E4%BD%9C%EF%BC%8C%E4%BD%86%E6%98%AF%E6%9C%AC%E8%BA%AB%E5%83%8F%20GBDT%20%E8%BF%99%E7%A7%8D%E6%A0%91%E6%A8%A1%E5%9E%8B%E5%85%B6%E5%AE%9E%E5%BE%88%E9%9A%BE%E5%A4%84%E7%90%86%20id%20%E7%B1%BB%E7%9A%84%E7%89%B9%E5%BE%81%EF%BC%88%E9%82%A3%E5%B0%B1%E5%AF%B9%20CTR%20%E9%A2%84%E4%BC%B0%E9%87%8C%E9%9D%A2%E7%9A%84%E5%8E%86%E5%8F%B2%E5%85%B4%E8%B6%A3%E5%BB%BA%E6%A8%A1%E6%97%A0%E8%83%BD%E4%B8%BA%E5%8A%9B%E4%BA%86%EF%BC%89%EF%BC%8C%E5%8F%AA%E4%B8%8D%E8%BF%87%E5%A6%82%E6%9E%9C%E6%9C%89%E4%B8%80%E4%B8%AA%E9%A1%B9%E7%9B%AE%E9%9C%80%E8%A6%81%E5%BF%AB%E9%80%9F%E4%B8%8A%E7%BA%BF%E7%9A%84%E6%97%B6%E5%80%99%EF%BC%8CGBDT%20%E5%BE%80%E5%BE%80%E8%83%BD%E5%BE%97%E5%88%B0%E4%B8%80%E4%B8%AA%E5%BF%AB%E9%80%9F%E7%9A%84%EF%BC%8C%E6%8E%A5%E8%BF%91%2070%20%E5%88%86%E7%9A%84%E6%95%88%E6%9E%9C))
  - 📝 GBDT+LR 方案的基本思路

- > **NFM：Neural Factorization Machines**

核心思想是 inputs 进入 DNN 之前先进 FM layer 进行预处理  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=NFM%EF%BC%9ANeural%20Factorization%20Machines%E6%A0%B8%E5%BF%83%E6%80%9D%E6%83%B3%E6%98%AF%20inputs%20%E8%BF%9B%E5%85%A5%20DNN%20%E4%B9%8B%E5%89%8D%E5%85%88%E8%BF%9B%20FM%20layer%20%E8%BF%9B%E8%A1%8C%E9%A2%84%E5%A4%84%E7%90%86))

- > ![](https://pic4.zhimg.com/v2-8f8f48d29d477fa2003c286ea7d9030f_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic4.zhimg.com/v2-8f8f48d29d477fa2003c286ea7d9030f_r.jpg))
  - 📝 NFM 的结构示意图

- > ![](https://pic3.zhimg.com/v2-d80c5c00c0ab8805762821400eb5046a_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic3.zhimg.com/v2-d80c5c00c0ab8805762821400eb5046a_r.jpg))
  - 📝 AFM 的示意图

- > 核心思想是在 NFM 的基础上，增加 attention 的机制，相当于对于 interacted vector 再进行 weighted sum。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E6%A0%B8%E5%BF%83%E6%80%9D%E6%83%B3%E6%98%AF%E5%9C%A8%20NFM%20%E7%9A%84%E5%9F%BA%E7%A1%80%E4%B8%8A%EF%BC%8C%E5%A2%9E%E5%8A%A0%20attention%20%E7%9A%84%E6%9C%BA%E5%88%B6%EF%BC%8C%E7%9B%B8%E5%BD%93%E4%BA%8E%E5%AF%B9%E4%BA%8E%20interacted%20vector%20%E5%86%8D%E8%BF%9B%E8%A1%8C%20weighted%20sum%E3%80%82))
  - 📝 AFM 的基本思想

- > PNN 的主体思想在于 embedding 之后对下一层输入两个结果，一个是原始的 embedding vector，另一个是 product 之后的结果  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=PNN%20%E7%9A%84%E4%B8%BB%E4%BD%93%E6%80%9D%E6%83%B3%E5%9C%A8%E4%BA%8E%20embedding%20%E4%B9%8B%E5%90%8E%E5%AF%B9%E4%B8%8B%E4%B8%80%E5%B1%82%E8%BE%93%E5%85%A5%E4%B8%A4%E4%B8%AA%E7%BB%93%E6%9E%9C%EF%BC%8C%E4%B8%80%E4%B8%AA%E6%98%AF%E5%8E%9F%E5%A7%8B%E7%9A%84%20embedding%20vector%EF%BC%8C%E5%8F%A6%E4%B8%80%E4%B8%AA%E6%98%AF%20product%20%E4%B9%8B%E5%90%8E%E7%9A%84%E7%BB%93%E6%9E%9C))
  - 📝 PNN  的基本思想

- > ![](https://pic4.zhimg.com/v2-32b686cde62f520d126da751a42bf827_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic4.zhimg.com/v2-32b686cde62f520d126da751a42bf827_r.jpg))
  - 📝 PNN 的示意图

- > 多任务模型一般面临几个问题：

*   哪些任务组合，任务是否可以组合（比如常见的任务有是否点击视频 + 观看视频时长，是否购买 + 购买 GMV，点击 + 购买）
*   多任务之间组合会不会出现负向的效果？
*   多任务如何组合？loss 相加？分别训练然后 share embedding？  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E5%A4%9A%E4%BB%BB%E5%8A%A1%E6%A8%A1%E5%9E%8B%E4%B8%80%E8%88%AC%E9%9D%A2%E4%B8%B4%E5%87%A0%E4%B8%AA%E9%97%AE%E9%A2%98%EF%BC%9A%E5%93%AA%E4%BA%9B%E4%BB%BB%E5%8A%A1%E7%BB%84%E5%90%88%EF%BC%8C%E4%BB%BB%E5%8A%A1%E6%98%AF%E5%90%A6%E5%8F%AF%E4%BB%A5%E7%BB%84%E5%90%88%EF%BC%88%E6%AF%94%E5%A6%82%E5%B8%B8%E8%A7%81%E7%9A%84%E4%BB%BB%E5%8A%A1%E6%9C%89%E6%98%AF%E5%90%A6%E7%82%B9%E5%87%BB%E8%A7%86%E9%A2%91%20+%20%E8%A7%82%E7%9C%8B%E8%A7%86%E9%A2%91%E6%97%B6%E9%95%BF%EF%BC%8C%E6%98%AF%E5%90%A6%E8%B4%AD%E4%B9%B0%20+%20%E8%B4%AD%E4%B9%B0%20GMV%EF%BC%8C%E7%82%B9%E5%87%BB%20+%20%E8%B4%AD%E4%B9%B0%EF%BC%89%E5%A4%9A%E4%BB%BB%E5%8A%A1%E4%B9%8B%E9%97%B4%E7%BB%84%E5%90%88%E4%BC%9A%E4%B8%8D%E4%BC%9A%E5%87%BA%E7%8E%B0%E8%B4%9F%E5%90%91%E7%9A%84%E6%95%88%E6%9E%9C%EF%BC%9F%E5%A4%9A%E4%BB%BB%E5%8A%A1%E5%A6%82%E4%BD%95%E7%BB%84%E5%90%88%EF%BC%9Floss%20%E7%9B%B8%E5%8A%A0%EF%BC%9F%E5%88%86%E5%88%AB%E8%AE%AD%E7%BB%83%E7%84%B6%E5%90%8E%20share%20embedding%EF%BC%9F))
  - 📝 推荐多任务学习的一般性问题

- > ![](https://pic4.zhimg.com/v2-10238dd616feab09781a3f4ee5742357_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic4.zhimg.com/v2-10238dd616feab09781a3f4ee5742357_r.jpg))
  - 📝 DeepMCP 的示意图

- > 这里面整体的思想在于，三个部分 share embedding，各自学习自己的子任务，通过 share 部分的 layer 的参数来对彼此有正向的影响  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E8%BF%99%E9%87%8C%E9%9D%A2%E6%95%B4%E4%BD%93%E7%9A%84%E6%80%9D%E6%83%B3%E5%9C%A8%E4%BA%8E%EF%BC%8C%E4%B8%89%E4%B8%AA%E9%83%A8%E5%88%86%20share%20embedding%EF%BC%8C%E5%90%84%E8%87%AA%E5%AD%A6%E4%B9%A0%E8%87%AA%E5%B7%B1%E7%9A%84%E5%AD%90%E4%BB%BB%E5%8A%A1%EF%BC%8C%E9%80%9A%E8%BF%87%20share%20%E9%83%A8%E5%88%86%E7%9A%84%20layer%20%E7%9A%84%E5%8F%82%E6%95%B0%E6%9D%A5%E5%AF%B9%E5%BD%BC%E6%AD%A4%E6%9C%89%E6%AD%A3%E5%90%91%E7%9A%84%E5%BD%B1%E5%93%8D))
  - 📝 DeepMCP 的基本思路，也是多任务学习的一种基本思路

- > ![](https://pic2.zhimg.com/v2-8c058aad539b84de73f76f0d39b1dda9_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic2.zhimg.com/v2-8c058aad539b84de73f76f0d39b1dda9_r.jpg))
  - 📝 ESMM 的示意图

- > 核心就是点击和购买这两个行为之间存在时序关系，通过贝叶斯方法来建模点击，转化，点击然后转化这三个结果  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E6%A0%B8%E5%BF%83%E5%B0%B1%E6%98%AF%E7%82%B9%E5%87%BB%E5%92%8C%E8%B4%AD%E4%B9%B0%E8%BF%99%E4%B8%A4%E4%B8%AA%E8%A1%8C%E4%B8%BA%E4%B9%8B%E9%97%B4%E5%AD%98%E5%9C%A8%E6%97%B6%E5%BA%8F%E5%85%B3%E7%B3%BB%EF%BC%8C%E9%80%9A%E8%BF%87%E8%B4%9D%E5%8F%B6%E6%96%AF%E6%96%B9%E6%B3%95%E6%9D%A5%E5%BB%BA%E6%A8%A1%E7%82%B9%E5%87%BB%EF%BC%8C%E8%BD%AC%E5%8C%96%EF%BC%8C%E7%82%B9%E5%87%BB%E7%84%B6%E5%90%8E%E8%BD%AC%E5%8C%96%E8%BF%99%E4%B8%89%E4%B8%AA%E7%BB%93%E6%9E%9C))
  - 📝 ESMM 的核心思想

- > ![](https://pic3.zhimg.com/v2-afeba333092ad7aae992bc1bba131bee_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic3.zhimg.com/v2-afeba333092ad7aae992bc1bba131bee_r.jpg))
  - 📝 MOE 的示意图

- > MOE 就是分为多个 expert 网络，用一个 Gate 网络来确定 n 个 expert 上的概率分布，最后将 n 个 expert 上的结果组合起来

MMOE 就是多个 expert 网络和多个 gate 网络（gate 网络的数量 = task 的数量）  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=MOE%20%E5%B0%B1%E6%98%AF%E5%88%86%E4%B8%BA%E5%A4%9A%E4%B8%AA%20expert%20%E7%BD%91%E7%BB%9C%EF%BC%8C%E7%94%A8%E4%B8%80%E4%B8%AA%20Gate%20%E7%BD%91%E7%BB%9C%E6%9D%A5%E7%A1%AE%E5%AE%9A%20n%20%E4%B8%AA%20expert%20%E4%B8%8A%E7%9A%84%E6%A6%82%E7%8E%87%E5%88%86%E5%B8%83%EF%BC%8C%E6%9C%80%E5%90%8E%E5%B0%86%20n%20%E4%B8%AA%20expert%20%E4%B8%8A%E7%9A%84%E7%BB%93%E6%9E%9C%E7%BB%84%E5%90%88%E8%B5%B7%E6%9D%A5MMOE%20%E5%B0%B1%E6%98%AF%E5%A4%9A%E4%B8%AA%20expert%20%E7%BD%91%E7%BB%9C%E5%92%8C%E5%A4%9A%E4%B8%AA%20gate%20%E7%BD%91%E7%BB%9C%EF%BC%88gate%20%E7%BD%91%E7%BB%9C%E7%9A%84%E6%95%B0%E9%87%8F%20=%20task%20%E7%9A%84%E6%95%B0%E9%87%8F%EF%BC%89))

- > AutoInt 这个模型相当于在特征交互层用 self attention。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=AutoInt%20%E8%BF%99%E4%B8%AA%E6%A8%A1%E5%9E%8B%E7%9B%B8%E5%BD%93%E4%BA%8E%E5%9C%A8%E7%89%B9%E5%BE%81%E4%BA%A4%E4%BA%92%E5%B1%82%E7%94%A8%20self%20attention%E3%80%82))

- > ![](https://pic1.zhimg.com/v2-4fd085df8fc4b999e24426f433222034_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic1.zhimg.com/v2-4fd085df8fc4b999e24426f433222034_r.jpg))
  - 📝 FiBiNet 示意图

- > **AutoFis**

相当于在 interaction 之后增加一个 gate，选择那些 interaction 的结果可以到下一层  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=AutoFis%E7%9B%B8%E5%BD%93%E4%BA%8E%E5%9C%A8%20interaction%20%E4%B9%8B%E5%90%8E%E5%A2%9E%E5%8A%A0%E4%B8%80%E4%B8%AA%20gate%EF%BC%8C%E9%80%89%E6%8B%A9%E9%82%A3%E4%BA%9B%20interaction%20%E7%9A%84%E7%BB%93%E6%9E%9C%E5%8F%AF%E4%BB%A5%E5%88%B0%E4%B8%8B%E4%B8%80%E5%B1%82))
  - 📝 AuoFIS 的基本思想

- > ![](https://pic1.zhimg.com/v2-aaebda7ea378429a4e7e9cceffa85cb4_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic1.zhimg.com/v2-aaebda7ea378429a4e7e9cceffa85cb4_r.jpg))
  - 📝 AutoFIS 的示意图

- > *   RNN 方式：将序列信息建模于 RNN 的 hidden state 中
*   Aggregation 方式：相当于不会在模型结构上考虑序列的时间信息，而是用各种 pooling 或者 attention 的方法去聚合用户的历史交互行为  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=RNN%20%E6%96%B9%E5%BC%8F%EF%BC%9A%E5%B0%86%E5%BA%8F%E5%88%97%E4%BF%A1%E6%81%AF%E5%BB%BA%E6%A8%A1%E4%BA%8E%20RNN%20%E7%9A%84%20hidden%20state%20%E4%B8%ADAggregation%20%E6%96%B9%E5%BC%8F%EF%BC%9A%E7%9B%B8%E5%BD%93%E4%BA%8E%E4%B8%8D%E4%BC%9A%E5%9C%A8%E6%A8%A1%E5%9E%8B%E7%BB%93%E6%9E%84%E4%B8%8A%E8%80%83%E8%99%91%E5%BA%8F%E5%88%97%E7%9A%84%E6%97%B6%E9%97%B4%E4%BF%A1%E6%81%AF%EF%BC%8C%E8%80%8C%E6%98%AF%E7%94%A8%E5%90%84%E7%A7%8D%20pooling%20%E6%88%96%E8%80%85%20attention%20%E7%9A%84%E6%96%B9%E6%B3%95%E5%8E%BB%E8%81%9A%E5%90%88%E7%94%A8%E6%88%B7%E7%9A%84%E5%8E%86%E5%8F%B2%E4%BA%A4%E4%BA%92%E8%A1%8C%E4%B8%BA))
  - 📝 序列建模的两种基本思路

- > ![](https://pic1.zhimg.com/v2-e457401f9c7a5dfe592f145cb8ca76ac_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic1.zhimg.com/v2-e457401f9c7a5dfe592f145cb8ca76ac_r.jpg))
  - 📝 DIN 的示意图

- > 这个思想跟 attention 的思想非常接近，所以 DIN 用候选商品作为 query，历史商品作为 key，计算历史商品和候选商品的相似性作为历史商品的权重，将加权后的历史商品 sum pooling 后输入到模型  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E8%BF%99%E4%B8%AA%E6%80%9D%E6%83%B3%E8%B7%9F%20attention%20%E7%9A%84%E6%80%9D%E6%83%B3%E9%9D%9E%E5%B8%B8%E6%8E%A5%E8%BF%91%EF%BC%8C%E6%89%80%E4%BB%A5%20DIN%20%E7%94%A8%E5%80%99%E9%80%89%E5%95%86%E5%93%81%E4%BD%9C%E4%B8%BA%20query%EF%BC%8C%E5%8E%86%E5%8F%B2%E5%95%86%E5%93%81%E4%BD%9C%E4%B8%BA%20key%EF%BC%8C%E8%AE%A1%E7%AE%97%E5%8E%86%E5%8F%B2%E5%95%86%E5%93%81%E5%92%8C%E5%80%99%E9%80%89%E5%95%86%E5%93%81%E7%9A%84%E7%9B%B8%E4%BC%BC%E6%80%A7%E4%BD%9C%E4%B8%BA%E5%8E%86%E5%8F%B2%E5%95%86%E5%93%81%E7%9A%84%E6%9D%83%E9%87%8D%EF%BC%8C%E5%B0%86%E5%8A%A0%E6%9D%83%E5%90%8E%E7%9A%84%E5%8E%86%E5%8F%B2%E5%95%86%E5%93%81%20sum%20pooling%20%E5%90%8E%E8%BE%93%E5%85%A5%E5%88%B0%E6%A8%A1%E5%9E%8B))
  - 📝 DIN 的核心思想就是对注意力的使用了

- > Dice 可以看做是 PReLU 的一种推广，主要思想是依据输入数据分布进行自适应调整修正点，该修正点不再默认为 0，而是设定为数据均值；其次，Dice 的一个好处是平滑过渡两个状态。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=Dice%20%E5%8F%AF%E4%BB%A5%E7%9C%8B%E5%81%9A%E6%98%AF%20PReLU%20%E7%9A%84%E4%B8%80%E7%A7%8D%E6%8E%A8%E5%B9%BF%EF%BC%8C%E4%B8%BB%E8%A6%81%E6%80%9D%E6%83%B3%E6%98%AF%E4%BE%9D%E6%8D%AE%E8%BE%93%E5%85%A5%E6%95%B0%E6%8D%AE%E5%88%86%E5%B8%83%E8%BF%9B%E8%A1%8C%E8%87%AA%E9%80%82%E5%BA%94%E8%B0%83%E6%95%B4%E4%BF%AE%E6%AD%A3%E7%82%B9%EF%BC%8C%E8%AF%A5%E4%BF%AE%E6%AD%A3%E7%82%B9%E4%B8%8D%E5%86%8D%E9%BB%98%E8%AE%A4%E4%B8%BA%200%EF%BC%8C%E8%80%8C%E6%98%AF%E8%AE%BE%E5%AE%9A%E4%B8%BA%E6%95%B0%E6%8D%AE%E5%9D%87%E5%80%BC%EF%BC%9B%E5%85%B6%E6%AC%A1%EF%BC%8CDice%20%E7%9A%84%E4%B8%80%E4%B8%AA%E5%A5%BD%E5%A4%84%E6%98%AF%E5%B9%B3%E6%BB%91%E8%BF%87%E6%B8%A1%E4%B8%A4%E4%B8%AA%E7%8A%B6%E6%80%81%E3%80%82))
  - 📝 DIN 的另一点创新点：DICE 激活函数

- > ![](https://pic3.zhimg.com/v2-1a58deff89577e1fa30576876661e79e_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=https://pic3.zhimg.com/v2-1a58deff89577e1fa30576876661e79e_r.jpg))
  - 📝 DIEN 的模型结构图

- > 有一个经典的问题就是热门 item 的问题，就是传说中的 2-8 定律，20% 的热门 item 占据了 80% 的曝光量，所以导致正样本中大部分都是热门的 item，而召回中常常需要解决这部分热门 item（咦我不是在讲精排吗？），如果不降低召回中的热门 item，那么召回的个性化就无从谈起，常见的样本层面的做法就是正样本里面减少热门样本，或者负样本并不进行随机负采样，而是根据样本的热门程度进行采样，相当于通过在负样本中热门样本的采样来” 抵消 “正样本中的热门样本的影响  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E6%9C%89%E4%B8%80%E4%B8%AA%E7%BB%8F%E5%85%B8%E7%9A%84%E9%97%AE%E9%A2%98%E5%B0%B1%E6%98%AF%E7%83%AD%E9%97%A8%20item%20%E7%9A%84%E9%97%AE%E9%A2%98%EF%BC%8C%E5%B0%B1%E6%98%AF%E4%BC%A0%E8%AF%B4%E4%B8%AD%E7%9A%84%202-8%20%E5%AE%9A%E5%BE%8B%EF%BC%8C20%25%20%E7%9A%84%E7%83%AD%E9%97%A8%20item%20%E5%8D%A0%E6%8D%AE%E4%BA%86%2080%25%20%E7%9A%84%E6%9B%9D%E5%85%89%E9%87%8F%EF%BC%8C%E6%89%80%E4%BB%A5%E5%AF%BC%E8%87%B4%E6%AD%A3%E6%A0%B7%E6%9C%AC%E4%B8%AD%E5%A4%A7%E9%83%A8%E5%88%86%E9%83%BD%E6%98%AF%E7%83%AD%E9%97%A8%E7%9A%84%20item%EF%BC%8C%E8%80%8C%E5%8F%AC%E5%9B%9E%E4%B8%AD%E5%B8%B8%E5%B8%B8%E9%9C%80%E8%A6%81%E8%A7%A3%E5%86%B3%E8%BF%99%E9%83%A8%E5%88%86%E7%83%AD%E9%97%A8%20item%EF%BC%88%E5%92%A6%E6%88%91%E4%B8%8D%E6%98%AF%E5%9C%A8%E8%AE%B2%E7%B2%BE%E6%8E%92%E5%90%97%EF%BC%9F%EF%BC%89%EF%BC%8C%E5%A6%82%E6%9E%9C%E4%B8%8D%E9%99%8D%E4%BD%8E%E5%8F%AC%E5%9B%9E%E4%B8%AD%E7%9A%84%E7%83%AD%E9%97%A8%20item%EF%BC%8C%E9%82%A3%E4%B9%88%E5%8F%AC%E5%9B%9E%E7%9A%84%E4%B8%AA%E6%80%A7%E5%8C%96%E5%B0%B1%E6%97%A0%E4%BB%8E%E8%B0%88%E8%B5%B7%EF%BC%8C%E5%B8%B8%E8%A7%81%E7%9A%84%E6%A0%B7%E6%9C%AC%E5%B1%82%E9%9D%A2%E7%9A%84%E5%81%9A%E6%B3%95%E5%B0%B1%E6%98%AF%E6%AD%A3%E6%A0%B7%E6%9C%AC%E9%87%8C%E9%9D%A2%E5%87%8F%E5%B0%91%E7%83%AD%E9%97%A8%E6%A0%B7%E6%9C%AC%EF%BC%8C%E6%88%96%E8%80%85%E8%B4%9F%E6%A0%B7%E6%9C%AC%E5%B9%B6%E4%B8%8D%E8%BF%9B%E8%A1%8C%E9%9A%8F%E6%9C%BA%E8%B4%9F%E9%87%87%E6%A0%B7%EF%BC%8C%E8%80%8C%E6%98%AF%E6%A0%B9%E6%8D%AE%E6%A0%B7%E6%9C%AC%E7%9A%84%E7%83%AD%E9%97%A8%E7%A8%8B%E5%BA%A6%E8%BF%9B%E8%A1%8C%E9%87%87%E6%A0%B7%EF%BC%8C%E7%9B%B8%E5%BD%93%E4%BA%8E%E9%80%9A%E8%BF%87%E5%9C%A8%E8%B4%9F%E6%A0%B7%E6%9C%AC%E4%B8%AD%E7%83%AD%E9%97%A8%E6%A0%B7%E6%9C%AC%E7%9A%84%E9%87%87%E6%A0%B7%E6%9D%A5%E2%80%9D%20%E6%8A%B5%E6%B6%88%20%E2%80%9C%E6%AD%A3%E6%A0%B7%E6%9C%AC%E4%B8%AD%E7%9A%84%E7%83%AD%E9%97%A8%E6%A0%B7%E6%9C%AC%E7%9A%84%E5%BD%B1%E5%93%8D))
  - 📝 推荐曝光也符合[[二八定律]]，因此
  - 📝 1. 在召回阶段就需要对热门商品做打压
  - 📝 2. 在挑选精排的数据集时，需要对热门商品进行[[降采样]]。

- > 你想做什么和你选择什么样的 label 问题，如果是在典型的 CTR 场景里面似乎非常简单，直接将点击作为正例，曝光未点击作为负例即可，但是如果是其他场景，比如建模用户的留存呢？是应该次日回访、三天回访、次月回访作为留存，还是应该拿什么作为 label 呢？比如建模用户的推送时机，正负例又应该是什么？  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E4%BD%A0%E6%83%B3%E5%81%9A%E4%BB%80%E4%B9%88%E5%92%8C%E4%BD%A0%E9%80%89%E6%8B%A9%E4%BB%80%E4%B9%88%E6%A0%B7%E7%9A%84%20label%20%E9%97%AE%E9%A2%98%EF%BC%8C%E5%A6%82%E6%9E%9C%E6%98%AF%E5%9C%A8%E5%85%B8%E5%9E%8B%E7%9A%84%20CTR%20%E5%9C%BA%E6%99%AF%E9%87%8C%E9%9D%A2%E4%BC%BC%E4%B9%8E%E9%9D%9E%E5%B8%B8%E7%AE%80%E5%8D%95%EF%BC%8C%E7%9B%B4%E6%8E%A5%E5%B0%86%E7%82%B9%E5%87%BB%E4%BD%9C%E4%B8%BA%E6%AD%A3%E4%BE%8B%EF%BC%8C%E6%9B%9D%E5%85%89%E6%9C%AA%E7%82%B9%E5%87%BB%E4%BD%9C%E4%B8%BA%E8%B4%9F%E4%BE%8B%E5%8D%B3%E5%8F%AF%EF%BC%8C%E4%BD%86%E6%98%AF%E5%A6%82%E6%9E%9C%E6%98%AF%E5%85%B6%E4%BB%96%E5%9C%BA%E6%99%AF%EF%BC%8C%E6%AF%94%E5%A6%82%E5%BB%BA%E6%A8%A1%E7%94%A8%E6%88%B7%E7%9A%84%E7%95%99%E5%AD%98%E5%91%A2%EF%BC%9F%E6%98%AF%E5%BA%94%E8%AF%A5%E6%AC%A1%E6%97%A5%E5%9B%9E%E8%AE%BF%E3%80%81%E4%B8%89%E5%A4%A9%E5%9B%9E%E8%AE%BF%E3%80%81%E6%AC%A1%E6%9C%88%E5%9B%9E%E8%AE%BF%E4%BD%9C%E4%B8%BA%E7%95%99%E5%AD%98%EF%BC%8C%E8%BF%98%E6%98%AF%E5%BA%94%E8%AF%A5%E6%8B%BF%E4%BB%80%E4%B9%88%E4%BD%9C%E4%B8%BA%20label%20%E5%91%A2%EF%BC%9F%E6%AF%94%E5%A6%82%E5%BB%BA%E6%A8%A1%E7%94%A8%E6%88%B7%E7%9A%84%E6%8E%A8%E9%80%81%E6%97%B6%E6%9C%BA%EF%BC%8C%E6%AD%A3%E8%B4%9F%E4%BE%8B%E5%8F%88%E5%BA%94%E8%AF%A5%E6%98%AF%E4%BB%80%E4%B9%88%EF%BC%9F))
  - 📝 数据及标签随业务目标而定。

- > **用户群体 bias：**

大部分产品都会有自己的大盘用户，举个例子，假设头条用户大部分都是中老年人（可能并不是，只是举例），这时候一个年轻人过来，从冷启开始推荐系统可能就会给他推荐大盘用户喜欢的文章，他喜欢的文章一直都没有机会展示给他，后续推荐系统对他的偏好的猜测也会受整体大盘用户的影响，导致新来的用户根本接不住，这是产品做用户增长和拓宽自己用户群体常见的问题。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/401775395#js_content:~:text=%E7%94%A8%E6%88%B7%E7%BE%A4%E4%BD%93%20bias%EF%BC%9A%E5%A4%A7%E9%83%A8%E5%88%86%E4%BA%A7%E5%93%81%E9%83%BD%E4%BC%9A%E6%9C%89%E8%87%AA%E5%B7%B1%E7%9A%84%E5%A4%A7%E7%9B%98%E7%94%A8%E6%88%B7%EF%BC%8C%E4%B8%BE%E4%B8%AA%E4%BE%8B%E5%AD%90%EF%BC%8C%E5%81%87%E8%AE%BE%E5%A4%B4%E6%9D%A1%E7%94%A8%E6%88%B7%E5%A4%A7%E9%83%A8%E5%88%86%E9%83%BD%E6%98%AF%E4%B8%AD%E8%80%81%E5%B9%B4%E4%BA%BA%EF%BC%88%E5%8F%AF%E8%83%BD%E5%B9%B6%E4%B8%8D%E6%98%AF%EF%BC%8C%E5%8F%AA%E6%98%AF%E4%B8%BE%E4%BE%8B%EF%BC%89%EF%BC%8C%E8%BF%99%E6%97%B6%E5%80%99%E4%B8%80%E4%B8%AA%E5%B9%B4%E8%BD%BB%E4%BA%BA%E8%BF%87%E6%9D%A5%EF%BC%8C%E4%BB%8E%E5%86%B7%E5%90%AF%E5%BC%80%E5%A7%8B%E6%8E%A8%E8%8D%90%E7%B3%BB%E7%BB%9F%E5%8F%AF%E8%83%BD%E5%B0%B1%E4%BC%9A%E7%BB%99%E4%BB%96%E6%8E%A8%E8%8D%90%E5%A4%A7%E7%9B%98%E7%94%A8%E6%88%B7%E5%96%9C%E6%AC%A2%E7%9A%84%E6%96%87%E7%AB%A0%EF%BC%8C%E4%BB%96%E5%96%9C%E6%AC%A2%E7%9A%84%E6%96%87%E7%AB%A0%E4%B8%80%E7%9B%B4%E9%83%BD%E6%B2%A1%E6%9C%89%E6%9C%BA%E4%BC%9A%E5%B1%95%E7%A4%BA%E7%BB%99%E4%BB%96%EF%BC%8C%E5%90%8E%E7%BB%AD%E6%8E%A8%E8%8D%90%E7%B3%BB%E7%BB%9F%E5%AF%B9%E4%BB%96%E7%9A%84%E5%81%8F%E5%A5%BD%E7%9A%84%E7%8C%9C%E6%B5%8B%E4%B9%9F%E4%BC%9A%E5%8F%97%E6%95%B4%E4%BD%93%E5%A4%A7%E7%9B%98%E7%94%A8%E6%88%B7%E7%9A%84%E5%BD%B1%E5%93%8D%EF%BC%8C%E5%AF%BC%E8%87%B4%E6%96%B0%E6%9D%A5%E7%9A%84%E7%94%A8%E6%88%B7%E6%A0%B9%E6%9C%AC%E6%8E%A5%E4%B8%8D%E4%BD%8F%EF%BC%8C%E8%BF%99%E6%98%AF%E4%BA%A7%E5%93%81%E5%81%9A%E7%94%A8%E6%88%B7%E5%A2%9E%E9%95%BF%E5%92%8C%E6%8B%93%E5%AE%BD%E8%87%AA%E5%B7%B1%E7%94%A8%E6%88%B7%E7%BE%A4%E4%BD%93%E5%B8%B8%E8%A7%81%E7%9A%84%E9%97%AE%E9%A2%98%E3%80%82))
  - 📝 群体 bias 可能导致推荐不准

