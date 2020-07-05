### c++ std::chrono时间库

* chrono是C++11中的时间库，提供计时、时钟等功能
* 学习chrono的关键是理解里面时间段(durations)、时间点(time points)的概念

### c++ 多线程 thread类

* C++11新标准中引入了4个头文件来支持多线程
* <atomic>,<thread>, <mutex>, <condition_variable>, <future>

##### std::thread

* 默认构造函数，创建一个新的thread执行对象
* 拷贝构造函数被禁用，意味着thread不可以被拷贝和构造


##### vector 中的reserve和resize的区别

* resize(n): 调整容器的长度大小，使得其能容纳n个元素；如果n小于容器的当前size，则删除多出来的元素；否则，添加采用值初始化的元素

* resize(n, t): 多一个参数，将所有新添加的元素初始化为t

* reserve(n), 预分配n个元素的存储空间

* 了解resize和reserve的区别，就需要首先了解size和capacity的区别

* resize()函数和容器的size相关，调用resize(n)之后，容器的size就是n；至于是否影响capacity,取决于调整后的容器的size是否大于capacity

* reserve()函数和容器的capacity相关，