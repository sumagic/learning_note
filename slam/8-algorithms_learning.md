# algorithms learning

# VO, visual odometry

## RANSAC

* 随机抽样一致
* random sample consensus
* 从一组包含局外点的观测数据集中，通过迭代方式估计数学模型的参数
* 是一种不确定的算法，有一定的概率得出一个合理的结果
* 为了提高得到合理结果的概率，必须提高迭代次数
* 

## BA

* bundle adjustment


### slding window bundle adjustment

* 

## image registration

* [图像配准技术研究](https://wenku.baidu.com/view/2b4656229ec3d5bbfc0a742d.html)
* 图像配准技术研究
* 傅里叶-梅林变换，通过对图像进行平移、缩放、旋转等一系列变换对两幅图像或者几幅图像进行配准
* 图像配准是说把多福在不同因素影响下获取的图像进行整合配准
* 通过寻找某种方法把一幅图像映射到另一幅图像，把多福待配准的图像的点进行融合以此来得到配准后的图像
* 把多个图像上的信息结合到一起，然后在同一张图像上统一显示出来

### 图像配准的步骤

* 首先进行特征检测，接下来对待配准图像进行对比，紧接着变换模型，最后实现把两幅图像的相同的部分提取实现配准
* 主要原则是根据图像的不同处理方法来区别图像配准，可以通过频域和时域进行配准
* 常用的方法，表面分析法，非线性变换法，取点法，矩阵法，主轴法，最大互信息法，曲线法，流体力学模型法，相关相位法，光流场模型法等


## 如何解决随着里程的增加产生的轨迹递增的问题

* 使用windows bundle adjustment
* 融合多传感器，比如GPS，IMU等

## full convariance kalman

## 刚体的旋转矩阵和平移运动

* vo的目的是实现路径的计算，摄像头作为一个agent，attached到实际的rover物体上，因此该物体的轨迹就是实际的路径简化
* vo的计算方法是计算前后帧的变换矩阵T，然后将所有的变换矩阵concat到一起。初始位置和姿态可以随意取，最后的位置和姿态综合以上即有一个确定的值
* 变换矩阵T的计算有两种方法，一种是appearance-based method，另一种是feature-basedmethod
* 前者计算量大而且不准确；后者计算量小准确

* feature matching 和feature tracking是不同的内容，要学会区分


### 数学计算

* 3D-2D的投影方程

## 摄像头标定

* checkboard-like pattern


## 图优化

## 多视图几何

## 相机标定

