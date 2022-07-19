title:: 【Reading Highlights】搜索推荐广告排序艺术 - 特征交叉
source:: https://zhuanlan.zhihu.com/p/530489632
summary:: 
tags:: [[简悦]] [[特征工程]]  [[特征组合]]  [[综述]]  [[推荐指数：二星]]   [[reading_highlights]]
date:: 20220629  

- > 交叉特征可以是稀疏的 id 特征或 dense 特征。

稀疏 id 特征：LR 模型中设计的交叉特征 <query, ad_id>。

dense 特征：比如在搜索中统计 <query, item> 的平均 ctr，在 DMT 模型中加入的 dense 特征。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%E5%8F%AF%E4%BB%A5%E6%98%AF%E7%A8%80%E7%96%8F%E7%9A%84%20id%20%E7%89%B9%E5%BE%81%E6%88%96%20dense%20%E7%89%B9%E5%BE%81%E3%80%82%E7%A8%80%E7%96%8F%20id%20%E7%89%B9%E5%BE%81%EF%BC%9ALR%20%E6%A8%A1%E5%9E%8B%E4%B8%AD%E8%AE%BE%E8%AE%A1%E7%9A%84%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%20%3Cquery,%20ad_id%3E%E3%80%82dense%20%E7%89%B9%E5%BE%81%EF%BC%9A%E6%AF%94%E5%A6%82%E5%9C%A8%E6%90%9C%E7%B4%A2%E4%B8%AD%E7%BB%9F%E8%AE%A1%20%3Cquery,%20item%3E%20%E7%9A%84%E5%B9%B3%E5%9D%87%20ctr%EF%BC%8C%E5%9C%A8%20DMT%20%E6%A8%A1%E5%9E%8B%E4%B8%AD%E5%8A%A0%E5%85%A5%E7%9A%84%20dense%20%E7%89%B9%E5%BE%81%E3%80%82))
  - 📝 ⚠️像<query, item> 的统计量，也属于交叉特征

- > ![](https://pic2.zhimg.com/v2-8d2ba18416b8bd2e4f57e55e8cd435a1_r.jpg) [[模型结构]]  [[京东技术]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=https://pic2.zhimg.com/v2-8d2ba18416b8bd2e4f57e55e8cd435a1_r.jpg))

- > DMT 中特征交叉建模方式包括两种：  
（1）DNN MLP 隐式建模 bit-wise 特征交叉。

（2）人工设计交叉特征，放在 dense 特征中。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=DMT%20%E4%B8%AD%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%E5%BB%BA%E6%A8%A1%E6%96%B9%E5%BC%8F%E5%8C%85%E6%8B%AC%E4%B8%A4%E7%A7%8D%EF%BC%9A%EF%BC%881%EF%BC%89DNN%20MLP%20%E9%9A%90%E5%BC%8F%E5%BB%BA%E6%A8%A1%20bit-wise%20%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%E3%80%82%EF%BC%882%EF%BC%89%E4%BA%BA%E5%B7%A5%E8%AE%BE%E8%AE%A1%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%EF%BC%8C%E6%94%BE%E5%9C%A8%20dense%20%E7%89%B9%E5%BE%81%E4%B8%AD%E3%80%82))

- > FM 提出为每一个特征学习一个隐藏向量，通过两个特征向量的点积来计算交叉特征对模型分数的贡献，大大减少了模型参数量，同时增强了模型泛化能力。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=FM%20%E6%8F%90%E5%87%BA%E4%B8%BA%E6%AF%8F%E4%B8%80%E4%B8%AA%E7%89%B9%E5%BE%81%E5%AD%A6%E4%B9%A0%E4%B8%80%E4%B8%AA%E9%9A%90%E8%97%8F%E5%90%91%E9%87%8F%EF%BC%8C%E9%80%9A%E8%BF%87%E4%B8%A4%E4%B8%AA%E7%89%B9%E5%BE%81%E5%90%91%E9%87%8F%E7%9A%84%E7%82%B9%E7%A7%AF%E6%9D%A5%E8%AE%A1%E7%AE%97%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%E5%AF%B9%E6%A8%A1%E5%9E%8B%E5%88%86%E6%95%B0%E7%9A%84%E8%B4%A1%E7%8C%AE%EF%BC%8C%E5%A4%A7%E5%A4%A7%E5%87%8F%E5%B0%91%E4%BA%86%E6%A8%A1%E5%9E%8B%E5%8F%82%E6%95%B0%E9%87%8F%EF%BC%8C%E5%90%8C%E6%97%B6%E5%A2%9E%E5%BC%BA%E4%BA%86%E6%A8%A1%E5%9E%8B%E6%B3%9B%E5%8C%96%E8%83%BD%E5%8A%9B%E3%80%82))

