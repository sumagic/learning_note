# cmake note

## [include_directories and find_package](https://blog.csdn.net/weixin_39393741/article/details/85070299)

* cmake本身不提供任何搜索库的便捷方法，所有搜索库并给变量赋值的操作必须由cmake代码完成

* include_directories, 用来提供找头文件路径
* find_package(<name>) 会在模块路径中寻找Find<name>.cmake，这是查找库的一个典型的方式
* 具体查找路径为CMake变量: ${CMAKE_MODULE_PATH}中的所有目录；如果没有，然后再查找自己的模块。这称为模块模式
* 如果没有找到这样的文件，find_package()会在～/.cmake/packages/或者/usr/local/share/中的各个包目录中查找，寻找<库名字的大写>Config.cmake或者<库名字的小写>-config.cmake。这成为配置模式

###### cmake变量设置

* 不管使用哪一种模式，只要找到*.cmake, *.cmake里面都会定义下面这些变量
* <NAME>_FOUND;<NAME>_INCLUDE_DIRS OR <NAME>_INCLUDES
* <NAME>_LIBRARIES or <NAME>_LIBRARIES or <NAME>_LIBS
* <NAME>_DEFINITIONS

###### 