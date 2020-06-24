# ros教程

## ROS的构建系统

* 默认使用CMake
* 在ROS中，CMake被修改为适合于ROS的catkin构建系统

### 创建功能包

* catkin_create_pkg [功能包名称][依赖功能包1][依赖功能包n]
* 该命令在创建用户功能包时会生成catkin构建系统所需的CMakeLists.txt和package.xml文件的包目录
* ros的功能包中名称全部是小写字母，不能包含空格

### 构建功能包

* 在构建之前，使用rospack profile命令更新ROS功能包的配置文件，将之前创建的功能包反映在ROS功能包列表的命令

## 第7章 ROS编程基础

### 创建工作区(workspace)

* [ROS空间创建](https://www.cnblogs.com/wjundong/p/10957824.html)
* 创建目录 pkg_dir
* cd pkg_dir && mkdir src
* cd src && catkin_init_workspace: 在当前目录下生成CMakeList.txt文件
* cd pkg_dir && catkin_make ：编译,在当前目录下生成build, devel, src文件夹
* 使用bash中进行注册：source devel/setup.bash
* echo ${ROS_PACKAGE_PATH}, 可以看到目录已经添加到环境变量中

##### 编译过程中的问题总结

* 找不到em: sudo apt-get install python3-empy
* catkin_pkg找不到：
    locate catkin_pkg; # 找到该目录为catkin_pkd_dir
    export PYTHONPATH={catkin_pkg_dir}:${PATHONPATH}

### 创建ROS工程包(package)

* 首先切换到工作区
* cd pkg_dir/src
* catkin_create_pkg ros_beginner std_msgs rospy roscpp
* cd pkg_dir && catkin_make
* 找不到ros pkg时，导出环境变量即可： source devel/setup.bash
* 发布者的名字需要和订阅者的名字一致就可以进行数据的通信。