- > 对比 MF 模型：MF 模型可以看出 FM 模型的特例，即只使用 user_id, item_id 特征。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=%E5%AF%B9%E6%AF%94%20MF%20%E6%A8%A1%E5%9E%8B%EF%BC%9AMF%20%E6%A8%A1%E5%9E%8B%E5%8F%AF%E4%BB%A5%E7%9C%8B%E5%87%BA%20FM%20%E6%A8%A1%E5%9E%8B%E7%9A%84%E7%89%B9%E4%BE%8B%EF%BC%8C%E5%8D%B3%E5%8F%AA%E4%BD%BF%E7%94%A8%20user_id,%20item_id%20%E7%89%B9%E5%BE%81%E3%80%82))

- > FM 的优势：

（1）适合搜推广大规模稀疏特征下的特征交叉，能自动实现二阶、多阶特征的交叉。

（2）模型参数和特征数目是线性的关系，大大降低了二阶或多节特征交叉的模型参数量。

（3）模型预测和特征数目是线性的关系，计算效率高

（4）和 LR 比，可以不需要人工交叉特征，参数量少，泛化能力强。 [[模型优势]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=FM%20%E7%9A%84%E4%BC%98%E5%8A%BF%EF%BC%9A%EF%BC%881%EF%BC%89%E9%80%82%E5%90%88%E6%90%9C%E6%8E%A8%E5%B9%BF%E5%A4%A7%E8%A7%84%E6%A8%A1%E7%A8%80%E7%96%8F%E7%89%B9%E5%BE%81%E4%B8%8B%E7%9A%84%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%EF%BC%8C%E8%83%BD%E8%87%AA%E5%8A%A8%E5%AE%9E%E7%8E%B0%E4%BA%8C%E9%98%B6%E3%80%81%E5%A4%9A%E9%98%B6%E7%89%B9%E5%BE%81%E7%9A%84%E4%BA%A4%E5%8F%89%E3%80%82%EF%BC%882%EF%BC%89%E6%A8%A1%E5%9E%8B%E5%8F%82%E6%95%B0%E5%92%8C%E7%89%B9%E5%BE%81%E6%95%B0%E7%9B%AE%E6%98%AF%E7%BA%BF%E6%80%A7%E7%9A%84%E5%85%B3%E7%B3%BB%EF%BC%8C%E5%A4%A7%E5%A4%A7%E9%99%8D%E4%BD%8E%E4%BA%86%E4%BA%8C%E9%98%B6%E6%88%96%E5%A4%9A%E8%8A%82%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%E7%9A%84%E6%A8%A1%E5%9E%8B%E5%8F%82%E6%95%B0%E9%87%8F%E3%80%82%EF%BC%883%EF%BC%89%E6%A8%A1%E5%9E%8B%E9%A2%84%E6%B5%8B%E5%92%8C%E7%89%B9%E5%BE%81%E6%95%B0%E7%9B%AE%E6%98%AF%E7%BA%BF%E6%80%A7%E7%9A%84%E5%85%B3%E7%B3%BB%EF%BC%8C%E8%AE%A1%E7%AE%97%E6%95%88%E7%8E%87%E9%AB%98%EF%BC%884%EF%BC%89%E5%92%8C%20LR%20%E6%AF%94%EF%BC%8C%E5%8F%AF%E4%BB%A5%E4%B8%8D%E9%9C%80%E8%A6%81%E4%BA%BA%E5%B7%A5%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%EF%BC%8C%E5%8F%82%E6%95%B0%E9%87%8F%E5%B0%91%EF%BC%8C%E6%B3%9B%E5%8C%96%E8%83%BD%E5%8A%9B%E5%BC%BA%E3%80%82))
  - 📝 [[FM]]

