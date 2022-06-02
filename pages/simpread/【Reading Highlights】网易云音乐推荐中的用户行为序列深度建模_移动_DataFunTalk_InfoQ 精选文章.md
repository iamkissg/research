title:: 【Reading Highlights】网易云音乐推荐中的用户行为序列深度建模_移动_DataFunTalk_InfoQ 精选文章
source:: https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share
summary:: 
tags:: [[简悦]] [[网易技术]]  [[推荐指数：一星]]   [[reading_highlights]]
date:: 20220602  

- > 其次一个非常大的不同点在于：商品是不可重复消费的。例如用户购买了一台电视机，可能在较长的一段时间之内，用户没有电视机的需求了。但是对于音乐来说，完全可以重复消费。比如一周之前听过的歌曲，可能今天还在听；昨天听过的歌曲，今天还可以单曲循环；甚至一个月之前一年前的那些老歌，都能拿来反复的进行播放。  ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=%E5%85%B6%E6%AC%A1%E4%B8%80%E4%B8%AA%E9%9D%9E%E5%B8%B8%E5%A4%A7%E7%9A%84%E4%B8%8D%E5%90%8C%E7%82%B9%E5%9C%A8%E4%BA%8E%EF%BC%9A%E5%95%86%E5%93%81%E6%98%AF%E4%B8%8D%E5%8F%AF%E9%87%8D%E5%A4%8D%E6%B6%88%E8%B4%B9%E7%9A%84%E3%80%82%E4%BE%8B%E5%A6%82%E7%94%A8%E6%88%B7%E8%B4%AD%E4%B9%B0%E4%BA%86%E4%B8%80%E5%8F%B0%E7%94%B5%E8%A7%86%E6%9C%BA%EF%BC%8C%E5%8F%AF%E8%83%BD%E5%9C%A8%E8%BE%83%E9%95%BF%E7%9A%84%E4%B8%80%E6%AE%B5%E6%97%B6%E9%97%B4%E4%B9%8B%E5%86%85%EF%BC%8C%E7%94%A8%E6%88%B7%E6%B2%A1%E6%9C%89%E7%94%B5%E8%A7%86%E6%9C%BA%E7%9A%84%E9%9C%80%E6%B1%82%E4%BA%86%E3%80%82%E4%BD%86%E6%98%AF%E5%AF%B9%E4%BA%8E%E9%9F%B3%E4%B9%90%E6%9D%A5%E8%AF%B4%EF%BC%8C%E5%AE%8C%E5%85%A8%E5%8F%AF%E4%BB%A5%E9%87%8D%E5%A4%8D%E6%B6%88%E8%B4%B9%E3%80%82%E6%AF%94%E5%A6%82%E4%B8%80%E5%91%A8%E4%B9%8B%E5%89%8D%E5%90%AC%E8%BF%87%E7%9A%84%E6%AD%8C%E6%9B%B2%EF%BC%8C%E5%8F%AF%E8%83%BD%E4%BB%8A%E5%A4%A9%E8%BF%98%E5%9C%A8%E5%90%AC%EF%BC%9B%E6%98%A8%E5%A4%A9%E5%90%AC%E8%BF%87%E7%9A%84%E6%AD%8C%E6%9B%B2%EF%BC%8C%E4%BB%8A%E5%A4%A9%E8%BF%98%E5%8F%AF%E4%BB%A5%E5%8D%95%E6%9B%B2%E5%BE%AA%E7%8E%AF%EF%BC%9B%E7%94%9A%E8%87%B3%E4%B8%80%E4%B8%AA%E6%9C%88%E4%B9%8B%E5%89%8D%E4%B8%80%E5%B9%B4%E5%89%8D%E7%9A%84%E9%82%A3%E4%BA%9B%E8%80%81%E6%AD%8C%EF%BC%8C%E9%83%BD%E8%83%BD%E6%8B%BF%E6%9D%A5%E5%8F%8D%E5%A4%8D%E7%9A%84%E8%BF%9B%E8%A1%8C%E6%92%AD%E6%94%BE%E3%80%82))
  - 📝 电商推荐与音乐推荐的不同一：可重复消费性

