### c++ std::chrono时间库

* chrono是C++11中的时间库，提供计时、时钟等功能
* 学习chrono的关键是理解里面时间段(durations)、时间点(time points)的概念

### c++ 多线程 thread类

* C++11新标准中引入了4个头文件来支持多线程
* <atomic>,<thread>, <mutex>, <condition_variable>, <future>

##### std::thread

* 默认构造函数，创建一个新的thread执行对象
* 拷贝构造函数被禁用，意味着thread不可以被拷贝和构造
* 