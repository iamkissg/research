- ABSTRACT” (Zhou et al., 2018, p. 1)
  “Deep Interest Network (DIN) which tackles this challenge by designing a local activation unit to adaptively learn the representation of user interests from historical behaviors with respect to a certain ad.” (Zhou et al., 2018, p. 1)
  DIN 的要点：给定特定广告/商品，使用局部激活单元（一种 attention）从用户历史行为中自适应（加权）地学习用户兴趣表示
- “Besides, we develop two techniques: mini-batch aware regularization and data adaptive activation function which can help training industrial deep networks with hundreds of millions of parameters.” (Zhou et al., 2018, p. 1)
  DIN 论文的另外两点贡献：mini-batch aware 正则化，新的激活函数 dice
- 1 INTRODUCTION” (Zhou et al., 2018, p. 1)
  “These methods follow a similar Embedding&MLP paradigm: large scale sparse input features are first mapped into low dimensional embedding vectors, and then transformed into fixed-length vectors in a group-wise manner, finally concatenated together to fed into fully connected layers (also known as multilayer perceptron, MLP) to learn the nonlinear relations among features.” (Zhou et al., 2018, p. 1)
  深度学习推荐系统的传统范式：embedding+mlp，embedding 作为特征抽取器
- “Users might be interested in different kinds of goods simultaneously when visiting the e-commerce site. That is to say, user interests are diverse.” (Zhou et al., 2018, p. 1)
  DIN 的出发点：用户兴趣具有多样性，他可能对不同商品都有兴趣
- “When it comes to CTR prediction task, user interests are usually captured from user behavior data. Embedding&MLP methods learn the representation of all interests for a certain user by transforming the embedding vectors of user behaviors into a fixed-length vector, which is in an euclidean space where all users’ representation vectors are.” (Zhou et al., 2018, p. 1)
  在 CTR 预估任务中，用户兴趣表现在用户行为中
- “diverse interests of the user are compressed into a fixed-length vector, which limits the expressive ability of Embedding&MLP methods.” (Zhou et al., 2018, p. 1)
  用户兴趣的表示最终是一个定长的向量，这里的关键是不加区分的聚合用户兴趣（pooling 等方式），会造成信息的极大丢失，从而限制了 Embedding&MLP 的表达能力
- “On the other hand, it is not necessary to compress all the diverse interests of a certain user into the same vector when predicting a candidate ad because only part of user’s interests will influence his/her action (to click or not to click).” (Zhou et al., 2018, p. 1)
  给定候选项（待排商品/广告），在表示用户兴趣的时候，使用他所有的行为（行为表达了兴趣）是非必要的，因为只有行为过的商品才与候选项相关。
- “By introducing a local activation unit, DIN pays attentions to the related user interests by soft-searching for relevant parts of historical behaviors and takes a weighted sum pooling to obtain the representation of user interests with respect to the candidate ad.” (Zhou et al., 2018, p. 1)
  综上两点：DIN 使用注意力机制来软搜索（区别于硬过滤）用户历史行为中与给定候选项相关的部分，使用加权平均的方式来获得对于候选项的用户兴趣
- adding with traditional ℓ2 regularization, the computation turns to be unacceptable, which needs to calculate L2-norm over the whole parameters (with size scaling up to billions in our situation) for each mini-batch.” (Zhou et al., 2018, p. 2)
  对于推荐系统模型的训练，使用L2正则，它会对所有的参数计算L2正则项。由于推荐系统亿级的巨大参数量，计算效率是难以接受的。
- “we develop a novel mini-batch aware regularization where only parameters of non-zero features appearing in each mini-batch participate in the calculation of L2-norm, making the computation acceptable.” (Zhou et al., 2018, p. 2)
  DIN 由此提出了 mini-batch aware regularization，即针对当前的批量数据中非零特征对应的参数计算L2正则项，从而极大地减少计算量。
