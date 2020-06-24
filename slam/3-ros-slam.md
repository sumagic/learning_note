# ROS_SLAM

## [ROS激光SLAM导航](https://blog.csdn.net/luohuiwu/article/details/92787237)

* gmapping包是ROS里对开元社区openslam下gmapping算法的c++实现，该算法采用一种高效的rao-blackwellized粒子滤波将收取到的激光测距数据最终转换为栅格地图

* 机器人定位与建图通常被认为是鸡与鸡蛋的问题，所以即时定位与地图构建(SLAM)是这样一个概念，把两方面的进程都捆绑在一个循环之中，以此来支持双方在各自进程中都求得连续解；不同进程中相互迭代的反馈对双方的连续解有改进作用

* 