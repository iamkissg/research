- ---
  tags:
    - zotero
    - note/paper
  uuid: b089dd5e-6a8f-4249-b912-1d59df0e93ca
  date updated: 2022-05-18 08:31
  ---
# ABSTRACT

“TriggerInduced Recommendation (TIR), where users’ instant interest can be explicitly induced with a trigger item and follow-up related target items are recommended accordingly.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=VG7I78XC) ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) TIR 的定义：通过触发商品，显式地捕捉用户的即时兴趣，进而推荐相关商品

TIR 有一些推荐的推荐的味道：feeds 是第一次推荐，TIR 在用户点击、加购、付款成功之后，再次推荐其可能感兴趣的商品

和搜索也很像，一个是用 trigger item、一个是用 search query 显式地表达了强意图。

“It has three main components including 1) User Intent Network (UIN), which responds to generate a precise probability score to predict user’s intent on the trigger item” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=2CWR53PA) ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) UIN：用户兴趣网络，基于触发商品，预估用户意图

“2) Fusion Embedding Module (FEM), which adaptively fuses trigger item and target item embeddings based on the prediction from UIN” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=Z28XN86M) ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) FEM：融合模块，基于 UIN 自适应地融合触发商品与待排商品的 embeddings

“3) Hybrid Interest Extracting Module (HIEM), which can effectively highlight users’ instant interest from their behaviors based on the result of FEM.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=635LP6KB) ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) HIEM：混合兴趣抽取模块，基于 FEM 的结果，高亮用户的即时兴趣
# 1 INTRODUCTION

“trigger item (𝑖.𝑒., the last clicked item” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=K72RT548) ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) 商详的 trigger 很容易定义的：最后一次点击的商品

两种沿伸：

1. 就是触发商品，不一定是点击，也可以是购物车看相似
2. 就是最后一次交互的商品，不一定在商详，还可以是列表页，表征最即时的兴趣

“in our online scenario (one of the largest e-commerce platform in the world), multiple cards with each three recommended items are displayed first as shown in Fig. 1(a). Then, once an item is clicked, a new page, called Item Feeds Flow Page (IFFP), will be triggered and displayed as shown in Fig. 1(b), where the clicked item just now, called trigger item, is always located at the first position (highlighted by the red rectangle), and other items are recommended accordingly. Next, if users click one interested item within IFFP, the corresponding detailed page will be displayed as shown in Fig. 1(c), where users can directly purchase or add it into the Shopping Cart. We refer to this recommendation scenario within IFFP as TIR scenario” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=L6K6UYBS) ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) 本文所谓的 TIR 还不是商详的，是更加广义的 trigger。

这里举的例子是：点击列表推荐的集合卡片中的某个商品、弹出推荐的中间页（点击商品位于中间页顶部，后接其他推荐的商品）、再点击商品才进行详情页

这和购物点击商品的“看相似”是一致的的

“TIR scenarios have contributed more than 60% of the item page view (IPV) among all recommendation scenarios from our app” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=5MY5SJEQ) ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) TIR 在淘宝上贡献了超过 60% 的 IPV

“These methods, from the perspective of feature interactions, firstly map large-scale sparse features into fixed low dimensional embedding vectors and then feed them into fully connected layers to learn feature representations, neglecting of capturing users’ interests from their historical behaviors.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=PSPJH7QD) ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) DNN 做推荐的常规思路：EMB+MLP

“behaviors. Alternatively, increasing novel methods have been proposed to extract users’ interests from their historical behaviors. Deep Interest Network (DIN) [30], the first attention based work in the CTR area, employs attention mechanism to dynamically reweigh users’ historical behaviors with respect to the target item. Deep Interest Evolution Network (DIEN) [29] is further proposed to model users’ interests evolving process in e-commerce system. In Search-based Interest Model (SIM) [13], a kind of hard-search mode is proposed to extract users’ interests with respect to the target item, which selects and aggregates only behaviors with the same category as the target item into a sub behavior sequence” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=8IEK3VYE) ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) 新式推荐的要点是：基于注意力的信息筛选

