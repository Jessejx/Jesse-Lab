# 1/2/3d CNN

## Conv1d, Conv2d and Conv3d
本节的主要内容就是一边看文档，一边用代码验证。在PyTorch中，分别在`torch.nn`和`torch.nn.functional`两个模块都有conv1d，conv2d和conv3d；从计算过程来说，
两者本身没有太大区别；但是`torch.nn`下的都是layer，conv的参数都是经过训练得到；`torch.nn.functional`下的都是函数，其参数可以人为设置。本文在分析时，两者
的文档一起看，但是实验主要以`torch.nn.functional`为主，更加方便修改。
### Conv1d
``` torch.nn.functional.conv1d(input, weight, bias=None, stride=1, padding=0, dilation=1, groups=1)  ```
`input`  
input是一维输入，其形状为```(Batch_Size,In_Channel,Length)```；```Batch_Size```是训练批量的大小；```In_Channel```是输入的通道数量；```Length```是输入的长度，因为是一维输入，
所以其只有长度。下图展示了一个一维输入，其包括3个通道：input如图所示  
![conv1d's input](./Record/figure2.png)  
 `weight`
 weight是一维卷积核，其形状为```(Out_Channel,In_Channel/Group,Kernel_Size)```；```Out_Channel```是输出的通道数量；```In_Channel/Group```
 的目的是决定每一层的输出是如何由输入组成的，后续会详细介绍，此处不妨设```Group=1```；```Kernel_Size```是一维卷积核的大小。下图展示了一个一维卷
 积核和其对应的累加方式：  
![conv1d's calculate](./Record/figure3.png)  
`group`
group我觉得应该属于卷机核的一个重要参数，从我们较为熟悉的2dcnn来说，group可以理解为filter的数量，在此rep中，我们使用一组图像来理解1dcnn中的group参数  
![group=1](./Record/figure4.jpg)
![group=3](./Record/figure5.jpg)  
`stride and padding`  
stride理解起来还是很容易；当stride=1时，卷积核在原始输入上以步长为1进行移动.stride理解起来还是很容易；当stride=1时，卷积核在原始输入上以步长为1进行移动.  
`dilation`  
```dilation```，按照我的理解就是带孔卷积，其控制输入层上的取样间隔，当dilation=1时，就是前文所示的卷积。下图展示了一个dilation=2的情形，不难发现，这个参数能够
在不增强计算量的前提下增大感受野。
![dilation=2](./Record/figure6.jpg)  
### Conv2d and Conv3d
原则上讲，如果看文档，会发现conv2d、conv3d和conv1d并没有太大的区别，只不过在维度上有所区别。因此，我也就不分开介绍，
直接放在一起。不难发现，唯一的区别在于维度的上升；因此为weights的定义也有所不同，分别是`(Out_Channels, In_channels/Groups,kH,kW)`
和`(Out_Channels, In_channels/Groups，kT,kH,kW)`。并且，conv2d和3d还是存在一定的不同  
* `conv3d`除了可以在图像平面上移动卷积之外，还可以在深度方向进行卷积；而`conv2d`并没有这个能力。 
* `conv3d`中的深度和`conv2d`中的Channel是不对应的，`conv3d`中的每一个深度上都可以对应多个Channel，因此深度和Channel是不同的概念

### Pytorch of 1、2 and 3d cnn
1. conv1d

