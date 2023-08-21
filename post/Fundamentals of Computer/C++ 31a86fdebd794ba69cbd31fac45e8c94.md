# C++

可分为三个阶段进行学习

[这才是你最想要的 C++ 学习路线 (zhihu.com)](https://www.zhihu.com/tardis/zm/art/435927070?source_id=1005)

## **一、入门阶段**

**入门阶段的学习主要是熟悉 C++ 语言的语法知识。**

*除了基础的变量、常量、关键字、数据类型、运算符、数组、函数、指针、结构体外，还要学习 C++ 的面向对象编程思想、命名空间 namespace、引用、函数扩展、类的封装、构造和析构、继承、多态、异常处理等内容*

### 1、简介

C++ 是一种静态类型的、编译式的、通用的、大小写敏感的、不规则的编程语言，支持过程化编程、面向对象编程和泛型编程。

面向对象四大特性：封装、继承、多态、抽象

标准的 C++ 由三个重要部分组成：

- 核心语言，提供了所有构件块，包括变量、数据类型和常量，等等。
- C++ 标准库，提供了大量的函数，用于操作文件、字符串等。
- 标准模板库（STL），提供了大量的方法，用于操作数据结构等。

C++ 语言在许多行业和领域都有广泛应用，包括：

- 游戏开发：C++ 是游戏开发领域中最常用的编程语言之一，因为它具有高效的性能和直接控制硬件的能力。许多主要的游戏引擎，如 Unreal Engine 和 Unity，都使用 C++ 编写。
- 嵌入式系统开发：C++ 可以在嵌入式系统中发挥重要作用，如智能手机、汽车、机器人和家电等领域。由于嵌入式系统通常具有严格的资源限制和实时要求，因此 C++ 的高效性能和内存控制功能非常有用。
- 金融领域：C++ 在金融领域中被广泛应用，如高频交易、算法交易和风险管理等领域。由于这些应用程序需要高效的性能和对硬件的直接控制，C++ 语言是一个合适的选择。
- 图形图像处理：C++ 可以用于开发图形和图像处理应用程序，如计算机视觉、计算机图形学和人工智能领域。由于这些应用程序需要高效的计算能力和对硬件的控制，因此 C++ 是一个很好的选择。
- 科学计算和数值分析：C++ 可以用于开发科学计算和数值分析应用程序，如数值模拟和高性能计算等领域。由于这些应用程序需要高效的计算能力和对硬件的直接控制，C++ 语言是一个很好的选择。

目前已经是**第五个**C++标准（C++17）

GNU 的 **gcc** 编译器适合于 C 和 C++ 编程语言。

****g++ 常用命令选项（用于指定如何进行编码）****

一般来说有三个地方可以定义变量：

- 在函数或一个代码块内部声明的变量，称为**局部变量**。
- 在函数参数的定义中声明的变量，称为**形式参数**。
- 在所有函数外部声明的变量，称为**全局变量**。

作用域是程序的一个区域，变量的作用域可以分为以下几种：

- **局部作用域**：在函数内部声明的变量具有局部作用域，它们只能在函数内部访问。局部变量在函数每次被调用时被创建，在函数执行完后被销毁。
- **全局作用域**：在所有函数和代码块之外声明的变量具有全局作用域，它们可以被程序中的任何函数访问。全局变量在程序开始时被创建，在程序结束时被销毁。
- **块作用域**：在代码块内部声明的变量具有块作用域，它们只能在代码块内部访问。块作用域变量在代码块每次被执行时被创建，在代码块执行完后被销毁。
- **类作用域**：在类内部声明的变量具有类作用域，它们可以被类的所有成员函数访问。类作用域变量的生命周期与类的生命周期相同。

### 二、基础语法

[C++ 的关键字（保留字）完整介绍 | 菜鸟教程 (runoob.com)](https://www.runoob.com/w3cnote/cpp-keyword-intro.html)

数据类型：`bool、char、int、float、double、void、wchar_t(类型修饰符：signed、unsigned、short、long)`

类型转换：静态转换、动态转换、常量转换、重新解释转换

存储类定义 C++ 程序中变量/函数的范围（可见性）和生命周期。这些说明符放置在它们所修饰的类型之前。下面列出 C++ 程序中可用的存储类：

- `auto`
- `register`
- `static`
- `extern`
- `mutable`
- `thread_local (C++11)`

从 C++ 17 开始，`auto` 关键字不再是 C++ 存储类说明符，且 `register` 关键字被弃用。

自增和自减的前缀形式与后缀形式之间有一点不同。如果使用前缀形式，则会在表达式计算之前完成自增或自减，如果使用后缀形式，则会在表达式计算之后完成自增或自减。

`A = 00111100 (~A)` 将得到 `-61`，即为 `1100 0011`，一个有符号二进制数的补码形式。

下表列出了 C++ 支持的其他一些重要的运算符。

| 运算符 | 描述 |
| --- | --- |
| sizeof | https://www.runoob.com/cplusplus/cpp-sizeof-operator.html返回变量的大小。例如，sizeof(a) 将返回 4，其中 a 是整数。 |
| Condition ? X : Y | https://www.runoob.com/cplusplus/cpp-conditional-operator.html。如果 Condition 为真 ? 则值为 X : 否则值为 Y。 |
| , | https://www.runoob.com/cplusplus/cpp-comma-operator.html会顺序执行一系列运算。整个逗号表达式的值是以逗号分隔的列表中的最后一个表达式的值。 |
| .（点）和 ->（箭头） | https://www.runoob.com/cplusplus/cpp-member-operators.html用于引用类、结构和共用体的成员。 |
| Cast | https://www.runoob.com/cplusplus/cpp-casting-operators.html把一种数据类型转换为另一种数据类型。例如，int(2.2000) 将返回 2。 |
| & | https://www.runoob.com/cplusplus/cpp-pointer-operators.html 返回变量的地址。例如 &a; 将给出变量的实际地址。 |
| * | https://www.runoob.com/cplusplus/cpp-pointer-operators.html 指向一个变量。例如，*var; 将指向变量 var。 |

**C++ 中的运算符优先级**

**循环**：`while、for、do…while、嵌套循环`

**判断**：`if、if…else、嵌套if、switch、嵌套switch、?:`

**函数参数：**如果函数要使用参数，则必须声明接受参数值的变量。这些变量称为函数的**形式参数**。

形式参数就像函数内的其他局部变量，在进入函数时被创建，退出函数时被销毁。

当调用函数时，有三种向函数传递参数的方式：

| 调用类型 | 描述 |
| --- | --- |
| https://www.runoob.com/cplusplus/cpp-function-call-by-value.html | 该方法把参数的实际值赋值给函数的形式参数。在这种情况下，修改函数内的形式参数对实际参数没有影响。 |
| https://www.runoob.com/cplusplus/cpp-function-call-by-pointer.html | 该方法把参数的地址赋值给形式参数。在函数内，该地址用于访问调用中要用到的实际参数。这意味着，修改形式参数会影响实际参数。 |
| https://www.runoob.com/cplusplus/cpp-function-call-by-reference.html | 该方法把参数的引用赋值给形式参数。在函数内，该引用用于访问调用中要用到的实际参数。这意味着，修改形式参数会影响实际参数。 |

默认情况下，C++ 使用**传值调用**来传递参数。一般来说，这意味着函数内的代码不能改变用于调用函数的参数。之前提到的实例，调用 max() 函数时，使用了相同的方法。

**数组**：（`type arrayName [ arraySize ];`）在 C++ 中，数组是非常重要的，我们需要了解更多有关数组的细节。下面列出了 C++ 程序员必须清楚的一些与数组相关的重要概念：

| 概念 | 描述 |
| --- | --- |
| https://www.runoob.com/cplusplus/cpp-multi-dimensional-arrays.html | C++ 支持多维数组。多维数组最简单的形式是二维数组。 |
| https://www.runoob.com/cplusplus/cpp-pointer-to-an-array.html | 您可以通过指定不带索引的数组名称来生成一个指向数组中第一个元素的指针。 |
| https://www.runoob.com/cplusplus/cpp-passing-arrays-to-functions.html | 您可以通过指定不带索引的数组名称来给函数传递一个指向数组的指针。 |
| https://www.runoob.com/cplusplus/cpp-return-arrays-from-function.html | C++ 允许从函数返回数组。 |

**字符串**C++ 中有大量的函数用来操作以 null 结尾的字符串:

| 序号 | 函数 & 目的 |
| --- | --- |
| 1 | strcpy(s1, s2);复制字符串 s2 到字符串 s1。 |
| 2 | strcat(s1, s2);连接字符串 s2 到字符串 s1 的末尾。连接字符串也可以用 + 号，例如:

string str1 = "runoob";
string str2 = "google";
string str = str1 + str2; |
| 3 | strlen(s1);返回字符串 s1 的长度。 |
| 4 | strcmp(s1, s2);如果 s1 和 s2 是相同的，则返回 0；如果 s1<s2 则返回值小于 0；如果 s1>s2 则返回值大于 0。 |
| 5 | strchr(s1, ch);返回一个指针，指向字符串 s1 中字符 ch 的第一次出现的位置。 |
| 6 | strstr(s1, s2);返回一个指针，指向字符串 s1 中字符串 s2 的第一次出现的位置。 |

**指针**是一个变量，其值为另一个变量的地址，即，内存位置的直接地址。就像其他变量或常量一样，您必须在使用指针存储其他变量地址之前，对其进行声明。在 C++ 中，有很多指针相关的概念，这些概念都很简单，但是都很重要。下面列出了 C++ 程序员必须清楚的一些与指针相关的重要概念：

| 概念 | 描述 |
| --- | --- |
| https://www.runoob.com/cplusplus/cpp-null-pointers.html | C++ 支持空指针。NULL 指针是一个定义在标准库中的值为零的常量。 |
| https://www.runoob.com/cplusplus/cpp-pointer-arithmetic.html | 可以对指针进行四种算术运算：++、--、+、- |
| https://www.runoob.com/cplusplus/cpp-pointers-vs-arrays.html | 指针和数组之间有着密切的关系。 |
| https://www.runoob.com/cplusplus/cpp-array-of-pointers.html | 可以定义用来存储指针的数组。 |
| https://www.runoob.com/cplusplus/cpp-pointer-to-pointer.html | C++ 允许指向指针的指针。 |
| https://www.runoob.com/cplusplus/cpp-passing-pointers-to-functions.html | 通过引用或地址传递参数，使传递的参数在调用函数中被改变。 |
| https://www.runoob.com/cplusplus/cpp-return-pointer-from-functions.html | C++ 允许函数返回指针到局部变量、静态变量和动态内存分配。 |

**引用**变量是一个别名，也就是说，它是某个已存在变量的另一个名字。一旦把引用初始化为某个变量，就可以使用该引用名称或变量名称来指向变量。

引用通常用于函数参数列表和函数返回值。下面列出了 C++ 程序员必须清楚的两个与 C++ 引用相关的重要概念：

| 概念 | 描述 |
| --- | --- |
| https://www.runoob.com/cplusplus/passing-parameters-by-references.html | C++ 支持把引用作为参数传给函数，这比传一般的参数更安全。 |
| https://www.runoob.com/cplusplus/returning-values-by-reference.html | 可以从 C++ 函数中返回引用，就像返回其他数据类型一样。 |

**<iostream>**定义了 `**cin、cout、cerr、clog**` 对象，分别对应于标准输入流、标准输出流、非缓冲标准错误流和缓冲标准错误流。

使用 `cerr` 流来显示错误消息，而其他的日志消息则使用 `clog` 流来输出。

定义结构

为了定义结构，您必须使用 **struct** 语句。struct 语句定义了一个包含多个成员的新的数据类型，struct 语句的格式如下：

```cpp
struct type_name {
member_type1 member_name1;
member_type2 member_name2;
member_type3 member_name3;
.
.
} object_names;
```

### 三、面向对象

C++ 在 C 语言的基础上增加了面向对象编程，C++ 支持面向对象程序设计。类是 C++ 的核心特性，通常被称为用户定义的类型。

**类**用于指定对象的形式，是一种用户自定义的数据类型，它是一种封装了数据和函数的组合。类中的数据称为成员变量，函数称为成员函数。类可以被看作是一种模板，可以用来创建具有相同属性和行为的多个对象。

**类 & 对象**到目前为止，我们已经对 C++ 的类和对象有了基本的了解。下面的列表中还列出了其他一些 C++ 类和对象相关的概念，可以点击相应的链接进行学习。

| 概念 | 描述 |
| --- | --- |
| https://www.runoob.com/cplusplus/cpp-class-member-functions.html | 类的成员函数是指那些把定义和原型写在类定义内部的函数，就像类定义中的其他变量一样。 |
| https://www.runoob.com/cplusplus/cpp-class-access-modifiers.html | 类成员可以被定义为 public、private 或 protected。默认情况下是定义为 private。 |
| https://www.runoob.com/cplusplus/cpp-constructor-destructor.html | 类的构造函数是一种特殊的函数，在创建一个新的对象时调用。类的析构函数也是一种特殊的函数，在删除所创建的对象时调用。 |
| https://www.runoob.com/cplusplus/cpp-copy-constructor.html | 拷贝构造函数，是一种特殊的构造函数，它在创建对象时，是使用同一类中之前创建的对象来初始化新创建的对象。 |
| https://www.runoob.com/cplusplus/cpp-friend-functions.html | 友元函数可以访问类的 private 和 protected 成员。 |
| https://www.runoob.com/cplusplus/cpp-inline-functions.html | 通过内联函数，编译器试图在调用函数的地方扩展函数体中的代码。 |
| https://www.runoob.com/cplusplus/cpp-this-pointer.html | 每个对象都有一个特殊的指针 this，它指向对象本身。 |
| https://www.runoob.com/cplusplus/cpp-pointer-to-class.html | 指向类的指针方式如同指向结构的指针。实际上，类可以看成是一个带有函数的结构。 |
| https://www.runoob.com/cplusplus/cpp-static-members.html | 类的数据成员和函数成员都可以被声明为静态的。 |

面向对象程序设计中最重要的一个概念是**继承**。继承允许我们依据另一个类来定义一个类，这使得创建和维护一个应用程序变得更容易。这样做，也达到了重用代码功能和提高执行效率的效果。

当创建一个类时，您不需要重新编写新的数据成员和成员函数，只需指定新建的类继承了一个已有的类的成员即可。这个已有的类称为**基类**，新建的类称为**派生类**。

**多继承**即一个子类可以有多个父类，它继承了多个父类的特性。

C++ 类可以从多个类继承成员，语法如下：

```cpp
class <派生类名>:<继承方式1><基类名1>,<继承方式2><基类名2>,…
{
<派生类类体>
};
```

C++ 允许在同一作用域中的某个**函数**和**运算符**指定多个定义，分别称为**函数重载**和**运算符重载**。

重载声明是指一个与之前已经在该作用域内声明过的函数或方法具有相同名称的声明，但是它们的参数列表和定义（实现）不相同。

**多态**按字面的意思就是多种形态。当类之间存在层次结构，并且类之间是通过继承关联时，就会用到多态。C++ 多态意味着调用成员函数时，会根据调用函数的对象的类型来执行不同的函数。

**虚函数** 是在基类中使用关键字 **`virtual`** 声明的函数。在派生类中重新定义基类中定义的虚函数时，会告诉编译器不要静态链接到该函数。

我们想要的是在程序中任意点可以根据所调用的对象类型来选择调用的函数，这种操作被称为**动态链接**，或**后期绑定**。

您可能想要在基类中定义虚函数，以便在派生类中重新定义该函数更好地适用于对象，但是您在基类中又不能对虚函数给出有意义的实现，这个时候就会用到**纯虚函数**。（`= 0` 告诉编译器，函数没有主体）

**数据抽象**是指，只向外界提供关键信息，并隐藏其后台的实现细节，即只表现必要的信息而不呈现细节。数据抽象有两个重要的优势：

- 类的内部受到保护，不会因无意的用户级错误导致对象状态受损。
- 类实现可能随着时间的推移而发生变化，以便应对不断变化的需求，或者应对那些要求不改变用户级代码的错误报告。

如果只在类的私有部分定义数据成员，编写该类的作者就可以随意更改数据。如果实现发生改变，则只需要检查类的代码，看看这个改变会导致哪些影响。如果数据是公有的，则任何直接访问旧表示形式的数据成员的函数都可能受到影响。

**数据封装**是一种把数据和操作数据的函数捆绑在一起的机制，**数据抽象**是一种仅向用户暴露接口而把具体的实现细节隐藏起来的机制。

C++ 通过创建**类**来支持封装和数据隐藏（`public、protected、private`）

**接口**描述了类的行为和功能，而不需要完成类的特定实现。

C++ 接口是使用**抽象类**来实现的，抽象类与数据抽象互不混淆，数据抽象是一个把实现细节与相关的数据分离开的概念。

如果类中至少有一个函数被声明为纯虚函数，则这个类就是抽象类。纯虚函数是通过在声明中使用 "= 0" 来指定的

定义一个函数为虚函数，不代表函数为不被实现的函数。

定义他为虚函数是为了允许用基类的指针来调用子类的这个函数。

定义一个函数为纯虚函数，才代表函数没有被实现。

定义纯虚函数是为了实现一个接口，起到一个规范的作用，规范继承这个类的程序员必须实现这个函数。

### 四、高级教程

**C++文件与流**`<fstream>`

在 C++ 编程中，我们使用流提取运算符（ >> ）从文件读取信息，就像使用该运算符从键盘输入信息一样。唯一不同的是，在这里您使用的是 `**ifstream**` 或 `**fstream**` 对象，而不是 **`cin`** 对象。

```cpp
void open(const char *filename, ios::openmode mode);

// 文件读写
write:outfile << data << endl;
read:infile >> data;

// 定位到 fileObject 的第 n 个字节（假设是 ios::beg）
fileObject.seekg( n );

// 把文件的读指针从 fileObject 当前位置向后移 n 个字节
fileObject.seekg( n, ios::cur );

// 把文件的读指针从 fileObject 末尾往回移 n 个字节
fileObject.seekg( n, ios::end );

// 定位到 fileObject 的末尾
fileObject.seekg( 0, ios::end );
```

**C++异常处理**`<expection>`

异常提供了一种转移程序控制权的方式。C++ 异常处理涉及到三个关键字：**`try、catch、throw`**

- **throw:** 当问题出现时，程序会抛出一个异常。这是通过使用 **throw** 关键字来完成的。
- **catch:** 在您想要处理问题的地方，通过异常处理程序捕获异常。**catch** 关键字用于捕获异常。
- **try:** **try** 块中的代码标识将被激活的特定异常。它后面通常跟着一个或多个 catch 块。

**C++动态内存：** 程序中的内存分为两个部分：

- **栈**在函数内部声明的所有变量都将占用栈内存。
- **堆**这是程序中未使用的内存，在程序运行时可用于动态分配内存。

在 C++ 中，您可以使用特殊的运算符为给定类型的变量在运行时分配堆内的内存，这会返回所分配的空间地址。这种运算符即 **new** 运算符。`new data-type;`

如果您不再需要动态分配的内存空间，可以使用 **delete** 运算符，删除之前由 new 运算符分配的内存。`delete obj;`

数组的动态内存分配（一维、二维、三维）

```cpp
一维数组
// 动态分配,数组长度为 m
int *array=new int [m];
//释放内存
delete [] array;

二维数组

int **array;
// 假定数组第一维长度为 m， 第二维长度为 n
// 动态分配空间
array = new int *[m];
for( int i=0; i<m; i++ )
{
    array[i] = new int [n];
}
//释放
for( int i=0; i<m; i++ )
{
    delete [] array[i];
}
delete [] array;

三维数组

int ***array;
// 假定数组第一维为 m， 第二维为 n， 第三维为h
// 动态分配空间
array = new int **[m];
for( int i=0; i<m; i++ )
{
array[i] = new int *[n];
for( int j=0; j<n; j++ )
{
array[i][j] = new int [h];
}
}
//释放
for( int i=0; i<m; i++ )
{
for( int j=0; j<n; j++ )
{
delete[] array[i][j];
}
delete[] array[i];
}
delete[] array;
```

对象的动态内存分配

```cpp
#include <iostream>
using namespace std;
class Box
{
public:
Box() {
cout << "调用构造函数！" <<endl;
}
~Box() {
cout << "调用析构函数！" <<endl;
}
};

int main( )
{
Box* myBoxArray = new Box[4];`

delete [] myBoxArray; // 删除数组
return 0;
}
```

**C++模板**：模板是泛型编程的基础，泛型编程即以一种独立于任何特定类型的方式编写代码。

模板是创建泛型类或函数的蓝图或公式。库容器，比如迭代器和算法，都是泛型编程的例子，它们都使用了模板的概念。

每个容器都有一个单一的定义，比如 **向量**，我们可以定义许多不同类型的向量，比如 **vector <int>** 或 **vector <string>**。

模板函数定义的一般形式如下所示：

```cpp
template <typename type> ret-type func-name(parameter list)
{
// 函数的主体
}
```

正如我们定义函数模板一样，我们也可以定义类模板。泛型类声明的一般形式如下所示：

```cpp
template <class type> class class-name {
.
.
.
}
```

**C++预处理器**：预处理器是一些指令，指示编译器在实际编译之前所需完成的预处理。

C++ 还支持很多预处理指令，比如 `#include、#define、#if、#else、#line` 等

C++ 提供了下表所示的一些预定义宏：

| 宏 | 描述 |
| --- | --- |
| __LINE__ | 这会在程序编译时包含当前行号。 |
| __FILE__ | 这会在程序编译时包含当前文件名。 |
| __DATE__ | 这会包含一个形式为 month/day/year 的字符串，它表示把源文件转换为目标代码的日期。 |
| __TIME__ | 这会包含一个形式为 hour:minute:second 的字符串，它表示程序被编译的时间。 |

**C++信号处理**信号是由操作系统传给进程的中断，会提早终止一个程序。在 UNIX、LINUX、Mac OS X 或 Windows 系统上，可以通过按 Ctrl+C 产生中断。

有些信号不能被程序捕获，但是下表所列信号可以在程序中捕获，并可以基于信号采取适当的动作。这些信号是定义在 C++ 头文件 `<csignal>` 中。

**C++多线程**多线程是多任务处理的一种特殊形式，多任务处理允许让电脑同时运行两个或两个以上的程序。一般情况下，两种类型的多任务处理：**基于进程和基于线程**。

- 基于进程的多任务处理是程序的并发执行。
- 基于线程的多任务处理是同一程序的片段的并发执行。

多线程程序包含可以同时运行的两个或多个部分。这样的程序中的每个部分称为一个线程，每个线程定义了一个单独的执行路径。

[C++ 多线程](https://www.runoob.com/cplusplus/cpp-multithreading.html)

**C++ Web编程**

[C++ Web 编程](https://www.runoob.com/cplusplus/cpp-web-programming.html)

## **二、进阶阶段**

*在进阶阶段，你已经对 C++ 有一定的认知了。*

*这个时候我们可以深入学习 C++ 标准模板库（STL）、设计模式、数据结构基础以及 UI 界面开发、数据库开发等高级技能。*

### 1、C++标准库

[STL教程：C++ STL快速入门（非常详细） (biancheng.net)](http://c.biancheng.net/stl/)

**C++ 标准库**是一组预定义的函数、类和对象，为 C++ 程序提供了广泛的功能和工具。它分为两个主要部分：**标准函数库和标准模板库**。

1. 标准函数库（Standard Library Functions）：标准函数库提供了大量的函数，涵盖了字符串处理、数学运算、输入输出、日期和时间、文件操作、动态内存管理等方面的功能。其中包括 `<iostream>、<string>、<cmath>、<ctime>、<fstream>` 等头文件。
    - `<iostream>` 提供了输入输出流操作，如 `std::cout、std::cin`
    - `<string>` 包含字符串处理函数和类，如 `std::string、std::getline`
    - `<cmath>` 提供了数学函数，如 `std::sqrt、std::sin`
    - `<ctime>` 提供了日期和时间操作函数，如 `std::time、std::strftime`
    - `<fstream>` 提供了文件操作函数和类，如 `std::ifstream、std::ofstream`
2. 标准模板库（Standard Template Library，STL）：标准模板库是 C++ 的一个重要组成部分，提供了各种容器、算法和迭代器等模板类。它包括 `<vector>、<list>、<map>、<algorithm>` 等头文件。
    - `<vector>` 提供了动态数组容器，支持快速的随机访问。
    - `<list>` 实现了双向链表容器，支持高效的插入和删除操作。
    - `<map>` 提供了关联数组容器，以键值对的形式存储数据。
    - `<algorithm>` 包含了一系列常用算法，如排序、查找、变换等。

**标准模板库 STL**是 C++ 标准库的一部分，不需要单独安装，只需要`#include` 头文件。C++ 对模板（Template）支持得很好，STL 就是借助模板把常用的数据结构及其算法都实现了一遍，并且做到了**数据结构和算法的分离**。

C++ 语言的核心优势之一就是便于软件的复用。

C++ 语言有两个方面体现了复用：

- 面向对象的继承和多态机制
- 通过模板的概念实现了对泛型程序设计的支持

下面给出**STL的组成**

| STL的组成 | 含义 |
| --- | --- |
| 容器 | 一些封装http://c.biancheng.net/data_structure/的模板类，例如 vector 向量容器、list 列表容器等。 |
| 算法 | STL 提供了非常多（大约 100 个）的数据结构算法，它们都被设计成一个个的模板函数，这些算法在 std 命名空间中定义，其中大部分算法都包含在头文件 <algorithm> 中，少部分位于头文件 <numeric> 中。 |
| 迭代器 | 在 http://c.biancheng.net/cplus/ STL 中，对容器中数据的读和写，是通过迭代器完成的，扮演着容器和算法之间的胶合剂。 |
| 函数对象 | 如果一个类将 () 运算符重载为成员函数，这个类就称为函数对象类，这个类的对象就是函数对象（又称仿函数）。 |
| 适配器 | 可以使一个类的接口（模板的参数）适配成用户指定的形式，从而让原本不能在一起工作的两个类工作在一起。值得一提的是，容器、迭代器和函数都有适配器。 |
| 内存分配器 | 为容器类模板提供自定义的内存申请和释放功能，由于往往只有高级用户才有改变内存分配策略的需求，因此内存分配器对于一般用户来说，并不常用。 |

下面给出C++标准中SLT的13个头文件

`<iterator> 
<functional> <vector> <deque> 
<list> <queue> <stack> <set> <map> <algorithm> <numeric> <memory> <utility>` 

下面记录一下需要掌握的**常用类**

- `cmath`
- `string`
- `ctime`
    
    

下面给出C++**官方手册**

[C++ Standard Library headers - cppreference.com](https://en.cppreference.com/w/cpp/header)


## 三、应用阶段

*其实编程语言就是要多练，怎么多练，就是代码量。自己多写，然后多观摩别人的项目，看人家的写法，模仿项目，学习其中的思想，一点点的积累，一步步形成自己的东西，厚积而薄发，慢慢你就会发现你也可以了。*

下面记录一些实战项目。