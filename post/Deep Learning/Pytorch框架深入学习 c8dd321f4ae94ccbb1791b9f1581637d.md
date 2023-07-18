# Pytorch框架深入学习

基础

进阶

高级

实践

## 参考教程

[机器视觉全栈|机器视觉教程|docsify|pytorch官方教程中文版|opencv-python官方教程中文版|open3D(0.15.1)官方教程中文版 (cvtutorials.com)](http://www.cvtutorials.com/#/)

## 基础知识

CPU上的张量和NumPy数组可以共享它们的底层内存位置，改变一个将改变另一个

## 深度学习训练模板

### 数据处理

一般来说，当你需要处理图像、文本、音频或视频数据时，你可以使用标准的Python包，将数据加载到一个numpy数组。然后你可以将这个数组转换为torch.*Tensor。

- 对于图像，诸如Pillow、OpenCV等包是有用的。
- 对于音频，诸如scipy和librosa等软件包。
- 对于文本，原始Python或基于Cython的加载，或者NLTK和SpaCy都很有用

PyTorch提供了两个数据模块：torch.utils.data.DataLoader和torch.utils.data.Dataset，允许你使用预先加载的数据集以及你自己的数据。Dataset存储了样本及其相应的标签，而DataLoader对Dataset包裹了一个可迭代的数据集，以便能够方便地访问这些样本。

一种方法是直接下载Pytorch内置的数据集。另一个是针对自定义的数据集，一个自定义数据集类必须实现三个函数：**`__init__`(初始化目录，目录中包括图像文件、标注文件和变换)**, **`__len__`(返回我们数据集中的样本数)**, 和 **`__getitem__`(在给定的索引idx处加载并返回数据集中的一个样本)**。

数据并不总是以训练机器学习算法所需的最终处理形式出现。我们使用变换来对数据进行一些操作，使其适合训练。torchvision.transforms模块提供了几个常用的变换，开箱即用。

如何判断模型所需的训练数据量

[How Much Training Data is Required for Machine Learning? - MachineLearningMastery.com](https://machinelearningmastery.com/much-training-data-required-machine-learning)

### 模型构建

- torch.nn： Module：创建一个类似于函数的可调用文件，但也可以包含状态（如神经网层权重）。它知道它所包含的Parameter，并可以将它们的梯度归零，通过它们进行权重更新的循环，等等； Parameter：一个tensor的包装器，告诉模块它有需要在后向传播过程中更新的权重。只有设置了require_grad属性的tensor才会被更新； functional: 一个模块（通常按惯例导入到F命名空间），包含激活函数、损失函数等，以及卷积层和线性层等非状态化版本。
- torch.optim：包含优化器，如SGD，它在后向传播步骤中更新Parameters的权重。
- Dataset：一个具有__len__和__getitem__对象的抽象接口，包括Pytorch提供的类，如TensorDataset
- DataLoader：接受任何Dataset并创建一个迭代器，返回批样本。

我们希望能够在像GPU这样的硬件加速器上训练我们的模型，如果它是可用的。让我们检查一下torch.cuda是否可用，否则我们继续使用CPU。

我们通过子类化 nn.Module 来定义我们的神经网络，并在 **`__init__`**
中初始化神经网络层。每个 nn.Module 子类都在 forward 方法中实现了对输入数据的操作。

查看模型信息：

为了计算这些梯度，PyTorch有一个内置的微分引擎，叫做torch.autograd。它支持对任何计算图的梯度进行自动计算。

我们需要能够计算损失函数相对于这些变量的梯度。为了做到这一点，我们设置了这些tensor的 requires_grad 属性。

当我们已经训练好了模型，只是想把它应用于一些输入数据，也就是说，我们只想通过网络进行前向计算。我们可以通过用torch.no_grad()块包围我们的计算代码来停止跟踪计算。

你可能想禁用梯度跟踪，原因如下：

- 将神经网络中的一些参数标记为冻结参数。这是对预训练的网络进行微调的一个非常常见的情况。
- 当你只做前向传递时，为了加快计算速度，对不跟踪梯度的tensor的计算会更有效率。

### 训练

超参数是可调整的参数，让你控制模型优化过程。不同的超参数值会影响模型的训练和收敛率

一旦我们设定了超参数，我们就可以通过优化Loop来训练和优化我们的模型。优化循环的每一次迭代被称为一个epoch。

每个epoch由两个主要部分组成。

- 训练loop--在训练数据集上迭代，试图收敛到最佳参数。
- 验证/测试循环--迭代测试数据集，以检查模型性能是否在提高。

常见的损失函数包括用于回归任务的nn.MSELoss（均方误差）和用于分类的nn.NLLLoss（负对数似然）

优化是在每个训练步骤中调整模型参数以减少模型误差的过程。优化算法定义了这个过程是如何进行的（在这个例子中，我们使用随机梯度下降法）。所有的优化逻辑都被封装在优化器对象中。在这里，我们使用SGD优化器；此外，PyTorch中还有许多不同的优化器，如Adam和RMSProp，它们对不同类型的模型和数据有更好的效果。

在训练loop中，优化分三步进行。

- 调用optimizer.zero_grad()来重置模型参数的梯度。梯度默认为累加；为了防止重复计算，我们在每次迭代中明确地将其归零。
- 通过调用loss.backwards()对预测损失进行反向传播。PyTorch将损失的梯度与每个参数联系在一起。
- 一旦我们有了梯度，我们就可以调用optimizer.step()来根据向后传递中收集的梯度调整参数。

### 测试

### 保存与载入模型

PyTorch模型将学到的参数存储在内部状态字典中，称为state_dict。这些可以通过torch.save方法持久化。

为了加载模型的权重，你需要先创建一个相同模型的实例，然后用load_state_dict()方法加载参数。

在加载模型权重时，我们需要先将模型类实例化，因为该类定义了网络的结构。我们可能想把这个类的结构和模型一起保存，在这种情况下，我们可以把模型（而不是model.state_dict()）传给保存函数。

PyTorch也有内置的ONNX导出支持。然而，由于PyTorch执行图的动态性质，导出过程必须遍历执行图以产生持久的ONNX模型。出于这个原因，应该向导出程序传递一个适当大小的测试变量（在我们的例子中，将创建一个正确形状且值为零的tensor）。

[ONNX学习笔记 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/346511883)

开放神经网络交换（Open Neural Network Exchange）简称ONNX是微软和Facebook提出用来表示深度学习模型的**开放**格式。所谓开放就是ONNX定义了一组和环境，平台均无关的标准格式，来增强各种AI模型的可交互性。

换句话说，无论你使用何种训练框架训练模型（比如TensorFlow/Pytorch/OneFlow/Paddle），在训练完毕后你都可以将这些框架的模型统一转换为ONNX这种统一的格式进行存储。注意ONNX文件不仅仅存储了神经网络模型的权重，同时也存储了模型的结构信息以及网络中每一层的输入输出和一些其它的辅助信息。