“in TIR scenarios, users’ instant interest can be explicitly induced with a trigger item.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=U4K4JIAP) ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) TIR 的要点：用户的即时意图被 trigger item 显式地表达出来了

“For example, given the category of the trigger item Electronic, it implies that the user is only interested in items related to Electronic category at that transient moment.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=5RRDQ7HB) ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) Trigger item 的沿伸，trigger 不一定是商品（item），还可以是类目（category），于是变成了类目导航的推荐。

“Challenge 1: Users’ instant interest induced from a trigger item are inherently noisy, because there are some accidental clicks on wrong items in users’ behaviors. How to evaluate users’ real intent for the trigger item remains challenging.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=LZR247CI) ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) 这一挑战是离线数据处理需要考虑的噪声剔除。\
线上应该这样看：

1. 误触的情况下，用户不看，直接退出了，推不推荐就变得不重要了；
2. 误触了，但是推荐的多样性照顾到了用户的长短期兴趣（本身第一次推荐就已经是个性化的了，这就将误触的范围给限定住了），也许再次推荐依然能够唤起用户的兴趣，推荐成功。

“UIN responds to generate a precise probability score to predict user’s intent on the trigger item.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=WTPJQHDQ) ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) 即时兴趣和长短期兴趣之间需要平衡，因此 UIN 的目标就是预估用户对触发商品的兴趣程度，也就是这里的概率，起到一个类似门控的作用。

“FEM adaptively fuses trigger item and target item embeddings” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=6C84I8PF) ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) FEM 利用 UIN 的输出对触发商品和目标商品的 embedding 进行融合。

“HIEM can effectively highlight users’ exact interest from their behaviors by leveraging two kinds of modelling paradigms named Soft Sequential Modelling (SSM) and Hard Sequential Modelling (HSM)” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=2WW4IVRW) ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) 在 FEM 的基础上，从用户行为序列中对其兴趣进行建模。

“SSM adaptively extracts the representation vector of users’ interests by taking into consideration the relevance of historical behaviors with respect to the FEM. While HSM, borrowing the idea of hard-search mode from SIM [13], firstly selects the behaviors with the same category as the trigger item, and then aggregates theses behaviors as a sub behavior sequence, followed by employing it to capture users’ corresponding interests. Finally, all the representation features are concatenated with several raw context features and fed into fully connected layers to generate the final prediction results.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=YKHPKJ47) ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) 软硬两种建模方式：

1. 软式序列建模：基于 FEM 的结果和历史行为的相关性
2. 挑选与触发商品同类目的商品，以此获得用户的子行为序列（没有后续了？）

最后将所有的表示同上下文特征拼接起来，输入到 MLP 中。
# 2 RELATED WORK

“DCN [21] and Wide&Deep [1] creatively replace the manual features transformation with neural networks for better memorization and generalization abilities” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=USNC5FHE) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) DCN 与 Wide&Deep：神经网络的引入

“generalization abilities. NCF [7], DeepFM [4] and DMF [24] impose a neural network with multiple MLPs to model the feature interactions between users and items” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=4H4CYI5S) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) NCF、DeepFM 与 DMF：建模特征组合。

“AutoInt [17] and CAN [28] further propose the self-attention mechanism for comprehensive feature interactions.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=UB9TTERY) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) AutoInt 与 CAN：利用自注意力机制，对复杂特征组合进行建模

“GNNs [3] realize feature interaction from the perspective of graphs and achieve great success.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=GX2UYNAY) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) GNN：图视角下的特征组合

“DIN [30] emphasizes that users’ interests are diverse and an attention mechanism is introduced to capture users’ diverse interests on the different target items” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=J6Q3PE2S) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) DIN 的主要共现是：使用注意力机制对用户的多样兴趣进行建模。

