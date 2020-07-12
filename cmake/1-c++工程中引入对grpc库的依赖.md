# grpc作为第三方那个库在cmake中的应用
* [在C++工程中使用grpc](https://zhuanlan.zhihu.com/p/129832642)
    
## 使用步骤
1. 在cmake/Modules中加入FindGRPC.cmake和FindProtobuf.cmake这两个文件
2. 然后在工程的主CMakeLists.txt中及加入模块寻找的位置
    ```CMake
        list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_LIST_DIR}/cmake/Modules)
        find_package(Protobuf REQUIRED)
        find_package(GRPC REQUIRED)
    ```
3. 把所有的proto文件放在一个目录下面
    ```CMake
        set(PROTOS core/protos/helloworld.proto)
    ```
4. 所有要编译好的protos类放到这个目录下，一般是build目录下：
    ```CMake
        set(PROTO_SRC_DIR ${CMAKE_CURRENT_BINARY_DIR}/core/proto_src)
        file(MAKE_DIRECTORY ${PROTO_SRC_DIR})
        include_directories(${PROTO_SRC_DIR})
        protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS ${PROTO_SRC_DIR} ${PROTOS})
        grpc_generate_cpp(GRPC_SRCS GRPC_HDRS ${PROTO_SRC_DIR} ${PROTOS})
    ```
5. 将所有的服务都放在一个目录中
    ```CMake
        add_executable(greeter_server
            ${CMAKE_CURRENT_SOURCE_DIR}/core/src/http://greeter_server.cc
            ${PROTO_SRCS}
            ${GRPC_SRCS}
        )
        target_link_libraries(greeter_server
            gRPC::grpc++_reflection
            protobuf::libprotobuf
        )
    ```