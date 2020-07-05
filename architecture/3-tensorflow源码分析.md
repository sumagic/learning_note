# tensorflow 源码分析 learning note
[bilibili](https://www.bilibili.com/video/BV1XW411n7Ur)

## tensorflow基本架构

* tensorflow实际上3部分，分成client-->master-->worker， 数据一步一步往下流

### client

* 客户端python可以做，C++可以做
* session准备
* python代码封装了一个图对象， protobuf对象，传输给master
* 声明constant, placeholder, variable, tensor, operate等并构建graph
* client计算依赖，
* Master接收graph，通过计算denpences, node placement算算法分解，将任务(子图)下发给worker
* worker(CPU, GPU)，执行subgraph
* worker通过kernel函数完成计算并返回
* 整个数据的传输全部是通过protobuf来实现的

### GraphDef, graph的定义

* 数据格式(protobuf)与grpc
* python只是构建了一个protobuf的graph
* protobuf --> tf.session.run() --> c++ master
* 