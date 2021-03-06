title:: 【Reading Highlights】特征处理经验
source:: https://zhuanlan.zhihu.com/p/166440574
summary:: 
tags:: [[简悦]] [[特征工程]]   [[reading_highlights]]
date:: 20220529  

- > **2 缺省值（默认值）处理原则**

*   一定要将缺省值和正常值区分开
*   尽可能把缺省值放在一个桶里面处理  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/166440574#js_content:~:text=2%20%E7%BC%BA%E7%9C%81%E5%80%BC%EF%BC%88%E9%BB%98%E8%AE%A4%E5%80%BC%EF%BC%89%E5%A4%84%E7%90%86%E5%8E%9F%E5%88%99%E4%B8%80%E5%AE%9A%E8%A6%81%E5%B0%86%E7%BC%BA%E7%9C%81%E5%80%BC%E5%92%8C%E6%AD%A3%E5%B8%B8%E5%80%BC%E5%8C%BA%E5%88%86%E5%BC%80%E5%B0%BD%E5%8F%AF%E8%83%BD%E6%8A%8A%E7%BC%BA%E7%9C%81%E5%80%BC%E6%94%BE%E5%9C%A8%E4%B8%80%E4%B8%AA%E6%A1%B6%E9%87%8C%E9%9D%A2%E5%A4%84%E7%90%86))
  - 📝 缺失特征的处理原则

- > 分桶的桶数很关键，**等频分桶**一定是可以分布均匀的，关键在区分度，均匀数据应该多桶，数据较少且分布集中应该少桶  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/166440574#js_content:~:text=%E7%AD%89%E9%A2%91%E5%88%86%E6%A1%B6%E5%88%86%E6%A1%B6%E7%9A%84%E6%A1%B6%E6%95%B0%E5%BE%88%E5%85%B3%E9%94%AE%EF%BC%8C%E4%B8%80%E5%AE%9A%E6%98%AF%E5%8F%AF%E4%BB%A5%E5%88%86%E5%B8%83%E5%9D%87%E5%8C%80%E7%9A%84%EF%BC%8C%E5%85%B3%E9%94%AE%E5%9C%A8%E5%8C%BA%E5%88%86%E5%BA%A6%EF%BC%8C%E5%9D%87%E5%8C%80%E6%95%B0%E6%8D%AE%E5%BA%94%E8%AF%A5%E5%A4%9A%E6%A1%B6%EF%BC%8C%E6%95%B0%E6%8D%AE%E8%BE%83%E5%B0%91%E4%B8%94%E5%88%86%E5%B8%83%E9%9B%86%E4%B8%AD%E5%BA%94%E8%AF%A5%E5%B0%91%E6%A1%B6))
  - 📝 分桶的关键是：等频分桶可均匀分布

- > 连续值 -> 离散值，可以将连续值，从小到大排序，进行等频分桶，等频分桶的效果最好，好于等距分桶和熵分桶，通过 GBDT 分桶效果最好，好于等频分桶。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/166440574#js_content:~:text=%E8%BF%9E%E7%BB%AD%E5%80%BC%20-%3E%20%E7%A6%BB%E6%95%A3%E5%80%BC%EF%BC%8C%E5%8F%AF%E4%BB%A5%E5%B0%86%E8%BF%9E%E7%BB%AD%E5%80%BC%EF%BC%8C%E4%BB%8E%E5%B0%8F%E5%88%B0%E5%A4%A7%E6%8E%92%E5%BA%8F%EF%BC%8C%E8%BF%9B%E8%A1%8C%E7%AD%89%E9%A2%91%E5%88%86%E6%A1%B6%EF%BC%8C%E7%AD%89%E9%A2%91%E5%88%86%E6%A1%B6%E7%9A%84%E6%95%88%E6%9E%9C%E6%9C%80%E5%A5%BD%EF%BC%8C%E5%A5%BD%E4%BA%8E%E7%AD%89%E8%B7%9D%E5%88%86%E6%A1%B6%E5%92%8C%E7%86%B5%E5%88%86%E6%A1%B6%EF%BC%8C%E9%80%9A%E8%BF%87%20GBDT%20%E5%88%86%E6%A1%B6%E6%95%88%E6%9E%9C%E6%9C%80%E5%A5%BD%EF%BC%8C%E5%A5%BD%E4%BA%8E%E7%AD%89%E9%A2%91%E5%88%86%E6%A1%B6%E3%80%82))

- > 分桶数量，分桶数量不是一成不变的，是需要考虑模型是否可以学习。依据覆盖率而定，覆盖率高的，多分些，更加精准，覆盖率少的，少分些，模型足够学习  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/166440574#js_content:~:text=%E5%88%86%E6%A1%B6%E6%95%B0%E9%87%8F%EF%BC%8C%E5%88%86%E6%A1%B6%E6%95%B0%E9%87%8F%E4%B8%8D%E6%98%AF%E4%B8%80%E6%88%90%E4%B8%8D%E5%8F%98%E7%9A%84%EF%BC%8C%E6%98%AF%E9%9C%80%E8%A6%81%E8%80%83%E8%99%91%E6%A8%A1%E5%9E%8B%E6%98%AF%E5%90%A6%E5%8F%AF%E4%BB%A5%E5%AD%A6%E4%B9%A0%E3%80%82%E4%BE%9D%E6%8D%AE%E8%A6%86%E7%9B%96%E7%8E%87%E8%80%8C%E5%AE%9A%EF%BC%8C%E8%A6%86%E7%9B%96%E7%8E%87%E9%AB%98%E7%9A%84%EF%BC%8C%E5%A4%9A%E5%88%86%E4%BA%9B%EF%BC%8C%E6%9B%B4%E5%8A%A0%E7%B2%BE%E5%87%86%EF%BC%8C%E8%A6%86%E7%9B%96%E7%8E%87%E5%B0%91%E7%9A%84%EF%BC%8C%E5%B0%91%E5%88%86%E4%BA%9B%EF%BC%8C%E6%A8%A1%E5%9E%8B%E8%B6%B3%E5%A4%9F%E5%AD%A6%E4%B9%A0))
  - 📝 覆盖率高的特征，分桶可以多一些，精准一些

- > 对于数值型变量 (Numerical Variable)，需要处理离群点，缺失值，异常值等情况。使得特征不命中，或者当成这个特征的空特征来处理，比如 age_null。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/166440574#js_content:~:text=%E5%AF%B9%E4%BA%8E%E6%95%B0%E5%80%BC%E5%9E%8B%E5%8F%98%E9%87%8F%20(Numerical%20Variable)%EF%BC%8C%E9%9C%80%E8%A6%81%E5%A4%84%E7%90%86%E7%A6%BB%E7%BE%A4%E7%82%B9%EF%BC%8C%E7%BC%BA%E5%A4%B1%E5%80%BC%EF%BC%8C%E5%BC%82%E5%B8%B8%E5%80%BC%E7%AD%89%E6%83%85%E5%86%B5%E3%80%82%E4%BD%BF%E5%BE%97%E7%89%B9%E5%BE%81%E4%B8%8D%E5%91%BD%E4%B8%AD%EF%BC%8C%E6%88%96%E8%80%85%E5%BD%93%E6%88%90%E8%BF%99%E4%B8%AA%E7%89%B9%E5%BE%81%E7%9A%84%E7%A9%BA%E7%89%B9%E5%BE%81%E6%9D%A5%E5%A4%84%E7%90%86%EF%BC%8C%E6%AF%94%E5%A6%82%20age_null%E3%80%82))

