# bazel learning note

## workspace

* bazel的编译是基于workspace的概念
* 工作区是一个存放了所有源代码和bazel编译输出文件的目录，也就是整个项目的根目录。
* workspace总是存放在项目的根目录下
* 一个或者多个BUILD文件，用于告诉bazel怎么构建项目的不同部分
* BUILD文件中的每一条编译指令被成为一个target，它指向一系列的源文件和依赖，一个target也可以指向别的target
* cc_binary, 构建一个可执行二级制文件
* 
