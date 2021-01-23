# learning note 《点云库PCL学习教程.pdf》

## 3.3 PCL已有点类型介绍和增加自定义的点类型

* PCL从开始就伴随着各种预定义的point类型，从用于XYZ数据到更加复杂的n维直方图表示，这些类型足够支持在PCL中应用的算法与方法

### PointT类型

* 大家认为，点云时复杂的n维结构，它需要能表示不同类型的信息
* PCL中所有的算法都是模板化的，除了更改的自定义结构之外不需要作其他的更改，增加了代码的重用性和可读性

##### PCL中可用的PointT类型

###### PointXYZ, 成员变量，float x,y,z

* 只包含XYZ坐标信息，这三个浮点数附加一个浮点数来满足存储对齐

###### PointXYZI, 成员变量：float x, y, z, intensity

###### PointXYZRGBA, 成员变量，float x,y,z; uint32_t rgba

###### PointXY, float x,y

###### InterestPoint, float x,y,z,strength

* strength表示关键点的强度的测量值

###### Normal， float normal, curvature

* normal结构体表示给定点所在样本曲面上的法线方向，以及对应曲率的测量值

###### PointNormal, float x,y,z; float normal[3], curvature

* 存储XYZ数据的point结构体，并且包括采样点对应法线和曲率

###### PointXYZRGBNormal

###### PointWithRange, float x,y,z

* 除了range包含从所获得的视点到采样点的距离测量值之外，其他与PointXYZI类似

### 如何在模板类中使用这些point类型

## 第4章 输出/输入IO

* PCL中所有的处理都是基于点云展开的，利用不同的设备获取点云、存储点云等都是点云处理前后必须作的流程
* PCL中有自己设计的内部PCD文件格式
* PCL内部支持对常用的3D格式文件的打开与存储操作，以及与PCD内部格式之间的相互转化

### openNI

* 开放式自然交互
* 一个非营利性组织，致力于提高和改善自然交互设备与应用软件的互操作能力
* openNI的主要目的时形成标准的API，便于以下两个接口之间进行通信
* 视觉和音频传感器
* 视觉和音频感知中间件

### PCL中IO模块以及类介绍

* IO库中提供了点云文件输入输出相关的操作类，并封装了openNI兼容的设备源数据获取接口，可直接从众多感知设备获取点云图像等数据
* 实现对点云数据的获取、读取、存储等，依赖common模块、octree模块和openNI外部开发包

##### class pcl::FileReader

* 定义了PCD文件的读取接口，主要用作其他读取类的父类
* 该类中的纯虚函数其继承关系

##### class pcl::FileWriter

##### class pcl::Grabber

* 为PCL1.x对应的设备驱动接口的基类定义

