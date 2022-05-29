title:: 【Reading Highlights】推荐系统里，你是怎么 Embedding 的？
source:: https://zhuanlan.zhihu.com/p/397600084
summary:: 
tags:: [[简悦]] [[embedding]]   [[reading_highlights]]
date:: 20220529  

- > 先看下什么是好的 encoding?

**唯一性 (U):** 好的 encoding 对每一个不同的特征编码都要是唯一的. 如果这个保证不了, 后续的 decoding 就没办法区分不同的特征了, 那模型效果也大打折扣.

**相似性 (E-S)**: 有唯一性并不足够, 相似特征编码后也要足够相似. 比如二进制编码, 8(1000) 和 9(1001) 就比 8(1000) 和 7(0111) 看着相似, 这就会给模型带来困扰, 误导后面的 decoding 过程.

**高维性 (H-D):** 这个很容易理解, 越高维区分度越高, 极端情况就是 one-hot 了, 区分度最强.

**高熵性 (H-E)**: 众所周知, 熵越高信息量越高, 我们肯定不希望有哪一位编码是冗余的.  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/397600084#js_content:~:text=%E5%85%88%E7%9C%8B%E4%B8%8B%E4%BB%80%E4%B9%88%E6%98%AF%E5%A5%BD%E7%9A%84%20encoding?%E5%94%AF%E4%B8%80%E6%80%A7%20(U):%20%E5%A5%BD%E7%9A%84%20encoding%20%E5%AF%B9%E6%AF%8F%E4%B8%80%E4%B8%AA%E4%B8%8D%E5%90%8C%E7%9A%84%E7%89%B9%E5%BE%81%E7%BC%96%E7%A0%81%E9%83%BD%E8%A6%81%E6%98%AF%E5%94%AF%E4%B8%80%E7%9A%84.%20%E5%A6%82%E6%9E%9C%E8%BF%99%E4%B8%AA%E4%BF%9D%E8%AF%81%E4%B8%8D%E4%BA%86,%20%E5%90%8E%E7%BB%AD%E7%9A%84%20decoding%20%E5%B0%B1%E6%B2%A1%E5%8A%9E%E6%B3%95%E5%8C%BA%E5%88%86%E4%B8%8D%E5%90%8C%E7%9A%84%E7%89%B9%E5%BE%81%E4%BA%86,%20%E9%82%A3%E6%A8%A1%E5%9E%8B%E6%95%88%E6%9E%9C%E4%B9%9F%E5%A4%A7%E6%89%93%E6%8A%98%E6%89%A3.%E7%9B%B8%E4%BC%BC%E6%80%A7%20(E-S):%20%E6%9C%89%E5%94%AF%E4%B8%80%E6%80%A7%E5%B9%B6%E4%B8%8D%E8%B6%B3%E5%A4%9F,%20%E7%9B%B8%E4%BC%BC%E7%89%B9%E5%BE%81%E7%BC%96%E7%A0%81%E5%90%8E%E4%B9%9F%E8%A6%81%E8%B6%B3%E5%A4%9F%E7%9B%B8%E4%BC%BC.%20%E6%AF%94%E5%A6%82%E4%BA%8C%E8%BF%9B%E5%88%B6%E7%BC%96%E7%A0%81,%208(1000)%20%E5%92%8C%209(1001)%20%E5%B0%B1%E6%AF%94%208(1000)%20%E5%92%8C%207(0111)%20%E7%9C%8B%E7%9D%80%E7%9B%B8%E4%BC%BC,%20%E8%BF%99%E5%B0%B1%E4%BC%9A%E7%BB%99%E6%A8%A1%E5%9E%8B%E5%B8%A6%E6%9D%A5%E5%9B%B0%E6%89%B0,%20%E8%AF%AF%E5%AF%BC%E5%90%8E%E9%9D%A2%E7%9A%84%20decoding%20%E8%BF%87%E7%A8%8B.%E9%AB%98%E7%BB%B4%E6%80%A7%20(H-D):%20%E8%BF%99%E4%B8%AA%E5%BE%88%E5%AE%B9%E6%98%93%E7%90%86%E8%A7%A3,%20%E8%B6%8A%E9%AB%98%E7%BB%B4%E5%8C%BA%E5%88%86%E5%BA%A6%E8%B6%8A%E9%AB%98,%20%E6%9E%81%E7%AB%AF%E6%83%85%E5%86%B5%E5%B0%B1%E6%98%AF%20one-hot%20%E4%BA%86,%20%E5%8C%BA%E5%88%86%E5%BA%A6%E6%9C%80%E5%BC%BA.%E9%AB%98%E7%86%B5%E6%80%A7%20(H-E):%20%E4%BC%97%E6%89%80%E5%91%A8%E7%9F%A5,%20%E7%86%B5%E8%B6%8A%E9%AB%98%E4%BF%A1%E6%81%AF%E9%87%8F%E8%B6%8A%E9%AB%98,%20%E6%88%91%E4%BB%AC%E8%82%AF%E5%AE%9A%E4%B8%8D%E5%B8%8C%E6%9C%9B%E6%9C%89%E5%93%AA%E4%B8%80%E4%BD%8D%E7%BC%96%E7%A0%81%E6%98%AF%E5%86%97%E4%BD%99%E7%9A%84.))

- > ![](https://pic2.zhimg.com/v2-0feedabd3d49556522ab03d409b87749_r.jpg)  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/397600084#js_content:~:text=https://pic2.zhimg.com/v2-0feedabd3d49556522ab03d409b87749_r.jpg))

