# bag of words learning note

## [BOW算法介绍](https://www.cnblogs.com/mafuqiang/p/7111424.html)

* bag of words, 是图像检索中最常用的俄方法，也是基于内容的图像检索中最基础的算法
* bag of words是用于文本检索，后被引用与图像检索， 和SIFT等出色的局部特征描述符共同使用
* 也叫bag of feature, BOF, 表示出比暴力匹配效率更高的图像检索效果，它是直接使用k-means对局部描述符进行聚类，获得一定数量的视觉单词，然后量化再统计词频或TF-IDF加权之后的权重系数
* 随着图像数据库的扩大，图像数据增加，所使用的马术规模也越来越大，k-means的效率就比较低了；为了改善大规模图像检索场景下的图像检索效果，有人提出了vocabulary tree（VT）算法，它是对BOW算法的一种改进算法，也就是我们常看见的分层量化的bow算法。

## [dbow2算法解析](https://blog.csdn.net/Zinan_Lin/article/details/73187961)

* dbow2算法主要用于重定位或者称作闭环检测，loop closure或者place recognition
* 使用ORB特征，这是一种结合了FAST特征和BRIEF描述子的特征
* 作者将特征点的描述子空间离散化，构建了词树(vocabulary tree)。然后用这种树作为几何验证阶段快速寻找点的对应

### 二值特征

* ORB特征是一种结合了FAST特征和BRIEF描述的一种特征，FAST关键点是一种角点，它通过在一个半径为3的bresenham圆中比较一些像素的灰度来获得。 然后在每一个FAST特征点的周围都选取一个方形的patch计算BRIEF描述子。BRIEF描述子是用一个二值向量来表示的，向量中的每一位都是patch中灰度值进行比较的结果，patch大小和向量的长度都是事先约定号的，可以根据世纪需要选择合适的值。

### [bag-of-words模型原理](https://zhuanlan.zhihu.com/p/136613724)

* bag-of-words模型假定对于一个文档，忽略它的单词顺序和语法、句法等要素，将其仅仅看作是若干个词汇的集合，文档中每个单词的出现都是独立的，不依赖于其他单词是否出现;无关顺序

### [bag-of-words模型入门](https://zhuanlan.zhihu.com/p/29933242)

* Bag-of-words模型是信息检索领域常用的文档表示方法
* 现在想象一个巨大的文档集合D，里面一共有M个文档，而文档里面的所有单词提取出来之后，一起构成一个包含N个单词的词典，利用bag-of-words模型，每个文档都可以被表示成为一个N维向量

* 变成N维向量之后，很多问题很好处理，计算机非常善于处理数值向量，我们可以通过余弦来求两个文档之间的相似度，也可以将这个向量作为特征向量送入分类器进行主体分类等一系列功能中

### SIFT算法

* 用SIFT作图像匹配效果不错
* SIFT算法是提取图像中局部不变特征的应用最为广泛的算法，因此我们可以用SIFT算法从图像中提取不变特征点，作为视觉词汇，并构造单词表，用单词表中的单词表示一幅图像

### [bag-of-words模型应用三步](https://yq.aliyun.com/articles/83866)

* 第一步，bag-of-words模型的第一步是利用SIFT算法，从每类图像中提取视觉词汇，将所有的视觉词汇集合在一起;这些向量代表的是图像中局部不变的特征点
* 第二步，利用K-means算法构造单词表，k-means算法是一种基于样本间相似性度量的间接聚类方法。SIFT提取的视觉词汇向量之间距离的远近，可以和i用k-means算法将词义相近的词汇合并，作为单词表中的基础词汇；构造一个包含K个词汇的单词表
* 第三步，利用单词表的中词汇表示图像，利用SIFT算法，可以从每个图像中提取很多个特征点，这些特征点都可以用单词表中的单词近似代替，通过统计单词表中每个单词在图像中出现的次数；从而将图像表示成为一个K维数值向量

##### [DBOW C++实现]()

* 