“DIEN [29] refines GRU to model evolution of interest and proposes an auxiliary loss to capture latent interest from users’ behaviors.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=GAJEC4TI) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) DIEN 的主要共现是：使用 GRU 对用户兴趣的演变进行了建模，并提出了捕捉用户潜在兴趣的辅助 loss

“behaviors. Pi et al. [13] proposes a novel memory based architecture named MIMN to capture users’ interests from long sequential behavior data, which is the first industrial solution that is capable of handling long sequential user behavior data with length scaling up to thousands” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=JB8PSSV7) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) MIMN 的主要共现是：对超长用户行为序列的建模
# 3 PROPOSED METHOD

“1) Feature Representation Layer (FRL), which transforms all kinds of high dimension sparse one-hot vectors into fixed-length low dimension dense vectors” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=B4SPRKLW) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) 特征表示层
## 3.2 Feature Representation Layer

“In DIHN, we mainly employ four categories of features namely User Profile, User Behaviors, Trigger, Target Item, and Context for users’ interest representation, where each category feature consists of several fields.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=IGY38NQR) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) 四类特征：

1. 用户画像
2. 用户行为
3. 触发与目标商品画像
4. 上下文

“feature in each field is normally transformed into high-dimensional sparse one-hot features via encoding.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=5UMV6Q9R) ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) 所有特征都表示成 one-hot 形式的高维稀疏表示。

([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) DIHN 的模型示意图
## 3.3 User Intent Network

“how to evaluate user’ real intent on the trigger item remains challenging. Here, we proposed a User Intent Network (UIN) to address the challenge, which responds to generate a precise probability score accounting for user’s real intent on the trigger item” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=VFHEHD5N) ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) UIN：预估用户对触发商品是否存在真实的意图；否的情况是，误点。

“we utilize three categories of features, 𝑖.𝑒, User Profile, User Behaviors, Trigger to estimate the probability.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=LMJISKZ8) ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R))

([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) 用户行为商品与触发商品的对齐

“Now, given the user representation feature 𝑉𝑈 , we firstly concatenate it with other dense representation vector 𝐸𝑢 and 𝐸𝑡 , 𝑖.𝑒.,” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=AVXUAWL6) ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R))

“𝑥 = [𝑉𝑈 ; 𝐸𝑢 ; 𝐸𝑡 ]. It is then fed into multiple fully connected layers to further learn the high-order feature interactions. Next, after the activation function, we obtain the output of the UIN, denoted as 𝑝 (𝑥), which represents the predicted probability of the trigger item being clicked in TIR scenarios” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=VI4I8U3L) ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) UIN 实际上是一个网络中的网络，它的功能是完备的。

“if users clicking the trigger item, the samples from the same IFFP with the trigger item will have the same auxiliary label (𝑒.𝑔., positive), which can be used to supervise the learning of UIN.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=FKCRQB8P) ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) UIN 的标签来源：在中间页发生了点击，在首页的点击并非误触，中间页上所有的商品都带上了 UIN 的点击表亲啊。
## 3.4 Fusion Embedding Module

“Actually, the result predicted by UIN reflects the intensity of users’ instant interest, which is used (𝑒.𝑔., element-wise products) in FEM to fuse both embeddings in an adaptive manner for better users’ interest extraction.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=U2WTVU4Z) ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) FEM 使用 UIN 预估的用户对当前商品的兴趣概率来融合 trigger 与 target 商品

([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) FEM 对主商品和触发商品的混合，VT 是 UIN 的输出概率
## 3.5 Hybrid Interest Extracting Module
### 3.5.1 Hard Sequential Modelling

“we propose the Hard Sequential Modelling (HSM), indicating that only behaviors with the same attribute (𝑒.𝑔., category, destination) as the trigger item will be firstly selected and aggregated as a sub behavior sequence, followed by employing it to capture users’ corresponding interests.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=B82WAXIU) ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) 硬性序列编码：强制挑选同类目（可以替换成其他筛选条件）的用户行为商品构成子序列