- > FM 为每个特征学习一个 embedding 向量，FFM 为每个特征学习 f 个 embedding 向量, f 为特征 field 个数。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=FM%20%E4%B8%BA%E6%AF%8F%E4%B8%AA%E7%89%B9%E5%BE%81%E5%AD%A6%E4%B9%A0%E4%B8%80%E4%B8%AA%20embedding%20%E5%90%91%E9%87%8F%EF%BC%8CFFM%20%E4%B8%BA%E6%AF%8F%E4%B8%AA%E7%89%B9%E5%BE%81%E5%AD%A6%E4%B9%A0%20f%20%E4%B8%AA%20embedding%20%E5%90%91%E9%87%8F,%20f%20%E4%B8%BA%E7%89%B9%E5%BE%81%20field%20%E4%B8%AA%E6%95%B0%E3%80%82))

- > 例如对应 query, age, gender, cate_id，在计算 <cate_id, age>, <cate_id, gender > 交叉特征时：FM 使用了相同的 cate_id embedding；FFM 认为 cate_id 和不同特征交叉时需要不同的表示，因此使用不同的 cate_id embedding。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=%E4%BE%8B%E5%A6%82%E5%AF%B9%E5%BA%94%20query,%20age,%20gender,%20cate_id%EF%BC%8C%E5%9C%A8%E8%AE%A1%E7%AE%97%20%3Ccate_id,%20age%3E,%20%3Ccate_id,%20gender%20%3E%20%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%E6%97%B6%EF%BC%9AFM%20%E4%BD%BF%E7%94%A8%E4%BA%86%E7%9B%B8%E5%90%8C%E7%9A%84%20cate_id%20embedding%EF%BC%9BFFM%20%E8%AE%A4%E4%B8%BA%20cate_id%20%E5%92%8C%E4%B8%8D%E5%90%8C%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%E6%97%B6%E9%9C%80%E8%A6%81%E4%B8%8D%E5%90%8C%E7%9A%84%E8%A1%A8%E7%A4%BA%EF%BC%8C%E5%9B%A0%E6%AD%A4%E4%BD%BF%E7%94%A8%E4%B8%8D%E5%90%8C%E7%9A%84%20cate_id%20embedding%E3%80%82))

- > 假设排序特征一共有 n 个 field，FFM 会为每个特征申请 n-1 个用于交叉的 embedding，分别用于和其他 n-1 个特征进行交叉。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=%E5%81%87%E8%AE%BE%E6%8E%92%E5%BA%8F%E7%89%B9%E5%BE%81%E4%B8%80%E5%85%B1%E6%9C%89%20n%20%E4%B8%AA%20field%EF%BC%8CFFM%20%E4%BC%9A%E4%B8%BA%E6%AF%8F%E4%B8%AA%E7%89%B9%E5%BE%81%E7%94%B3%E8%AF%B7%20n-1%20%E4%B8%AA%E7%94%A8%E4%BA%8E%E4%BA%A4%E5%8F%89%E7%9A%84%20embedding%EF%BC%8C%E5%88%86%E5%88%AB%E7%94%A8%E4%BA%8E%E5%92%8C%E5%85%B6%E4%BB%96%20n-1%20%E4%B8%AA%E7%89%B9%E5%BE%81%E8%BF%9B%E8%A1%8C%E4%BA%A4%E5%8F%89%E3%80%82))

- > DeepFM 模型，将 wide&Deep 中的 wide 侧的建模从 LR 换成了 FM。输入不再需要人工设计特征，FM 侧的 embedding 和 DNN 侧共享。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=DeepFM%20%E6%A8%A1%E5%9E%8B%EF%BC%8C%E5%B0%86%20wide&Deep%20%E4%B8%AD%E7%9A%84%20wide%20%E4%BE%A7%E7%9A%84%E5%BB%BA%E6%A8%A1%E4%BB%8E%20LR%20%E6%8D%A2%E6%88%90%E4%BA%86%20FM%E3%80%82%E8%BE%93%E5%85%A5%E4%B8%8D%E5%86%8D%E9%9C%80%E8%A6%81%E4%BA%BA%E5%B7%A5%E8%AE%BE%E8%AE%A1%E7%89%B9%E5%BE%81%EF%BC%8CFM%20%E4%BE%A7%E7%9A%84%20embedding%20%E5%92%8C%20DNN%20%E4%BE%A7%E5%85%B1%E4%BA%AB%E3%80%82))

