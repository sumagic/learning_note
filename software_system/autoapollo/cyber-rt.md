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