“As we all known, user’s interest may change with time, where more recent behaviors reflect user’s temporal interest better, we apply an attention mechanism with positional encoding as query to adaptively learn the weight for each behavior, where the position of user behavior is the serial number in the behavior sequence.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=LIXGUFC5) ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) 位置作为 attention query

“In the same way, the above processing method can be applied in other attributes (𝑖.𝑒., destination, tag) of trigger item, which reflect users’ interests from different aspects, getting the destination based vector 𝑢𝑑 and tag based representation 𝑢𝑡 , respectively.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=4HRJ8D5A) ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) 过滤 sub seq 的时候，可以使用不同的条件，除了类目，还可以是标签。

“we propose the Feature Interaction Module (FIM). To be specific, we first concatenate features into one representation vector as: 𝑟𝑔 = [𝐸𝑢, 𝑢𝑐, 𝑢𝑑, 𝑢𝑡 ]. (7) Then, the combination of all the features is taken as the input of the FIM, which utilizes the global attention unit to extract the relationship among different parts of the input features.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=QZKESBQV) ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) 不同的 sub seq 的输出再经过一层融合（有一点多头注意力的意思，这里换成了多种过滤条件）
### 3.5.2 Soft Sequential Modelling

“An alternative modeling solution is to extract users’ interests with respect to the clicked trigger item and the target item simultaneously.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=L7RHSBUY) ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) 硬式序列建模的硬，体现在它使用主商品的属性来过滤子行为序列，但是对主商品没有显式的建模

“Soft Sequential Modelling (SSM), which adaptively calculates the representation vector of users’ behaviors with respect to the fusing result from FEM. In addition, since attention mechanism, specifically the Multi-Head Self-Attention (MHSA),” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=7ZZK6BF3) ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) 使用 FEM 的输出来对齐用户行为序列，并使用多头注意力

“given 𝐸 ′ 𝑏 and the fusing result from FEM, we employ DIN [30] to extract the user representation vector, denoted as 𝐸𝑆 ′ 𝑏.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=6&annotation=XSPI4S7C) ([Shen et al., 2022, p. 6](zotero://select/library/items/T3WXFB3R)) 最终使用 DIN 来生成用户行为表征
# 4 EXPERIMENTS
## 4.1 Dataset and Experimental Setup

“We implement all the competitive methods in TensorFlow using the Adam optimizer with a exponential decay learning rate schedule. The initial learning rate is set as 0.001 and decay rate is set as 0.9. The hyper-parameters 𝛼 and 𝛽 in Eq. (13) are set 1 and 0.8, respectively. We take AUC [30] as the main metric to evaluate model’s performance, which is widely adopted in the field of CTR prediction task.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=6&annotation=UVIW7QU2) ([Shen et al., 2022, p. 6](zotero://select/library/items/T3WXFB3R)) DIHN 的参数设置
## 4.4 Ablation Study
### 4.4.1 Effectiveness of HSM module

“Since HSM module can help filter irrelevant noise so that the model focuses on the most relevant behaviors for users’ interest extraction” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=7&annotation=XEYLXUIJ) ([Shen et al., 2022, p. 7](zotero://select/library/items/T3WXFB3R)) HSM 具有强剔除噪声的作用
### 4.4.2 Effectiveness of UIN module

“Users’ interest on the trigger item obtained by the UIN module can help extract users’ interests with respect to the target item and bring further performance improvement.” [Go to annotation](zotero://open-pdf/library/items/N8JTW5T3?page=8&annotation=2LDRP7FZ) ([Shen et al., 2022, p. 8](zotero://select/library/items/T3WXFB3R)) Ablation study 展示了 UIN 的有效性
# Annotations  
(5/18/2022, 7:13:21 AM)

“ABSTRACT” ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=JVZMFGKR))

“TriggerInduced Recommendation (TIR), where users’ instant interest can be explicitly induced with a trigger item and follow-up related target items are recommended accordingly.” ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=VG7I78XC)) TIR 的定义：通过触发商品，显式地捕捉用户的即时兴趣，进而推荐相关商品  
TIR 有一些推荐的推荐的味道：feeds 是第一次推荐，TIR 在用户点击、加购、付款成功之后，再次推荐其可能感兴趣的商品  
和搜索也很像，一个是用 trigger item、一个是用 search query 显式地表达了强意图。

“It has three main components including 1) User Intent Network (UIN), which responds to generate a precise probability score to predict user’s intent on the trigger item” ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=2CWR53PA)) UIN：用户兴趣网络，基于触发商品，预估用户意图

