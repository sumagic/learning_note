# ROS学习

## [命令](https://blog.csdn.net/BenjaminYoung29/article/details/47067995)

* 程序代码是分布在众多的ros软件包中，当使用命令行工具浏览非常麻烦，因此提供了专门的命令工具来简化操作

* rospack find， 返回包的安装路径

## [创建ROS Package](https://blog.csdn.net/BenjaminYoung29/article/details/47068411)

* 一个package必须至少包含以下两个文件： package.xml; CMakeList.txt
* 进入到src目录下执行 catkin_create_pkg


## [理解节点和话题](https://blog.csdn.net/BenjaminYoung29/article/details/47072835)

* ros开始与一个master
* 首先，所有的节点都要到master登记，这样master才能直到信息要传递到哪个节点。

## 理解ros服务和参数

## 使用rosed编辑ROS的文件

* 在rviz中无法使用传感器信息，所以需要使用包含物理引擎的3D仿真器gazebo

* 