- > 消费一首歌曲的时间成本是远高于点击商品的。可能几秒钟之内就曝光了非常多的商品，并且可以通过浏览商品的图片查看商品的标题。用户就能在短时间之内大致的了解到这些商品。但是歌曲就不一样，用户可能会对歌手有一定的了解。但是在很多情况下，演唱者对用户是陌生的。只有真正的去播放这首歌曲，甚至是需要播放到中间的副歌部分，才能真正感受到这首歌曲，对他的感觉，这就需要 1~2 分钟的消费时间。所以很多时候，用户历史的歌曲消费行为，包含着非常多的信息。  ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=%E6%B6%88%E8%B4%B9%E4%B8%80%E9%A6%96%E6%AD%8C%E6%9B%B2%E7%9A%84%E6%97%B6%E9%97%B4%E6%88%90%E6%9C%AC%E6%98%AF%E8%BF%9C%E9%AB%98%E4%BA%8E%E7%82%B9%E5%87%BB%E5%95%86%E5%93%81%E7%9A%84%E3%80%82%E5%8F%AF%E8%83%BD%E5%87%A0%E7%A7%92%E9%92%9F%E4%B9%8B%E5%86%85%E5%B0%B1%E6%9B%9D%E5%85%89%E4%BA%86%E9%9D%9E%E5%B8%B8%E5%A4%9A%E7%9A%84%E5%95%86%E5%93%81%EF%BC%8C%E5%B9%B6%E4%B8%94%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%E6%B5%8F%E8%A7%88%E5%95%86%E5%93%81%E7%9A%84%E5%9B%BE%E7%89%87%E6%9F%A5%E7%9C%8B%E5%95%86%E5%93%81%E7%9A%84%E6%A0%87%E9%A2%98%E3%80%82%E7%94%A8%E6%88%B7%E5%B0%B1%E8%83%BD%E5%9C%A8%E7%9F%AD%E6%97%B6%E9%97%B4%E4%B9%8B%E5%86%85%E5%A4%A7%E8%87%B4%E7%9A%84%E4%BA%86%E8%A7%A3%E5%88%B0%E8%BF%99%E4%BA%9B%E5%95%86%E5%93%81%E3%80%82%E4%BD%86%E6%98%AF%E6%AD%8C%E6%9B%B2%E5%B0%B1%E4%B8%8D%E4%B8%80%E6%A0%B7%EF%BC%8C%E7%94%A8%E6%88%B7%E5%8F%AF%E8%83%BD%E4%BC%9A%E5%AF%B9%E6%AD%8C%E6%89%8B%E6%9C%89%E4%B8%80%E5%AE%9A%E7%9A%84%E4%BA%86%E8%A7%A3%E3%80%82%E4%BD%86%E6%98%AF%E5%9C%A8%E5%BE%88%E5%A4%9A%E6%83%85%E5%86%B5%E4%B8%8B%EF%BC%8C%E6%BC%94%E5%94%B1%E8%80%85%E5%AF%B9%E7%94%A8%E6%88%B7%E6%98%AF%E9%99%8C%E7%94%9F%E7%9A%84%E3%80%82%E5%8F%AA%E6%9C%89%E7%9C%9F%E6%AD%A3%E7%9A%84%E5%8E%BB%E6%92%AD%E6%94%BE%E8%BF%99%E9%A6%96%E6%AD%8C%E6%9B%B2%EF%BC%8C%E7%94%9A%E8%87%B3%E6%98%AF%E9%9C%80%E8%A6%81%E6%92%AD%E6%94%BE%E5%88%B0%E4%B8%AD%E9%97%B4%E7%9A%84%E5%89%AF%E6%AD%8C%E9%83%A8%E5%88%86%EF%BC%8C%E6%89%8D%E8%83%BD%E7%9C%9F%E6%AD%A3%E6%84%9F%E5%8F%97%E5%88%B0%E8%BF%99%E9%A6%96%E6%AD%8C%E6%9B%B2%EF%BC%8C%E5%AF%B9%E4%BB%96%E7%9A%84%E6%84%9F%E8%A7%89%EF%BC%8C%E8%BF%99%E5%B0%B1%E9%9C%80%E8%A6%81%201~2%20%E5%88%86%E9%92%9F%E7%9A%84%E6%B6%88%E8%B4%B9%E6%97%B6%E9%97%B4%E3%80%82%E6%89%80%E4%BB%A5%E5%BE%88%E5%A4%9A%E6%97%B6%E5%80%99%EF%BC%8C%E7%94%A8%E6%88%B7%E5%8E%86%E5%8F%B2%E7%9A%84%E6%AD%8C%E6%9B%B2%E6%B6%88%E8%B4%B9%E8%A1%8C%E4%B8%BA%EF%BC%8C%E5%8C%85%E5%90%AB%E7%9D%80%E9%9D%9E%E5%B8%B8%E5%A4%9A%E7%9A%84%E4%BF%A1%E6%81%AF%E3%80%82))
  - 📝 电商推荐与音乐推荐的不同二：消费的时间成本不一样