“2) Fusion Embedding Module (FEM), which adaptively fuses trigger item and target item embeddings based on the prediction from UIN” ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=Z28XN86M)) FEM：融合模块，基于 UIN 自适应地融合触发商品与待排商品的 embeddings

“3) Hybrid Interest Extracting Module (HIEM), which can effectively highlight users’ instant interest from their behaviors based on the result of FEM.” ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=635LP6KB)) HIEM：混合兴趣抽取模块，基于 FEM 的结果，高亮用户的即时兴趣

“1 INTRODUCTION” ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=U7MDYNWM))

“trigger item (𝑖.𝑒., the last clicked item” ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=K72RT548)) 商详的 trigger 很容易定义的：最后一次点击的商品  
两种沿伸：  
1\. 就是触发商品，不一定是点击，也可以是购物车看相似  
2\. 就是最后一次交互的商品，不一定在商详，还可以是列表页，表征最即时的兴趣

“in our online scenario (one of the largest e-commerce platform in the world), multiple cards with each three recommended items are displayed first as shown in Fig. 1(a). Then, once an item is clicked, a new page, called Item Feeds Flow Page (IFFP), will be triggered and displayed as shown in Fig. 1(b), where the clicked item just now, called trigger item, is always located at the first position (highlighted by the red rectangle), and other items are recommended accordingly. Next, if users click one interested item within IFFP, the corresponding detailed page will be displayed as shown in Fig. 1(c), where users can directly purchase or add it into the Shopping Cart. We refer to this recommendation scenario within IFFP as TIR scenario” ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=L6K6UYBS)) 本文所谓的 TIR 还不是商详的，是更加广义的 trigger。  
这里举的例子是：点击列表推荐的集合卡片中的某个商品、弹出推荐的中间页（点击商品位于中间页顶部，后接其他推荐的商品）、再点击商品才进行详情页  
这和购物点击商品的“看相似”是一致的的

“TIR scenarios have contributed more than 60% of the item page view (IPV) among all recommendation scenarios from our app” ([Shen et al., 2022, p. 1](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=1&annotation=5MY5SJEQ)) TIR 在淘宝上贡献了超过 60% 的 IPV

“These methods, from the perspective of feature interactions, firstly map large-scale sparse features into fixed low dimensional embedding vectors and then feed them into fully connected layers to learn feature representations, neglecting of capturing users’ interests from their historical behaviors.” ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=PSPJH7QD)) DNN 做推荐的常规思路：EMB+MLP

“behaviors. Alternatively, increasing novel methods have been proposed to extract users’ interests from their historical behaviors. Deep Interest Network (DIN) \[30\], the first attention based work in the CTR area, employs attention mechanism to dynamically reweigh users’ historical behaviors with respect to the target item. Deep Interest Evolution Network (DIEN) \[29\] is further proposed to model users’ interests evolving process in e-commerce system. In Search-based Interest Model (SIM) \[13\], a kind of hard-search mode is proposed to extract users’ interests with respect to the target item, which selects and aggregates only behaviors with the same category as the target item into a sub behavior sequence” ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=8IEK3VYE)) 新式推荐的要点是：基于注意力的信息筛选

“in TIR scenarios, users’ instant interest can be explicitly induced with a trigger item.” ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=U4K4JIAP)) TIR 的要点：用户的即时意图被 trigger item 显式地表达出来了

“For example, given the category of the trigger item Electronic, it implies that the user is only interested in items related to Electronic category at that transient moment.” ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=5RRDQ7HB)) Trigger item 的沿伸，trigger 不一定是商品（item），还可以是类目（category），于是变成了类目导航的推荐。

