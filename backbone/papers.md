# papers<br>

### Backbone: 什么是Backbone?<br>
* [link](https://zhuanlan.zhihu.com/p/99548894)<br>
* 用来提取特征的就是CNN中的backbone，backbone的复杂度在很大程度上决定了整网算法的耗时<br>
* RCNN的文章表明，将大规模的多尺度的分类问题中训练的模型作为目标检测的预训练模型，可以为训练检测器提供更丰富的语义信息，且可以提高检测性能。<br>
### 常见的backbone<br>
* VGG16是在AlexNet的基础上发展而来的，VGG16提出一个观点，通过堆加卷积层增加网络的深度，可以提高模型的表达能力。但是越深越梯度弥散<br>
* renet提出后，深层网络向浅层反向传递的时候就像有了一条高速公路，所以再深的网络都不怕梯度弥散了。常见的resnet有16层和101层, 152层。<br>
* densenet作者认为resnet没有很好的利用浅层的特征，导致参数浪费，因此提出DenseNet:把所有层都链接起来了，主要优点就是：增强特征传播，鼓励特征复用，更少的参数量<br>

### densenet
* [Densely Connected Convolutional Networks](http://xxx.itp.ac.cn/pdf/1608.06993.pdf)<br>
* [Convolutional Networks with Dense Connectivity](http://xxx.itp.ac.cn/pdf/2001.02394.pdf)<br>

### vgg
* [VERY DEEP CONVOLUTIONAL NETWORKS FOR LARGE-SCALE IMAGE RECOGNITION](http://xxx.itp.ac.cn/pdf/1409.1556.pdf)<br>

### resnet
* [Deep Residual Learning for Image Recognition](http://xxx.itp.ac.cn/pdf/1512.03385.pdf)<br>

### googLeNet
* inception v1: [Going deeper with convolutions](http://xxx.itp.ac.cn/pdf/1409.4842.pdf)<br>
* inception v2,v3: [Rethinking the Inception Architecture for Computer Vision](http://xxx.itp.ac.cn/pdf/1512.00567v3.pdf)<br>
* inception v4: [Inception-v4, Inception-ResNet and the Impact of Residual Connections on Learning](http://xxx.itp.ac.cn/pdf/1602.07261.pdf)<br>

### mobileNet
* mobileNet v1: [mobileNet_v1]()
* mobileNet v2: [mobileNet_v2]()
* mobileNet v3: [mobileNet_v3]()