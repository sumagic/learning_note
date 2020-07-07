# cmake learning note.md

## 指令学习

* CMAKE_BUILD_TYPE: Debug, Release

### include

* 用来载入并运行来自于文件或者模块的cmake代码
* include (<file|module>[OPTIONAL][RESULT_VARIABLE <VAR>] [NO_POLICY_SCOPE])

* 如果使用的是一个module，<modulename>.cmake将会首先在CMAKE_MODULE_PATH变量中搜索，再在CMAKE module 目录中。

* check_cxx_compiler_flag(<flag><var>): 检查编译器是否支持给定的flag

##### [LIST](https://www.cnblogs.com/narjaja/p/8343765.html)

* LENGTH, GET, APPEND, FIND, INSERT, REMOVE_ITEM, REMOVE_AT...

* cmake中的list是以分号隔开的一组字符串，可以使用set命令创建一个列表
* list与set命令类似

### [find_package](https://blog.csdn.net/haluoluo211/article/details/80559341)

* 当编译一个需要使用第三方的软件时，我们需要知道.h文件的位置(GCC -I)，链接二进制文件的位置(GCC -L)，链接二进制文件的名字(GCC -l)

* include_directories(xxx)
* target_link_libraries(xxx)

* 同样可以是使用cmake提供的finder
* find_package的查找路径：首先在模块路径中寻找find.cmake.具体查找路径依次为，CMAKE变量 CMAKE_MODULE_PATH中的所有目录。
* 为了能支持各种常见的库和包，cmake自带了很多模块。可以通过cmake --help-module-list查看
* 