“Challenge 1: Users’ instant interest induced from a trigger item are inherently noisy, because there are some accidental clicks on wrong items in users’ behaviors. How to evaluate users’ real intent for the trigger item remains challenging.” ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=LZR247CI)) 这一挑战是离线数据处理需要考虑的噪声剔除。  
线上应该这样看：  
1\. 误触的情况下，用户不看，直接退出了，推不推荐就变得不重要了；  
2\. 误触了，但是推荐的多样性照顾到了用户的长短期兴趣（本身第一次推荐就已经是个性化的了，这就将误触的范围给限定住了），也许再次推荐依然能够唤起用户的兴趣，推荐成功。

“UIN responds to generate a precise probability score to predict user’s intent on the trigger item.” ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=WTPJQHDQ)) 即时兴趣和长短期兴趣之间需要平衡，因此 UIN 的目标就是预估用户对触发商品的兴趣程度，也就是这里的概率，起到一个类似门控的作用。

“FEM adaptively fuses trigger item and target item embeddings” ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=6C84I8PF)) FEM 利用 UIN 的输出对触发商品和目标商品的 embedding 进行融合。

“HIEM can effectively highlight users’ exact interest from their behaviors by leveraging two kinds of modelling paradigms named Soft Sequential Modelling (SSM) and Hard Sequential Modelling (HSM)” ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=2WW4IVRW)) 在 FEM 的基础上，从用户行为序列中对其兴趣进行建模。

“SSM adaptively extracts the representation vector of users’ interests by taking into consideration the relevance of historical behaviors with respect to the FEM. While HSM, borrowing the idea of hard-search mode from SIM \[13\], firstly selects the behaviors with the same category as the trigger item, and then aggregates theses behaviors as a sub behavior sequence, followed by employing it to capture users’ corresponding interests. Finally, all the representation features are concatenated with several raw context features and fed into fully connected layers to generate the final prediction results.” ([Shen et al., 2022, p. 2](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=2&annotation=YKHPKJ47)) 软硬两种建模方式：  
1\. 软式序列建模：基于 FEM 的结果和历史行为的相关性  
2\. 挑选与触发商品同类目的商品，以此获得用户的子行为序列（没有后续了？）  
最后将所有的表示同上下文特征拼接起来，输入到 MLP 中。

“2 RELATED WORK” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=RVRRNQUN))

“DCN \[21\] and Wide&Deep \[1\] creatively replace the manual features transformation with neural networks for better memorization and generalization abilities” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=USNC5FHE)) DCN 与 Wide&Deep：神经网络的引入

“generalization abilities. NCF \[7\], DeepFM \[4\] and DMF \[24\] impose a neural network with multiple MLPs to model the feature interactions between users and items” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=4H4CYI5S)) NCF、DeepFM 与 DMF：建模特征组合。

“AutoInt \[17\] and CAN \[28\] further propose the self-attention mechanism for comprehensive feature interactions.” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=UB9TTERY)) AutoInt 与 CAN：利用自注意力机制，对复杂特征组合进行建模

“GNNs \[3\] realize feature interaction from the perspective of graphs and achieve great success.” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=GX2UYNAY)) GNN：图视角下的特征组合

“DIN \[30\] emphasizes that users’ interests are diverse and an attention mechanism is introduced to capture users’ diverse interests on the different target items” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=J6Q3PE2S)) DIN 的主要共现是：使用注意力机制对用户的多样兴趣进行建模。

“DIEN \[29\] refines GRU to model evolution of interest and proposes an auxiliary loss to capture latent interest from users’ behaviors.” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=GAJEC4TI)) DIEN 的主要共现是：使用 GRU 对用户兴趣的演变进行了建模，并提出了捕捉用户潜在兴趣的辅助 loss

“behaviors. Pi et al. \[13\] proposes a novel memory based architecture named MIMN to capture users’ interests from long sequential behavior data, which is the first industrial solution that is capable of handling long sequential user behavior data with length scaling up to thousands” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=JB8PSSV7)) MIMN 的主要共现是：对超长用户行为序列的建模