- > ![](https://static001.infoq.cn/resource/image/98/3b/98b49a10b856644d96a955c5fcd3553b.png) [[系统架构]]   ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=https://static001.infoq.cn/resource/image/98/3b/98b49a10b856644d96a955c5fcd3553b.png))
  - 📝 网易云音乐的召回系统架构

- > ![](https://static001.infoq.cn/resource/image/0e/d2/0ec1fb067102ff6ee4768432ebbb33d2.png)  ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=https://static001.infoq.cn/resource/image/0e/d2/0ec1fb067102ff6ee4768432ebbb33d2.png))
  - 📝 网易云音乐的召回模型是基于 Youtebe 的视频召回模型的，两点主要的改进：
  - 📝 1. 使用[[self-attention]]代替 average-pooling，强调歌曲间的相关性
  - 📝 2. 用点击序列代替了搜索序列

- > ![](https://static001.infoq.cn/resource/image/28/1e/28845b96fa43f61e84a332e15cbe521e.png)  ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=https://static001.infoq.cn/resource/image/28/1e/28845b96fa43f61e84a332e15cbe521e.png))

- > ![](https://static001.infoq.cn/resource/image/39/46/390b162455679702eca3e3ce08e1da46.png)  ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=https://static001.infoq.cn/resource/image/39/46/390b162455679702eca3e3ce08e1da46.png))

- > ![](https://static001.infoq.cn/resource/image/b4/ce/b4194e23d4c8eae256c603a2d8ea01ce.png)  ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=https://static001.infoq.cn/resource/image/b4/ce/b4194e23d4c8eae256c603a2d8ea01ce.png))

- > ![](https://static001.infoq.cn/resource/image/34/6e/34d1173547548b552a012da57fa3556e.png)  ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=https://static001.infoq.cn/resource/image/34/6e/34d1173547548b552a012da57fa3556e.png))

- > ![](https://static001.infoq.cn/resource/image/7b/a3/7b01ed0c45f7b73269071869dd6e87a3.png) [[推荐系统]]   ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=https://static001.infoq.cn/resource/image/7b/a3/7b01ed0c45f7b73269071869dd6e87a3.png))
  - 📝 网易云音乐的用户行为链路

- > ![](https://static001.infoq.cn/resource/image/3f/07/3f91f59bacae406acf4b697d876e8407.png)  ([🌐 摘要链接](https://www.infoq.cn/article/caqErFHGX7S1LLX1Y2wg?source=app_share#js_content:~:text=https://static001.infoq.cn/resource/image/3f/07/3f91f59bacae406acf4b697d876e8407.png))

