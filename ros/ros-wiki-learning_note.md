# ros-wiki-learning_note.md

## [理解ROS节点](http://wiki.ros.org/cn/ROS/Tutorials/UnderstandingNodes)

* Nodes: 节点，一个节点即为一个可执行文件，它可以通过ROS与其他节点进行通信
* Messages: 消息，是一种ROS数据类型，用于订阅或发布到一个话题
* Topics: 话题，节点可以发布消息到话题，也可以订阅话题以接受消息
* Master: 节点管理其

### 节点：

* 一个节点不过是ROS程序包的一个可执行文件。

### 客户端

* ros客户端允许使用不同编程语言编写的节点之间互相通信

### 编写简单的服务器和客户端(c++)

### 数据录制和回放

* [数据录制和回放](http://wiki.ros.org/cn/ROS/Tutorials/Recording%20and%20playing%20back%20data)

* 录制所有发布的话题
* rostopic list -v， 发布部分列出的话题消息是唯一可以被录制保存到文件中的话题消息，因为只有消息已经发布了才可以被录制
* rosbag record -a，该选项表示将当前发布的所有话题数据都录制保存到一个bag文件中
* 查看bag的信息： rosbag info xxx.bag

### 数据包回放

* rosbag play xxx.bag

### 录制数据子集

* 当运行一个复杂的系统时，会有几百个话题被发布。在这种系统中，要想将所有的话题都录制保存到硬盘上的单个bag文件是不现实的。rosbag record命令支持只录制某些特别指定的话题到单个bag文件中。

* rosbag record -O topicxxx

### [安全检查](http://wiki.ros.org/cn/ROS/Tutorials/Getting%20started%20with%20roswtf)

* roswtf可以检查你的ROS系统并尝试发现问题
* rosdep install，能够下载并安装ROS package所需要的系统依赖项的小工具
* 依赖配置在package.xml文件中

### 自定义消息： msg

* ros使用一个简单的msg描述符语言来描述数据的类型。
* 使得自动生成代码很简单

##### msg描述符说明

* fieldType filename
* 定义常量: constantype1 CONSTANTNAME1 = constancvalue1
* 