“3 PROPOSED METHOD” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=ZF8LMXDH))

“1) Feature Representation Layer (FRL), which transforms all kinds of high dimension sparse one-hot vectors into fixed-length low dimension dense vectors” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=B4SPRKLW)) 特征表示层

“3.2 Feature Representation Layer” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=3F5WRK6S))

“In DIHN, we mainly employ four categories of features namely User Profile, User Behaviors, Trigger, Target Item, and Context for users’ interest representation, where each category feature consists of several fields.” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=IGY38NQR)) 四类特征：  
1\. 用户画像  
2\. 用户行为  
3\. 触发与目标商品画像  
4\. 上下文

“feature in each field is normally transformed into high-dimensional sparse one-hot features via encoding.” ([Shen et al., 2022, p. 3](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=3&annotation=5UMV6Q9R)) 所有特征都表示成 one-hot 形式的高维稀疏表示。

\[image\] ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=7AYHV8N2))  
([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) DIHN 的模型示意图

“3.3 User Intent Network” ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=BIMAPFSE))

“how to evaluate user’ real intent on the trigger item remains challenging. Here, we proposed a User Intent Network (UIN) to address the challenge, which responds to generate a precise probability score accounting for user’s real intent on the trigger item” ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=VFHEHD5N)) UIN：预估用户对触发商品是否存在真实的意图；否的情况是，误点。

“we utilize three categories of features, 𝑖.𝑒, User Profile, User Behaviors, Trigger to estimate the probability.” ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=LMJISKZ8))

\[image\] ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=JV37TG54))  
([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) 用户行为商品与触发商品的对齐

“Now, given the user representation feature 𝑉𝑈 , we firstly concatenate it with other dense representation vector 𝐸𝑢 and 𝐸𝑡 , 𝑖.𝑒.,” ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=AVXUAWL6))

“𝑥 = \[𝑉𝑈 ; 𝐸𝑢 ; 𝐸𝑡 \]. It is then fed into multiple fully connected layers to further learn the high-order feature interactions. Next, after the activation function, we obtain the output of the UIN, denoted as 𝑝 (𝑥), which represents the predicted probability of the trigger item being clicked in TIR scenarios” ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=VI4I8U3L)) UIN 实际上是一个网络中的网络，它的功能是完备的。

“if users clicking the trigger item, the samples from the same IFFP with the trigger item will have the same auxiliary label (𝑒.𝑔., positive), which can be used to supervise the learning of UIN.” ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=FKCRQB8P)) UIN 的标签来源：在中间页发生了点击，在首页的点击并非误触，中间页上所有的商品都带上了 UIN 的点击表亲啊。

“3.4 Fusion Embedding Module” ([Shen et al., 2022, p. 4](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=4&annotation=2EBPM2GN))

“Actually, the result predicted by UIN reflects the intensity of users’ instant interest, which is used (𝑒.𝑔., element-wise products) in FEM to fuse both embeddings in an adaptive manner for better users’ interest extraction.” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=U2WTVU4Z)) FEM 使用 UIN 预估的用户对当前商品的兴趣概率来融合 trigger 与 target 商品

\[image\] ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=KJFN2AHU))  
([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) FEM 对主商品和触发商品的混合，VT 是 UIN 的输出概率

“3.5 Hybrid Interest Extracting Module” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=E6JD8GMA))

“3.5.1 Hard Sequential Modelling.” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=S4SBKUNU))

“we propose the Hard Sequential Modelling (HSM), indicating that only behaviors with the same attribute (𝑒.𝑔., category, destination) as the trigger item will be firstly selected and aggregated as a sub behavior sequence, followed by employing it to capture users’ corresponding interests.” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=B82WAXIU)) 硬性序列编码：强制挑选同类目（可以替换成其他筛选条件）的用户行为商品构成子序列

