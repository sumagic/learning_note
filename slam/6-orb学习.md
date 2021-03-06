# ORB learning note

## Papers

* ORB an efficient alternative to SIFT or SURF
* 

## 特征匹配

* 是计算机视觉应用场景中的一个基础问题，ORB论文中作者提出一种BRIEF的能够快速运行的二进制描述子计算方法，具有旋转不变性且对噪声有较强的抗干扰能力

* 该论文作者表明该算法在计算时间上要比sift算法快两个数量级，同时保持相似的检测效果

* ORB算法基于FAST角点检测算法和BRIEF描述子，因此成为ORB

### Fast算子

* [FAST算子描述](https://blog.csdn.net/lwx309025167/article/details/80234307)

* 角点： 是一种局部特征，具有旋转不变性质和不随光照条件变化而变化的特点。一般将图像中曲率足够高或者曲率变化明显的点作为角点
* 检测到的角点主要用于图像匹配、目标跟踪、运动估计等方面
* FAST角点认为，若某像素点与周围领域内足够多的像素点处于不同的区域，则该像素点可能为角点。也就是某些属性与众不同，考虑灰度图像，即若该点的灰度值比其周围领域内足够多的像素点的恢复值大或者小，则该点可能为角点

* 若是一个角点，超过3/4圆的部分应该满足判断条件，如果不满足，则p不可能是一个角点。对于所有点作上述这一步初步的检测后，符合条件的将成为候选的角点，我们再对候选的角点，作完整的测试，即检测圆上的所有点

###### 算法步骤

* 从图片中选取一个像素P，首先将它的亮度值设置为Ip；
* 设定一个合适的阈值t
* 考虑以该像素点为中心的一个半径为3像素的离散化的bresenham圆，这个圆的边界上有16个像素
* 现在如果在这个大小为16个像素的圆上有n个连续的像素点，他们的像素值要么都比Ip + t大，要么都比Ip - t小，那么他就是一个角点。n的值可以设置为12或者9，实验证明选择9是可能会有更好的选择
* 上述算法效率实际上很高，但是缺点如下：
* 当设置 n < 12时就不能使用快速算法来过滤非角点的点
* 角点不是最优的，效率取决于问题的排序和角点的分布
* 对于角点分析的结果被丢弃了
* 多个特征点容易挤在一起

##### 使用机器学习作一个角点分类器

* 首先使用FAST算法找出每幅图像的特征点
* 对于每一特征点，将其周围的16个像素存储构成一个向量
* 

##### 基本思想

* 06年出现的一篇论文
* 以某个像素点为圆心，某半径的圆周上其他像素点与圆心像素点特性差异达到某种标准时即认为该点就是角点

##### 数学模型

* 测试发现，选取的圆形半径为3时可以兼顾检测效果和效率。
* 对图像中所有像素点进行操作后，得到候选点点集。通常使用非极大值抑制过滤局部非极大值点，在这之前需要先计算各候选点的score，score由定义为16个点与中心点灰度值差值的绝对值总和

* 该算法的问题在于对于边缘点与噪点区分能力不强
* 该算法只有一个参数，就是中心点灰度值和圆形邻域内其他点灰度值之间的差值阈值

### BRIEF算子

* papers: BRIEF-binary-robust-indepdent-elementary-features
* 采用二进制编码的方法对特征点周围区域提取描述子，存储空间比SIFT、SURF更小，采用Hamming Distance进行比较，匹配速度更快
* 


### 质心法计算旋转角度

* 角点的方向主要用于描述特征描述子的旋转不变性——强度质心法
* 一般一个图像块的强度质心是偏离物理中心的，我们可以用这个偏离计算得到一个方向
* 