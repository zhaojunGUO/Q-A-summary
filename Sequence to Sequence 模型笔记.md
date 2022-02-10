# Sequence to Sequence 模型笔记

## Sequence to Sequence

RNN：每个cell使用上一个hidden state来输入对应的hiden state和output。使用每个时刻的output或者最后时刻的hidden state来输出结果。所以模型具有的**问题**是：模型输入和输出的比例只能是t:t 或者是t:1 

而Sequence to Sequence的模型优点是：在 Encoder 中，将可变长度的序列转变为固定长度的向量表达，Decoder 将这个固定长度的向量转换为可变长度的目标的信号序列。

![img](https://upload-images.jianshu.io/upload_images/244848-2aca743a6ad3194d.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200)

最基础的 Seq2Seq模型 包含了三个部分，即 Encoder、Decoder 以及连接两者的中间状态向量 C，Encoder通过学习输入，将其编码成一个固定大小的状态向量 C（也称为语义编码），继而将 C 传给Decoder，Decoder再通过对状态向量 C 的学习来进行输出对应的序列。

训练过程：

encoder input: 原始序列作为输入

decoder input： 训练时将`decoder_target`往后移一位，第一位是`<S>`，例如原序列为“ABC”，输出序列为“WXYZ”，那么训练时`decoder_input`为`<S>WXYZ`

decoder target：愿序列的输入序列



预测：

encoder input：需要预测的序列

decoder input：第一位输入使用`<S>`，其后使用上一时刻的输出作为输入



## Sequence to Sequence Attention

加入了模拟人类注意力机制

早在计算机视觉目标检测相关的内容学习时，我们就提到过注意力机制的思想，目标检测中的 Fast R-CNN 利用 RoI（兴趣区域）来更好的执行检测任务，其中 RoI 便是注意力模型在计算机视觉上的应用。

普通Sequence to Sequence的问题：并不能有效的聚焦到输入目标上

比如：“我 爱 你” 在普通的Sequence to Sequence中“你” 在解码时每一个输出都会使用这个“你”进行解码

而加入了注意力机制后，模型会根据序列的每个时间步将编码器编码为不同 C，在解码时，结合每个不同的 C 进行解码输出，这样得到的结果会更加准确

假设这里有t个Encoder hidden states。Attention主要步骤为：

1. 准备前t个encoder隐藏层和第t+1个decoder隐藏层
2. 计算attention score
3. softmax转为proba
4. 把softmax score分别乘以每个vector
5. 把第四步骤得到的t个vector相加

![img](https://upload-images.jianshu.io/upload_images/244848-464154d2a8369253.png?imageMogr2/auto-orient/strip|imageView2/2/w/934)

<img width="748" alt="截屏2022-02-10 19 35 00" src="https://user-images.githubusercontent.com/64532223/153473918-38126cd9-f79c-4ce5-be49-412b11e91018.png">