“As we all known, user’s interest may change with time, where more recent behaviors reflect user’s temporal interest better, we apply an attention mechanism with positional encoding as query to adaptively learn the weight for each behavior, where the position of user behavior is the serial number in the behavior sequence.” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=LIXGUFC5)) 位置作为 attention query

“In the same way, the above processing method can be applied in other attributes (𝑖.𝑒., destination, tag) of trigger item, which reflect users’ interests from different aspects, getting the destination based vector 𝑢𝑑 and tag based representation 𝑢𝑡 , respectively.” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=4HRJ8D5A)) 过滤 sub seq 的时候，可以使用不同的条件，除了类目，还可以是标签。

“we propose the Feature Interaction Module (FIM). To be specific, we first concatenate features into one representation vector as: 𝑟𝑔 = \[𝐸𝑢, 𝑢𝑐, 𝑢𝑑, 𝑢𝑡 \]. (7) Then, the combination of all the features is taken as the input of the FIM, which utilizes the global attention unit to extract the relationship among different parts of the input features.” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=QZKESBQV)) 不同的 sub seq 的输出再经过一层融合（有一点多头注意力的意思，这里换成了多种过滤条件）

“3.5.2 Soft Sequential Modelling.” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=BLDVYFR7))

“An alternative modeling solution is to extract users’ interests with respect to the clicked trigger item and the target item simultaneously.” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=L7RHSBUY)) 硬式序列建模的硬，体现在它使用主商品的属性来过滤子行为序列，但是对主商品没有显式的建模

“Soft Sequential Modelling (SSM), which adaptively calculates the representation vector of users’ behaviors with respect to the fusing result from FEM. In addition, since attention mechanism, specifically the Multi-Head Self-Attention (MHSA),” ([Shen et al., 2022, p. 5](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=5&annotation=7ZZK6BF3)) 使用 FEM 的输出来对齐用户行为序列，并使用多头注意力

“given 𝐸 ′ 𝑏 and the fusing result from FEM, we employ DIN \[30\] to extract the user representation vector, denoted as 𝐸𝑆 ′ 𝑏.” ([Shen et al., 2022, p. 6](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=6&annotation=XSPI4S7C)) 最终使用 DIN 来生成用户行为表征

“4 EXPERIMENTS” ([Shen et al., 2022, p. 6](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=6&annotation=NB5Z3JU7))

“4.1 Dataset and Experimental Setup” ([Shen et al., 2022, p. 6](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=6&annotation=BGLG7XEG))

“We implement all the competitive methods in TensorFlow using the Adam optimizer with a exponential decay learning rate schedule. The initial learning rate is set as 0.001 and decay rate is set as 0.9. The hyper-parameters 𝛼 and 𝛽 in Eq. (13) are set 1 and 0.8, respectively. We take AUC \[30\] as the main metric to evaluate model’s performance, which is widely adopted in the field of CTR prediction task.” ([Shen et al., 2022, p. 6](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=6&annotation=UVIW7QU2)) DIHN 的参数设置

“4.4 Ablation Study” ([Shen et al., 2022, p. 7](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=7&annotation=G5QHFQBH))

“4.4.1 Effectiveness of HSM module.” ([Shen et al., 2022, p. 7](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=7&annotation=BIW7EJEA))

“Since HSM module can help filter irrelevant noise so that the model focuses on the most relevant behaviors for users’ interest extraction” ([Shen et al., 2022, p. 7](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=7&annotation=XEYLXUIJ)) HSM 具有强剔除噪声的作用

“4.4.2 Effectiveness of UIN module.” ([Shen et al., 2022, p. 8](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=8&annotation=HKLHSBNL))

“Users’ interest on the trigger item obtained by the UIN module can help extract users’ interests with respect to the target item and bring further performance improvement.” ([Shen et al., 2022, p. 8](zotero://select/library/items/T3WXFB3R)) ([pdf](zotero://open-pdf/library/items/N8JTW5T3?page=8&annotation=2LDRP7FZ)) Ablation study 展示了 UIN 的有效性