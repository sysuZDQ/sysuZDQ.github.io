# ***Deep Learning***     
2015年，深度学习三巨头携手撰写了一篇综述性文章[Deep learning](https://www.nature.com/articles/nature14539.pdf)。对于刚入门深度学习的同学来说，这篇文章可能是一个好的选择。   

-----
## ***Learning Deep Neural Network from Scratch***
什么是神经网络呢？或许你的脑海中马上就浮现出一个大致的轮廓，但要你仔细地按照原理娓娓道来你很可能就会磕磕绊绊了。所以，我们要必要清晰把握神经网络的基本思想和发展脉络，以便我们日后能够将自己天马行空的想法付诸于其中！    
### ***A Simple Neural Network***
一个简单的神经网络就是输入为$X=(x_1,x_2,...,x_n)$，得到输出$y$。通过调整权重$W=(w_1,w_2,...,w_n)$使得你输入的$X$能得到你想要的$y$，就比如我们常见的图片分类，输入的$X$是图片的表征，这里的$y$就是我们的类别标记$0,1,2,3.....$，最后将这些数字映射到例如猫，狗，马等标签     
<div align=center><img src="..\..\image\DL\23b6869fada0eb4acacbf16ef141922.jpg" width="500"></div>  
这时你会想，这个激活函数是干嘛的呀？很显然，仅以一条直线（我们这里以输入为一维来举例，多维的同理）划分区域是远远不够的。因此我们需要引入非线性，这里就是激活函数的意义啦！常见的激活函数如下，但是一般ReLU会用的比较多。 
 <div align=center><img src="..\..\image\DL\9f8dd136e38433c68c86d7ee6c9cfd7.jpg" width="500"></div>    
 最后，经过多次线性和非线性的变化，就可以达到期望的分类
 <div align=center><img src="..\..\image\DL\c6466eecad906013013ad4f2219ad61.jpg" width="500"></div>

 好了，我们已经清楚了每个模块的意义。接下来你肯定会好奇训练学习是什么？我们期望得到一个函数，他能使得我们的输入都能得到期望的输出，那么得到这个函数的过程就是训练了！这在里，我们就是要得到权值$W$。因此，我们先随机初始化$W$，然后通过前向传播计算出$y$，此时我们得到的$y$和我们的期望肯定不一样的，那么就我们就需要利用这个差值信息来调整$W$，也就是说我们期望这个差值最小，因此我们寻找的是最小值。这里的做法就是通过[梯度下降](https://www.bilibili.com/video/BV18P4y1j7uH/?spm_id_from=333.788&vd_source=16860f65fea90013288ea5a6ba1bba3a)反向传播回去，使得$W$能不断地朝着目前调整。梯度为0的点就是最低点，因此我们就有了一个目标，朝着梯度下降的地方调整！     
 细心的同学肯定会疑惑，这个最低点可能是极小点而不是全局最小点啊？没错，这确实是一个问题，具体可以看看[这里](https://blog.csdn.net/weixin_42887138/article/details/112499704)的分析

## ***CNN***
既然已经有了上面的网络，那么为什么还有卷积神经网络的诞生呢？这篇[博客](https://blog.csdn.net/weixin_44177568/article/details/102812050)可以回答你的问题！    
所谓卷积，公式描述为$f(t)*g(t)=\int f(\tau)g(t-\tau)d\tau$，本质上就是两个函数重叠的部分。   
卷积神经网络的基本思想是：利用卷积核的特征提取能力，通过多层级联，实现多尺度特征学习
<div align=center><img src="..\..\image\DL\20201105221547811.png" width="500"></div>   

### **卷积层**
利用卷积核将输入的矩阵进行映射，最后在通过激活函数，这里卷积核的数值就是可学习的参数，而个数是我们的超参数，不同的卷积核关注的特征不一样    
### **池化层**
将信息进一步汇聚起来，即抓住主要矛盾，忽略次要矛盾。常见的有最大池化、平均池化   
### **全连接层**
最后将上面学到的特征综合起来，得到期望的输出


## ***RNN***
那么有人就会问，既然有BP神经网络和CNN，为什么还要RNN呢?这个就跟RNN的循环有关了，之前的BP神经网络和CNN的每一个神经元输入输出都是相互独立的，互相并没有产生干扰或者联系，而在实际应用场景中呢?有些场景的输出内容和之前的内容是有关联的，例如你说的话肯定是有语序的，倘如改变了顺序语义也会改变了，也就是一种“记忆”的概念，因此RNN引入这个概念，循环就是指每一个神经元都执行相同的任务，但是输出不仅依赖于输入，还依赖于神经元自身之前的“记忆”。   
RNN的公式为$S_{t}=f(W_{in}X+W_SS_{t-1}+b)$   
<div align=center><img src="..\..\image\DL\575a470f4e25d2debbf0e789372d1fe.jpg" width="500"></div> 

至于RNN的记忆问题，可以想象，间隔越长，梯度越小，如$f(g(h(x)))=0.1*0.1*0.1$   
为了解决该问题，LSTM诞生了   
<div align=center><img src="..\..\image\DL\490a5d78edc4fe3af683f646b41a4d4.jpg" width="500"></div>    

## ***Transformer***
最简单的encoder-decoder架构就是将一个RNN分为两部分。
<div align=center><img src="..\..\image\DL\44ee6d5374ee1cef56b5c4a5b832b19.jpg" width="500"></div>    
但是仅仅以一个$C$来存储一个句子的信息精度有限，因此使用attention机制对每一个token都产生一个表征。
<div align=center><img src="..\..\image\DL\1fa446e67a14de71cd94678444ae043.jpg" width="500"></div>  
这样还有一个问题，就是不能并行操作，特别对于现在普遍使用GPU进行运算来说，这样的特性显然是不能被容忍的。既然我们已经使用attention机制融合了上下文，那么这个顺序运算我们可以去除   
<div align=center><img src="..\..\image\DL\1ead9a280b2c0480127a40d3dda97aa.jpg" width="500"></div>   
最后，我们给出关于attention的一些基本知识  
<div align=center><img src="..\..\image\DL\561d05caebced4fedbc72d77ac949bc.jpg" width="500"></div>    

想进一步了解transformer的同学，可以看我对论文[Attention Is All You Need](../论文解读/Attention%20Is%20All%20You%20Need.html)的解读！