- “we design a data adaptive activation function, which generalizes commonly used PReLU[12] by adaptively adjusting the rectified point w.r.t. distribution of inputs and is shown to be helpful for training industrial networks with sparse features.” (Zhou et al., 2018, p. 2)
  DIN dice 是 PReLU 的变形，改动了两点：1、根据输入数据的分布来计算整流点，而不是固定为0，从曲线图上看，相当于左右平移了；2、原来的阶跃函数变得更加平滑
- “4 DEEP INTEREST NETWORK” (Zhou et al., 2018, p. 3)
  “4.1 Feature Representation” (Zhou et al., 2018, p. 3)
  “Then one instance can be represent as x = [tT 1 ,tT 2 , ...tT M ]T in a group-wise manner, where M is number of feature groups, ÍM i=1 Ki = K, K is dimensionality of the entire feature space” (Zhou et al., 2018, p. 3)
- (Zhou et al., 2018, p. 3)
  推荐系统特征的划分及其 vocab 大小（维度）：用户画像、用户行为、广告/商品特征、上下文特征。用户行为特征的维度相对更高，数据更加稀疏，这是因为使用的多少类目、ID型特征。DIN 用到了商品ID、店铺ID、商品类目ID。
- (Zhou et al., 2018, p. 3)
  从上表和当前示例，可以看到 DIN 将用户历史行为过的商品列表直接当作一个 multi-hot 向量来处理了。还原这个过程，用户历史行为过的商品列表，首先是一个 one-hot vector 的列表，也可以看作一个 one-hot matrix，将矩阵按商品维度求“与（AND）”，就压缩成了一个 multi-hot vector。
  看作列表/序列的形式，会更加自然，缺点是，这个列表是变长的。从 multi-hot vector 的视角来看的好处是，容易将其对应到特征抽取的定长向量（从向量到向量）。
- “Note that in our setting, there are no combination features. We capture the interaction of features with deep neural network.” (Zhou et al., 2018, p. 3)
  本文的实验中，没有实验特征组合，而是使用深度模型来做隐式的特征组合。
- “4.2 Base Model(Embedding&MLP)” (Zhou et al., 2018, p. 3)
- (Zhou et al., 2018, p. 4)
  sum-pooling 与 DIN 的 weighted-sum pooling 的模型结构对比，右上角是 DIN 提出的 local activation unit 的计算形式
- “4.3 The structure of Deep Interest Network” (Zhou et al., 2018, p. 4)
  “The local activation characteristic of user interests gives us inspiration to design a novel model named deep interest network(DIN).” (Zhou et al., 2018, p. 4)
  再次强调了 DIN 的设计初衷：用户兴趣的局部激活特性
- “behaviors related to displayed ad greatly contribute to the click action. DIN simulates this process by paying attention to the representation of locally activated interests w.r.t. given ad.” (Zhou et al., 2018, p. 4)
  DIN 用局部激活单元（注意力机制）模拟了用户行为序列中与给定广告/商品的相关度计算，计算得到的相关度，也是兴趣值。
- “However different from traditional attention method, the constraint of Í i wi = 1 is relaxed in Eq.(3), aiming to reserve the intensity of user interests. That is, normalization with softmax on the output of a(·) is abandoned. Instead, value of Í i wi is treated as an approximation of the intensity of activated user interests to some degree.” (Zhou et al., 2018, p. 5)
  DIN 的局部激活与常规 attention 的差异点：DIN 希望保留用户兴趣的强度，所以没有使用 softmax 做归一化。
- “We have tried LSTM to model user historical behavior data in the sequential manner. But it shows no improvement. Different from text which is under the constraint of grammar in NLP task, the sequence of user historical behaviors may contain multiple concurrent interests. Rapid jumping and sudden ending over these interests causes the sequence data of user behaviors to seem to be noisy.” (Zhou et al., 2018, p. 5)
  此时（DIN 在阿里实验的时间大约是 17年），尝试过使用 LSTM 来建模用户行为序列，没有取得可观的提升。这里作者的推测是：用户行为序列中同时包含了多种兴趣，相邻行为之间的联系不如 NLP 的词、句之间那么强，换言之，就是用户历史行为的跳跃性更强，难以被 RNN/LSTM 所捕获。
  后面他们提出的 DIEN 算是对此处未解问题的继续求解。
  我看过DUPN的模型示意图，它是先过  LSTM，再过 attention 的
