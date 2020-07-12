# learning note
*[GFlags使用文档](http://www.yeolar.com/note/2014/12/14/gflags/)

## introduction
* GFlags是Google开源的一个命令行flag（区别于参数）库
* 和 getopt() 之类的库不同，flag的定义可以散布在各个源码中，而不用放在一起。一个源码文件可以定义一些它自己的flag,链接了该文件的应用都能使用这些flag。这样就能非常方便地复用代码。如果不同的文件定义了相同的flag，链接时会报错。
* GFlags是一个C++库，同时也有一个Python移植，使用完全相同的接口。

## 使用cmake链接gflags
* 最新版本的GFlags已经可以支持CMake了
    ```CMake
        find_package (gflags REQUIRED) include_directories (${gflags_INCLUDE_DIR})s
        add_executable (foo main.cc) target_link_libraries (foo gflags)
    ```


# glog的使用

* 在CMakeLists.txt中添加如下语句即可：
    ```CMake
        find_package(Glog REQUIRED)
        include_directories(BEFORE ${GLOG_INCLUDE_DIRS}) 
    ```
* 在main函数的文件中添加
    ```cpp
        #include <iostream>
        #include <glog/logging.h>  
        int main(int argc, char **argv) {
            google::InitGoogleLogging(argv[0]);  
            google::SetLogDestination(google::GLOG_FATAL, "./log/log_fatal_"); 
            google::SetLogDestination(google::GLOG_ERROR, "./log/log_error_"); 
            google::SetLogDestination(google::GLOG_WARNING, "./log/log_warning_"); 
            google::SetLogDestination(google::GLOG_INFO, "./log/log_info_"); 
            LOG(INFO) << "HELLO" << "ok!";  
            return 0;
        }
    ```
* 在其他文件中使用glog
    ```c++
        #include <glog/logging.h>
    ```
    然后在需要的地方使用LOG(INFO),WARNING, ERROR, FATAL等信息