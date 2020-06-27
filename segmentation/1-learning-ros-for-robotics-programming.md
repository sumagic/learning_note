# learning ros for robotics programming note

* book pdf

## 概念

### ROS Filesystem

* ROS程序分成几个文件夹

* Packages: 来自ROS的同一个level。一个package有最小的结构和内容来创建内容。包含ROS runtime processes(nodes)，配置文件等等

* Manifests: 提供一个package的信息，例如license information, dependencies, compiler flags等等。Manifests使用一个文件管理： manifests.xml

* stacks： 当想要聚集一些package的时候，你将获得一个stack。在ROS里面有很多使用不同的栈，例如, navigation stack

* stack manifests: stack manifests(stack.xml)提供了关于一个stack的数据，包括license信息和它在其他stack的栈

* Message (msg) types: 一个进程发送给其他进程的information格式。ROS有很多标准的message类型。存储在 my_package/msg/MyMessageType.msg

* service (srv) types: service描述，存储在 my_package/srv/myserviceType.srv，定义ROS中服务中的请求和响应的数据结构

### Packages

* 
