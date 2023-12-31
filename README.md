# pic


# LeNet5网络介绍
在本次项目中，我们使用的是LeNet5实现手写数字识别目标的。下面我将对LeNet5做出详细介绍。<br>
 ![](https://raw.githubusercontent.com/zq111724/pic/main/1.png)<br>
LeNet5的基本结构包括7层网络结构（不含输入层），其中包括2个卷积层、2个降采样层（池化层）、2个全连接层和输出层。<br>
输入层：接收大小为的手写数字图像，其中包括灰度值（0-255）。在实际应用中，我们通常会对输入图像进行预处理，例如对像素值进行归一化，以加快训练速度和提高模型的准确性。<br>
卷积层C1：包括6个卷积核，每个卷积核的大小为，步长为1，填充为0。因此，每个卷积核会产生一个大小为的特征图（输出通道数为6）。<br>
采样层S2：采用最大池化（max-pooling）操作，每个窗口的大小为，步长为2。因此，每个池化操作会从4个相邻的特征图中选择最大值，产生一个大小为的特征图（输出通道数为6）。这样可以减少特征图的大小，提高计算效率，并且对于轻微的位置变化可以保持一定的不变性。<br>
卷积层C3：包括16个卷积核，每个卷积核的大小为，步长为1，填充为0。因此，每个卷积核会产生一个大小为的特征图（输出通道数为16）。<br>
采样层S4：采用最大池化操作，每个窗口的大小为，步长为2。因此，每个池化操作会从4个相邻的特征图中选择最大值，产生一个大小为的特征图（输出通道数为16）。<br>
全连接层C5：将每个大小为的特征图拉成一个长度为400的向量，并通过一个带有120个神经元的全连接层进行连接。120是由LeNet-5的设计者根据实验得到的最佳值。<br>
全连接层F6：将120个神经元连接到84个神经元。<br>
输出层：由10个神经元组成，每个神经元对应0-9中的一个数字，并输出最终的分类结果。在训练过程中，使用交叉熵损失函数计算输出层的误差，并通过反向传播算法更新卷积核和全连接层的权重参数。<br>
该网络在MINST数据集中表现优秀，可以达到98%以上的准确率。<br>

# MNIST数据集介绍
MNIST数据集是手写数字识别数据集，由60000张训练图像和10000张测试图像组成。每张图像的大小为28x28像素，表示一个手写的数字。MNIST数据集来自美国国家标准与技术研究所, National Institute of Standards and Technology (NIST). 训练集 (training set) 由来自 250 个不同人手写的数字构成, 其中 50% 是高中学生, 50% 来自人口普查局 (the Census Bureau) 的工作人员. 测试集(test set) 也是同样比例的手写数字数据。<br>
 ![](https://raw.githubusercontent.com/zq111724/pic/main/2.png)<br>
在该项目中，我们直接使用pytorch的处理图像视频的torchvision工具集下载MNIST的训练和测试图片，数据集的图片是以字节的形式进行存储，在我们进行训练和测试时可以直接使用 torch.utils.data.DataLoader 进行加载。<br>