- “5 TRAINING TECHNIQUES” (Zhou et al., 2018, p. 5)
  “5.1 Mini-batch Aware Regularization” (Zhou et al., 2018, p. 5)
  “Only parameters of non-zero sparse features appearing in each mini-batch needs to be updated in the scenario of SGD based optimization methods without regularization. However, when adding ℓ2 regularization it needs to calculate L2-norm over the whole parameters for each mini-batch, which leads to extremely heavy computations and is unacceptable with parameters scaling up to hundreds of millions.” (Zhou et al., 2018, p. 5)
  无正则项时，SGD 只会更新 mini-batch 中非零特征对应的参数；但是加入 L2 正则项之后，由于它的计算是针对整个参数空间的，因此会对所有参数计算正则项。这带来了巨大的计算开销。
- (Zhou et al., 2018, p. 5)
  Dice（公式见下） 与 PReLU 的对比，两点差异：1、整流点不再固定，根据输入数据计算；2、曲线变得更加平滑，不再是阶跃信号
- “5.2 Data Adaptive Activation Function” (Zhou et al., 2018, p. 5)
  “PReLU takes a hard rectified point with value of 0, which may be not suitable when the inputs of each layer follow different distributions.” (Zhou et al., 2018, p. 5)
  PReLU 的整流点固定为 0，这对于服从不同分布的数据是硬伤。
- (Zhou et al., 2018, p. 5)
  Dice 的函数式
- “In the training phrase, E[s] and V ar [s] is the mean and variance of input in each mini-batch. In the testing phrase, E[s] and V ar [s] is calculated by moving averages E[s] and V ar [s] over data. ε is a small constant which is set to be 10−8 in our practice.” (Zhou et al., 2018, p. 5)
  训练过程中，Dice 使用了每个 mini-batch 的均值与方差；测试时，则使用数据集上的移动平均来计算均值与方差。
- “6 EXPERIMENTS” (Zhou et al., 2018, p. 6)
  “6.1 Datasets and Experimental Setup” (Zhou et al., 2018, p. 6)
  “Amazon Dataset” (Zhou et al., 2018, p. 6)
  “MovieLens Dataset” (Zhou et al., 2018, p. 6)
  “We segment the data into training and testing dataset based on userID.” (Zhou et al., 2018, p. 6)
  使用用户 ID 来划分数据集
  更常规的做法应该是用 {date} 做测试集，{date}之前的 N 天数据做训练集，防止数据穿越。
- “Alibaba Dataset” (Zhou et al., 2018, p. 6)
  “For all the deep models, the dimensionality of embedding vector is 12 for the whole 16 groups of features. Layers of MLP is set by 192 × 200 × 80 × 2. Due to the huge size of data, we set the mini-batch size to be 5000 and use Adam[15] as the optimizer.” (Zhou et al., 2018, p. 6)
- “exponential decay, in which learning rate starts at 0.001 and decay rate is set to 0.9.” (Zhou et al., 2018, p. 6)
  DIN 的模型设置：emb_dim=12，mlp 的 hidden_size=192、200、80、2，batch_size=5000，使用 Adam，lr=0.001，衰退率为 0.9
- “6.3 Metrics” (Zhou et al., 2018, p. 6)
  “An variation of user weighted AUC is introduced in [7, 13] which measures the goodness of intra-user order by averaging AUC over users and is shown to be more relevant to online performance in display advertising system.” (Zhou et al., 2018, p. 6)
- (Zhou et al., 2018, p. 6)
  使用 GAUC 作为指标，按用户分组计算 AUC，再按曝光量求加权平均。按照本文的说法，GAUC 更能反映线上性能。
- “Besides, we follow [25] to introduce RelaImpr metric to measure relative improvement over models. For a random guesser, the value of AUC is 0.5.” (Zhou et al., 2018, p. 6)
- (Zhou et al., 2018, p. 6)
  本文实验的另一个 metric，AUC 的相对提升度
