# VFS（virtual file system）学习笔记

* VFS是一个异构文件系统之上的软件黏合层，有时也把VFS称为可堆叠的文件系统，stackable filesystem，因为VFS可以无缝地使用多个不同类型的文件系统，就像把多个文件系统堆叠在一起。通过VFS，可以为访问文件系统的系统调用提供一个统一的抽象接口

* VFS的作用就是采用标注的UNIX系统调用读写位于不同物理介质上的不同文件系统，可以让open,read,write等系统调用不用关心底层的存储介质和文件系统类型就可以工作的粘合层

* 