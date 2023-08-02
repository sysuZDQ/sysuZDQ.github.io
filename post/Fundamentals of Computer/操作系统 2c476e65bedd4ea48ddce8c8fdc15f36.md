# 操作系统

操作系统功能：操作系统位于硬件资源之上，管理硬件资源*;* 应⽤程序之下，为应⽤程序提供服务，同时管理应⽤程序

- 资源分配，资源回收
- 为应用程序提供服务
- 管理应用程序

操作系统内核的功能

- 进程调度能力： 管理进程、线程，决定哪个进程、线程使⽤CPU。
- 内存管理能力： 决定内存的分配和回收。
- 硬件通信能力：管理硬件，为进程和硬件之间提供通信。
- 系统调⽤能力： 应⽤程序进⾏更⾼限权运⾏的服务，需要系统调⽤，⽤户程序和操作
系统之间的接口

操作系统的角色：魔术师与管理者

- 管理者：主要分为：CPU管理、内存管理、外存管理、IO管理；以及⾃⼰的健壮性和安全性管理。
- 魔术师：⽐如操作系统会让每个进程都觉得⾃⼰独占CPU、独占整⽚物理内存，⽽实际上每个进程都只是在某⼀时间段内占⽤CPU，仅仅只是占⽤实际⼀点点物理内存。

操作系统的特征

- 并发（最重要、其他特征的前提）：两个或多个事件在同一时间间隔内发生
- 共享：系统中的资源可供内存中多个并发执行的进程共同使用、资源共享即共享
    - 互斥共享方式（对摄像头设备的共享使用）
    - 互斥共享方式（对摄像头设备的共享使用）
- 虚拟：把一个物理上的实体变为若干逻辑上的对应物（分时使用资源）
- 异步：多道程序环境允许多个程序并发执行，由于资源有限，进程的执行不是一贯到底的，而是走走停停的，它以不可预知的速度向前推进

操作系统的基本知识（参考王道的分类：[《王道操作系统》学习笔记总目录+思维导图_王道操作系统思维导图_BitHachi的博客-CSDN博客](https://blog.csdn.net/weixin_43914604/article/details/104415990)）

- 计算机系统概述
    - 操作系统的概念、功能、特征、发展、分类
    - 操作系统的运行机制和体系结构、中断和异常、系统调用
- 进程管理
    - 进程和线程
    - 处理机调度
    - 进程的同步与互斥
    - 死锁
- 内存管理
    - 内存管理的概念（内存空间的分配与回收、扩充、地址转换、存储保护）
    - 虚拟内存管理
- 文件管理
    - 文件系统
    - 磁盘组织与管理
- I/O管理
    - I/O管理概述（分类、I/O控制器、控制方式、I/O软件的层次结构）
    - I/O核心子系统（SPOOLing、I/O设备的分配与回收、缓冲区管理）

## 一、进程

1、进程运行的流程

![Untitled](%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%202c476e65bedd4ea48ddce8c8fdc15f36/Untitled.png)

2、socket编程

![Untitled](%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%202c476e65bedd4ea48ddce8c8fdc15f36/Untitled%201.png)

## 二、线程

## 三、并发

[30张图解：高并发服务模型哪家强？ (qq.com)](https://mp.weixin.qq.com/s/a2Q1DQqOHdhtGEjJ4QxPew)

## 四、存储

1、内存的构成

![Untitled](%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%202c476e65bedd4ea48ddce8c8fdc15f36/Untitled%202.png)

2、压缩算法

- 把文件内容用 `数据 * 重复次数` 的形式来表示的压缩方法成为 `RLE(Run Length Encoding, 行程长度编码)`  算法
- ****哈夫曼算法和莫尔斯编码****

## 五、互斥和同步

## 六、文件系统

## 七、Linux的系统接口

[阅前必读 - 《Linux API速查手册》 - 书栈网 · BookStack](https://www.bookstack.cn/read/linuxapi/README.md)

[Linux命令大全(手册) – 真正好用的Linux命令在线查询网站 (linuxcool.com)](https://www.linuxcool.com/)

## 八、Windows的系统接口

[Windows API函数大全(完整) - 狂想NICE - 博客园 (cnblogs.com)](https://www.cnblogs.com/kuangxiangnice/p/10990668.html)

[说明简介 (office-cn.net)](http://www.office-cn.net/t/api/index.html?web.htm)

[pywin32库 : Python 操作 windows 系统 API_擒贼先擒王的博客-CSDN博客](https://blog.csdn.net/freeking101/article/details/88231952)

## 九、CPU

1、程序执行过程

![Untitled](%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%202c476e65bedd4ea48ddce8c8fdc15f36/Untitled%203.png)

2、CPU中的寄存器

![Untitled](%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%202c476e65bedd4ea48ddce8c8fdc15f36/Untitled%204.png)

3、CPU指令执行过程

![Untitled](%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%202c476e65bedd4ea48ddce8c8fdc15f36/Untitled%205.png)

4、冯诺依曼体系

![Untitled](%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%202c476e65bedd4ea48ddce8c8fdc15f36/Untitled%206.png)