# C++ Note.md

## [c++运行期断言和编译期断言](https://www.cnblogs.com/mywolrd/archive/2009/08/26/1930692.html)

* 通常为了检测一些条件，我们在程序里面加断言。
* 一般只在DEBUG版有效，RELEASE版本断言不生成任何代码。
* C++可以使用两种断言，静态断言和动态断言，就是运行期断言和编译期断言。
* 编译期断言是再程序运行过程中判断指定的条件，如果条件不满足，编译期给出错误提示，需要人为实现，只要条件不成立，程序是编译不通过的。
* [编译期断言](http://www.360doc.com/content/13/1231/17/6828497_341537049.shtml)
* 编译期断言： compile-time assertion

## [c++11静态断言](static_assert)

* c++0x中引入了static_assert关键字，用来做编译期的断言，因此叫做静态断言
* 用法： static_assert(常量表达式， 提示字符串)
* 如果第一个参数常量表达式的值为真(true或者非零值)，不作任何事情，否则会产生一条编译错误，错误位置就是该static_assert语句所在行，错误提示就是第二个参数提示字符串

## [c++ new带括号和不带括号](https://www.cnblogs.com/youxin/p/3735064.html)

* 