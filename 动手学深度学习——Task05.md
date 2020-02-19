#### 一.卷积神经网络基础
二维卷积层二维卷积层一般用来处理图像数据，这里的核心函数是处理矩阵做卷积操作的。
池化层主要为了缓解卷积层对位置的过度敏感性，常用的是最大池化层，也有用平均池化层的，同样涉及 Padding 和 Stride 的问题。在处理多通道数据时，会对每个输入通道分别池化，这一点和卷积层的相加不一样了。池化层无法通过类似 1x1 的技巧改变通道数，只是一个简单的调整，也不涉及任何参数的学习。
#### 二.LeNet
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200219173045355.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L01BVExBQjY3OA==,size_16,color_FFFFFF,t_70)
#### 三.卷积神经网络进阶
AlexNet
特征：
8层变换，其中有5层卷积和2层全连接隐藏层，以及1个全连接输出层。
将sigmoid激活函数改成了更加简单的ReLU激活函数。
用Dropout来控制全连接层的模型复杂度。
引入数据增强，如翻转、裁剪和颜色变化，从而进一步扩大数据集来缓解过拟合。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200219173235478.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L01BVExBQjY3OA==,size_16,color_FFFFFF,t_70)

