## cyber-rt notes

### website link
    1. [cyber框架](https://zhuanlan.zhihu.com/p/91322837)
    2. cyber是一个分布式收发消息和调度框架，同时对外提供一系列的工具和接口来辅助开发和定位问题。
    3. cyber相比ROS来说有很多优势，唯一的恶劣就是cyber相对ROS没有丰富的算法库支持

### cyber入口
    1. cyber/mainboard中
    '''c++
    ├── mainboard.cc           // 主函数
    ├── module_argument.cc     // 模块输入参数
    ├── module_argument.h
    ├── module_controller.cc   // 模块加载，卸载
    └── module_controller.h
    '''
    2. 

### cyber RT学习
* [apollo cyber rt操作系统学习记录](https://blog.csdn.net/jinfagang1211/article/details/87198285)
<img src="../data/img/cyberrt-architecture.png">cyberrt架构</img>
* cyberRT最底层的是一些apollo内部使用的库，为了减少依赖，提高整个系统的效率，许多轮子自己造。比如他们自己实现的高效率的FreeList对象回收池；
* 再往上是通信相关的，包括服务发现，publish-subscribe通信机制。CyberRT也支持跨进程、跨机器通信，上层业务逻辑无需关心，通信层会根据算法模块的部署，自动选择相应通信机制
* 通信层之上是数据缓存/融合层，多路传感器之间数据需要融合，而且算法可能需要缓存一定的数据。数据层起到了这个模块间通信桥梁的作用。
* 再往上是计算层，计算模型包括刚才前面提到的调度和任务。
* 计算模型之上是为开发者提供的借口。cyber rt为开发者提供了component类，开发者的算法业务模块只需要继承该类，实现其中的proc接口即可。cyberrt基于协程，为开发者提供了并行计算相关的接口
* cyberrt中另外一个比较重要的创新就是，改变了ROS里面的调度顺序，或者说ROS里面其实并没有调度，完全依赖于系统，此时就会导致系统负载过多过乱，cyberrt再这个基础之上引入自建调度体系，这是一个十分重要创新。
* apollo里面讲算法搭载再协程之上，是轻量化的线程。现成是进程下面的多个并行化的任务，线程与线程之间的通信必须通过信道进行，而协程可以直接通过访问全局变量来进行协程之间的通信。具体如何搭载要看代码实现和分析了。

### cyberrt源码分析
* cyberrt的实现是模块化的，重要的就是component和croutine两个模块，后者是自己实现的一个高性能的协程库，为整个系统提供协程的调用。

##### ros存在哪些问题
* 烦人的master，由于master的存在，导致每次的ros工程都要启动master节点，一旦master挂机了，其他节点都GG;
* ros内部没有调度，完全依赖于操作系统，所以进程之间没有优先性，这回导致一些重要的节点有时候会由于其他非重要节点的抢占而卡顿，二有时候他们的卡顿是致命的。
* cyber是框架，也就是调度的东西，所有的节点都变成了modules，也就是模块

## cyberrt架构
* [cyberrt架构](https://blog.csdn.net/qq_25762163/article/details/103591766)
* 