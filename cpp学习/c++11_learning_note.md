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

* reserve()函数和容器的capacity相关

## pause

* int pause(void): 使调用进程(线程)进入休眠状态，就是挂起；直到收到信号且信号函数成功返回，pause函数才会返回
* 返回值，始终返回-1
* 当我们没有发送信号时，pause会阻塞
* 当进程接收到信号时，不会立刻返回，只有当信号处理函数返回时，pause才会返回-1
* pause函数使得该进程暂停让出CPU，但是该函数的暂停和前面的那个sleep函数的睡眠都是可以被中断的睡眠。也就是说收到了中断信号之后再重新执行该进程的时候，就直接执行pause和sleep函数之后的语句

##### 在一个多线程的进程中，信号的捕获会产生混淆

## alarm

* alarm(time): 该函数执行之后告诉内核，让内核在time秒时间之后向该进程发送一个定时信号，然后该进程捕捉该信号并处理
* 触发的信号名称： SIGALRM
* 该信号只触发一次，如果想要反复触发，可以在信号处理函数里继续注册该事件

## pthread_sigmask

* 线程中的信号屏蔽函数

## sigemptyset: 清除信号集合

## select实现定时

* select函数: 用超时来实现定时
* 