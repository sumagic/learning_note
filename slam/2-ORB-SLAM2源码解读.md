# orb-slam2 note

[link](https://zhuanlan.zhihu.com/p/83735700)

## [SLAM的引入](https://blog.csdn.net/lwx309025167/article/details/80257549)

* 同时定位和地图构建
* 它是指搭载特定传感器的主体，在没有环境先验信息的环境下，于运动过程中建立环境的模型，同时估计自己的运动。如果这里的传感器主要为相机，那就称为视觉SLAM
* 开发背景： 稀疏路标地图作为定位；稠密地图作为导航和避障和重建；语义地图作为交互

##### 视觉SLAM设备选型

* 设备选型的重要性不言而喻，毕竟好模型驾不住坏数据。SLAM模型建立得再好，如果设备采集的数据本身误差过大，计算结果必定也不理想。
* 为了加快开发，若选择能够提供开发SDK等工具的厂家，可以省去对相机的标定、数据同步等开发工作
* 

## [1 系统流程](https://zhuanlan.zhihu.com/p/83735700)

* orb一共由三个线程，分别是跟踪(tracking), 局部建图(local mapping)和闭环(loop closing)功能，同时又增加了重定位(place recognition)功能

* 系统流程的入口在system.cc文件中，这个文件中一共由四个函数：
* system；trackStereo；TrackRGBD; TrackMonocular
* 其中system是SLAM系统的构造函数，包括所有功能模块和所有线程的初始化，后面的3个分别是双目，RGBD和单目的数据入口，使用过程中，先调用system函数生成SLAM系统的对象，然后根据传感器类型，调用相应的入口函数，就可以执行SLAM的流程了。

### 初始化词袋模型

* 词袋是再做闭环检测和重定位时候做检索用的，从历史关键帧中检索出和当前帧最相似的一帧，以进行位姿匹配
[link](https://www.zhihu.com/question/49153462/answer/114807054)

* 为了减少累积误差，目前visual slam都假如回环检测了，并通过后端优化来纠正整个回环中的姿态估计误差。要实现回环检测，slam系统要回答一个问题，这个场景之前我是不是见过，而且是在可能出现平移+缩放+旋转的情形下，判断当前帧和之前记录过的帧是不是来源于同一个场景。这个问题落入到基于内容的图像检索范畴

* ORBSLAM采用的是bag-of-words的方式将图像中的多个局部描述符表示成一个定长的全局特征，而vocabulary tree是局部描述符量化和索引的一种高效数据结构

### 初始化关键帧数据集

### 初始化地图

### 初始化用户显示界面，并打开对应的线程

### 初始化局部地图，并打开对应的线程

### 初始化闭环流程，并打开对应的线程

### 给各个线程之间建立关联

## MapPoint类

* MapPoint是地图中的特征点，它自身的参数是三维坐标和描述子， 在这个类中它需要完成的主要工作如下

* 维护关键帧之间的共视关系
* 通过计算描述向量之间的距离，再多个关键帧的特征点中找最匹配的特征点
* 在闭环完成修正之后，需要根据修正的主帧位姿修正特征点
* 对于非关键帧，呀产生MapPoint，只不多是给tracking功能临时使用

### system.h .cc学习

## System类

* 构造函数，初始化slam系统: **拉起local mapping**、**闭环检测和可视化线程** [但是通常不推荐在构造函数中进行逻辑处理，没有返回值无法进行判断]

* cv::FileStorage，存储数据和读取指定标记好的数据
* cv::FileStorage fp(filename, cv::FileStorage::WRITE), 写入数据
* 读取数据： cv::FileStorage::READ
* fp.release()
* fp.isOpened()
* std::thread* pointer, 在主线程内跟踪线程

### load ORB Vocabulary

##### [vocabulary tree](https://www.zhihu.com/question/49153462)

* 为了减少累积误差，目前visual slam都加入回环检测了，并通过后端优化来纠正整个回环中的姿态误差。
* 要实现回环检测，slam系统需要回答一个问题，这个场景之前是不是出现过，而且是在可能出现平移、缩放、旋转的情形下，判断当前帧与之前记录过的帧是否来源于同一个场景。
* 回环检测落到基于内容的图像检索范畴

* 新建 vocabulary

* 新建keyFrame Database: KeyFrameDataBase()

* 新建map

* 创建可视化画图

* 初始化Tracking线程: 存在于执行的主线程中

* mapping thread

* 初始化闭环检测线程

* 初始化viewer线程

* 线程pointer： 

##### vocabulary tree的构建流程

* 对应用场景下的大量训练图像历险提取局部描述符(words)
* 将这些描述符号 KNN聚成 k类
* 对于上一步的每一自类，继续KNN聚成k类
* 按照这个循环，直到聚类的层次数达到阈值L

* vocabulary tree实际上就是通过学习的方法实现对原始特征空间的一种划分
* ORB-SLAM2中附带的ORBvoc.txt是使用大量通用场景下的图像提取ORB特征分类聚集出来的。
* 该文件存在于 Vocabulary/ORBvoc.txt文件中

##### 

## Vocabulary 类

* 定义在 include/ORBVocabulary.h中
* 使用 DBOW2中定义的vocabulary
* 

## KeyFrameDataBase 类


## ORB特征提取

### oriented FAST

### BRIEF描述子

## 相机标定算法

* 