- > xDeepFM 中使用 CIN 模块建模多阶交叉，其中 CIN 模块和 Deep Cross 类似  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=xDeepFM%20%E4%B8%AD%E4%BD%BF%E7%94%A8%20CIN%20%E6%A8%A1%E5%9D%97%E5%BB%BA%E6%A8%A1%E5%A4%9A%E9%98%B6%E4%BA%A4%E5%8F%89%EF%BC%8C%E5%85%B6%E4%B8%AD%20CIN%20%E6%A8%A1%E5%9D%97%E5%92%8C%20Deep%20Cross%20%E7%B1%BB%E4%BC%BC))

- > 2019 (Arxiv) [FAT-DeepFFM] - Field Attentive Deep Field-aware Factorization Machine

FAT-DeepFFM 将 SENet 思想融入 DeepFFM，来建模特征交叉。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=2019%20(Arxiv)%20%5BFAT-DeepFFM%5D%20-%20Field%20Attentive%20Deep%20Field-aware%20Factorization%20MachineFAT-DeepFFM%20%E5%B0%86%20SENet%20%E6%80%9D%E6%83%B3%E8%9E%8D%E5%85%A5%20DeepFFM%EF%BC%8C%E6%9D%A5%E5%BB%BA%E6%A8%A1%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%E3%80%82))

- > DeepFFM:

将 FFM 特征交互后的结果作为 DNN 输入，其中特征交互层可以用 inner product 或 Hadamard product。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=DeepFFM:%E5%B0%86%20FFM%20%E7%89%B9%E5%BE%81%E4%BA%A4%E4%BA%92%E5%90%8E%E7%9A%84%E7%BB%93%E6%9E%9C%E4%BD%9C%E4%B8%BA%20DNN%20%E8%BE%93%E5%85%A5%EF%BC%8C%E5%85%B6%E4%B8%AD%E7%89%B9%E5%BE%81%E4%BA%A4%E4%BA%92%E5%B1%82%E5%8F%AF%E4%BB%A5%E7%94%A8%20inner%20product%20%E6%88%96%20Hadamard%20product%E3%80%82))

- > FAT-DeepFFM 借鉴了 SE-Net 的思想，提出 Compose-Excitation network (CENet) attention mechanism，在 FFM 特征交互前动态建模不同 field 特征的重要性，选取高信息量的特征，抑制作用小的特征。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=FAT-DeepFFM%20%E5%80%9F%E9%89%B4%E4%BA%86%20SE-Net%20%E7%9A%84%E6%80%9D%E6%83%B3%EF%BC%8C%E6%8F%90%E5%87%BA%20Compose-Excitation%20network%20(CENet)%20attention%20mechanism%EF%BC%8C%E5%9C%A8%20FFM%20%E7%89%B9%E5%BE%81%E4%BA%A4%E4%BA%92%E5%89%8D%E5%8A%A8%E6%80%81%E5%BB%BA%E6%A8%A1%E4%B8%8D%E5%90%8C%20field%20%E7%89%B9%E5%BE%81%E7%9A%84%E9%87%8D%E8%A6%81%E6%80%A7%EF%BC%8C%E9%80%89%E5%8F%96%E9%AB%98%E4%BF%A1%E6%81%AF%E9%87%8F%E7%9A%84%E7%89%B9%E5%BE%81%EF%BC%8C%E6%8A%91%E5%88%B6%E4%BD%9C%E7%94%A8%E5%B0%8F%E7%9A%84%E7%89%B9%E5%BE%81%E3%80%82))