- (Zhou et al., 2018, p. 7)
  Alibaba 数据集上，不同模型的训练损失。绿色上线是不用正则项的 case，在一个 epoch 之后，开始严重过拟合。
- (Zhou et al., 2018, p. 7)
  在 MovieLens 和 Amazon 数据集上，DIN 与基线的对比，证明了其效果（DIN 🐂️🍺️）
- (Zhou et al., 2018, p. 7)
  正则化的消融实验，使用本文提出的 mini-batch aware regularization（MBA）效果最好
- “6.5 Performance of regularization” (Zhou et al., 2018, p. 7)
  “• Dropout[22]. Randomly discard 50% of feature ids in each sample. • Filter. Filter visited дoods_id by occurrence frequency in samples and leave only the most frequent ones. In our setting, top 20 million дoods_ids are left. • Regularization in DiFacto[16]. Parameters associated with frequent features are less over-regularized. • MBA. Our proposed Mini-Batch Aware regularization method (Eq.4). Regularization parameter λ for both DiFacto and MBA is searched and set to be 0.01.” (Zhou et al., 2018, p. 7)
  正则化消融实验的对照组：1、Dropout，注意看 droupout 的对象是 ID 们；2、过滤，过滤掉长尾商品 ID；3、Difacto，对高频和长尾特征使用不同的正则化力度，高频特征更不容易过正则化，因此加强对他们的正则，减弱长尾特征的正则
- “Dropout prevents quick overfitting but causes slower convergence. Frequency filter relieves overfitting to a degree. Regularization in DiFacto sets a greater penalty on дoods_id with high frequency, which performs worse than frequency filter.” (Zhou et al., 2018, p. 8)
  实验中，Dropout ID 特征，能够有效防止过拟合，但是训练收敛变得更慢；过滤长尾特征能够缓解过拟合；DiFacto 法也有一点效果。
- “6.7 Result from online A/B testing” (Zhou et al., 2018, p. 8)
  “Careful online A/B testing in the display advertising system in Alibaba was conducted from 2017-05 to 2017-06. During almost a month’s testing, DIN trained with the proposed regularizer and activation function contributes up to 10.0% CTR and 3.8% RPM(Revenue Per Mille) promotion4 compared with the introduced BaseModel, the last version of our online-serving model.” (Zhou et al., 2018, p. 8)
  线上做了近一个月的 ab 实验，CTR 提升显著：+10%！
- (Zhou et al., 2018, p. 8)
  DIN 与基线在 Alibaba 数据集上的性能对比
- “In our practice, several important techniques are deployed for accelerating online serving of industrial deep networks under the CPU-GPU architecture: i) request batching which merges adjacent requests from CPU to take advantage of GPU power, ii) GPU memory optimization which improves the access pattern to reduce wasted transactions in GPU memory, iii) concurrent kernel computation which allows execution of matrix computations to be processed with multiple CUDA kernels concurrently.” (Zhou et al., 2018, p. 8)
  为了 DIN 上线，做出的工程优化的点：1、相邻请求合并后再预估，充分利用 GPU 的算力，2、GPU 内存优化，3、并发优化
- “6.8 Visualization of DIN” (Zhou et al., 2018, p. 8)
  “Taking the young mother mentioned before as example, we randomly select 9 categories (dress, sport shoes, bags, etc) and 100 goods of each category as the candidate ads for her. Fig.6 shows the visualization of embedding vectors of goods with t-SNE[17] learned by DIN, in which points with same shape correspond to the same category. We can see that goods with same category almost belong to one cluster, which shows the clustering property of DIN embeddings clearly.” (Zhou et al., 2018, p. 8)
- “Besides, we color the points that represent candidate ads by the prediction value. Fig.6 is also a heat map of this mother’s interest density distribution for potential candidates in embedding space. It shows DIN can form a multimodal interest density distribution” (Zhou et al., 2018, p. 8)
- (Zhou et al., 2018, p. 9)
  DIN 的可视化效果，用户历史行为与候选的相关度
- (Zhou et al., 2018, p. 9)
  DIN 的可视化效果，可以看到，DIN 具有一定的聚类效果