- > ![](https://pic2.zhimg.com/v2-2dc3070c5c85ea38104969e9314163b5_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=https://pic2.zhimg.com/v2-2dc3070c5c85ea38104969e9314163b5_r.jpg))
  - 📝 [[FiBiNet]]

- > Deep Crossing 模型只需要输入原始特征，不需要手动构造交叉特征，使用 Multiple Residual Units 来建模特征交叉，应用在 Bing Ads 中。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=Deep%20Crossing%20%E6%A8%A1%E5%9E%8B%E5%8F%AA%E9%9C%80%E8%A6%81%E8%BE%93%E5%85%A5%E5%8E%9F%E5%A7%8B%E7%89%B9%E5%BE%81%EF%BC%8C%E4%B8%8D%E9%9C%80%E8%A6%81%E6%89%8B%E5%8A%A8%E6%9E%84%E9%80%A0%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%EF%BC%8C%E4%BD%BF%E7%94%A8%20Multiple%20Residual%20Units%20%E6%9D%A5%E5%BB%BA%E6%A8%A1%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%EF%BC%8C%E5%BA%94%E7%94%A8%E5%9C%A8%20Bing%20Ads%20%E4%B8%AD%E3%80%82))

- > 模型输入的稀疏特征、dense 特征通过 embedding 后拼接成一个向量，作为 Multiple Residual Units 的输入。

Multiple Residual Units 可以看作多层带残差连接的 MLP。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=%E6%A8%A1%E5%9E%8B%E8%BE%93%E5%85%A5%E7%9A%84%E7%A8%80%E7%96%8F%E7%89%B9%E5%BE%81%E3%80%81dense%20%E7%89%B9%E5%BE%81%E9%80%9A%E8%BF%87%20embedding%20%E5%90%8E%E6%8B%BC%E6%8E%A5%E6%88%90%E4%B8%80%E4%B8%AA%E5%90%91%E9%87%8F%EF%BC%8C%E4%BD%9C%E4%B8%BA%20Multiple%20Residual%20Units%20%E7%9A%84%E8%BE%93%E5%85%A5%E3%80%82Multiple%20Residual%20Units%20%E5%8F%AF%E4%BB%A5%E7%9C%8B%E4%BD%9C%E5%A4%9A%E5%B1%82%E5%B8%A6%E6%AE%8B%E5%B7%AE%E8%BF%9E%E6%8E%A5%E7%9A%84%20MLP%E3%80%82))

- > ![](https://pic3.zhimg.com/v2-8904b0829087ecce98bea9596b49bb06_r.jpg) [[模型结构]]   ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=https://pic3.zhimg.com/v2-8904b0829087ecce98bea9596b49bb06_r.jpg))
  - 📝 [[AutoInt]]

- > CAN 使用 Co-Action Network 建模特征交互，解决使用 cartesian product 特征交叉参数爆炸的问题。  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=CAN%20%E4%BD%BF%E7%94%A8%20Co-Action%20Network%20%E5%BB%BA%E6%A8%A1%E7%89%B9%E5%BE%81%E4%BA%A4%E4%BA%92%EF%BC%8C%E8%A7%A3%E5%86%B3%E4%BD%BF%E7%94%A8%20cartesian%20product%20%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%E5%8F%82%E6%95%B0%E7%88%86%E7%82%B8%E7%9A%84%E9%97%AE%E9%A2%98%E3%80%82))

- > Co-Action Unit：

对于 <induction, feed> 交叉特征，Co-Action Unit 将 p_induction 看成 MLP 的参数，再根据 p_feed，生成特征交叉后的结果  ([🌐 摘要链接](https://zhuanlan.zhihu.com/p/530489632#js_content:~:text=Co-Action%20Unit%EF%BC%9A%E5%AF%B9%E4%BA%8E%20%3Cinduction,%20feed%3E%20%E4%BA%A4%E5%8F%89%E7%89%B9%E5%BE%81%EF%BC%8CCo-Action%20Unit%20%E5%B0%86%20p_induction%20%E7%9C%8B%E6%88%90%20MLP%20%E7%9A%84%E5%8F%82%E6%95%B0%EF%BC%8C%E5%86%8D%E6%A0%B9%E6%8D%AE%20p_feed%EF%BC%8C%E7%94%9F%E6%88%90%E7%89%B9%E5%BE%81%E4%BA%A4%E5%8F%89%E5%90%8E%E7%9A%84%E7%BB%93%E6%9E%9C))

