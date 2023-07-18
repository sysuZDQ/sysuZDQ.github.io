# Algorithm

## 资料

- [Hello 算法 (hello-algo.com)](https://www.hello-algo.com/) ：简单易懂的算法知识梳理，适合初学者与回顾复习的同学们使用
- [小浩算法 | 小浩算法 (geekxh.com)](https://www.geekxh.com/0.0.%E5%AD%A6%E4%B9%A0%E9%A1%BB%E7%9F%A5/01.html) ：算法刷题中基础且必备的类型汇总，适宜准备面试时刷一遍
- [牛客网在线编程_编程学习|练习题_数据结构|系统设计题库 (nowcoder.com)](https://www.nowcoder.com/exam/oj?page=1&tab=%E7%AE%97%E6%B3%95%E7%AF%87&topicId=295&fromPut=pc_kol_aaaxiu)

## 基础算法

### 排序

排序算法的动图演示

[十大经典排序算法（动图演示） - 一像素 - 博客园 (cnblogs.com)](https://www.cnblogs.com/onepixel/articles/7674659.html)

[11.1.   排序简介 - Hello 算法 (hello-algo.com)](https://www.hello-algo.com/chapter_sorting/intro_to_sort/)

C++和Python内置排序算法的实现原理

[C++ 中的sort()排序函数原理、用法看这一篇就够了_c++ sort原理_猿六凯的博客-CSDN博客](https://blog.csdn.net/u014339447/article/details/109017759)

[TimSort 一个几乎没人知道的排序算法 | 时间复杂度最快达到了o(n)_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1944y1E7as/?spm_id_from=autoNext&vd_source=16860f65fea90013288ea5a6ba1bba3a)

Python中的排序函数

[排序指南 — Python 3.11.2 文档](https://docs.python.org/zh-cn/3/howto/sorting.html)

Leetcode题单

## 数组

数组的题目常使用快慢指针、双指针、滑动窗口的方式来减少时间复杂度

## 分治法

总结一下一般实现的几个条件：

- **初始条件：left = 0, right = length-1**
- **终止：left > right**
- **向左查找：right = mid-1**
- **向右查找：left = mid +1**

[(107条消息) 关于二分查找的 left ＜= right 和 left ＜ right 的不同_SASAKI佐佐木的博客-CSDN博客](https://blog.csdn.net/weixin_44162334/article/details/120127776)

[(107条消息) 二分法的细节加细节 你真的应该搞懂！！！_二分法为什么要加一_M小马M的博客-CSDN博客](https://blog.csdn.net/xiao_jj_jj/article/details/106018702)

模板

```cpp
// 版本一
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size() - 1; // 定义target在左闭右闭的区间里，[left, right]
        while (left <= right) { // 当left==right，区间[left, right]依然有效，所以用 <=
            int middle = left + ((right - left) / 2);// 防止溢出 等同于(left + right)/2
            if (nums[middle] > target) {
                right = middle - 1; // target 在左区间，所以[left, middle - 1]
            } else if (nums[middle] < target) {
                left = middle + 1; // target 在右区间，所以[middle + 1, right]
            } else { // nums[middle] == target
                return middle; // 数组中找到目标值，直接返回下标
            }
        }
        // 未找到目标值
        return -1;
    }
};
```

学会如何变化区间

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled.png)

一百个人有一百个二分，不要妄图和别人写出一模一样的代码，这是没有意义的

有序数组的查找一般考虑二分

mid = left + (left + right)//2

[(106条消息) int mid = l + (r - l) / 2 防止溢出_int mid = l +(r-l)/2为什么不会溢出_lucky tiger的博客-CSDN博客](https://blog.csdn.net/weixin_42269817/article/details/105934567)

矩阵的二分

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%201.png)

不一定输入是有序数组才能用二分，要分析处理的对象

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%202.png)

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%203.png)

要会分析如何使用二分

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%204.png)

分治法（如归并排序）

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%205.png)

## 动态规划

官方的定义是**指把多阶段过程转化为一系列单阶段问题，利用各阶段之间的关系，逐个求解**。概念中的**各阶段之间的关系**，其实指的就是**状态转移方程**。很多人觉得DP难（下文统称动态规划为DP），根本原因是因为**DP跟一些固定形式的算法不同**（比如DFS、二分法、KMP），它没有实际的步骤规定第一步、第二步来做什么，所以准确来说，**DP其实是一种解决问题的思想。**

## 贪心法

求最值考虑使用贪心或者动态规划，当局部最优解可以推导最终得出全局最优解时，用贪心，剩下的情况用动态规划。

最长递增子序列

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%206.png)

调度问题

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%207.png)

左右遍历一遍，使用贪心才能得到正确答案

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%208.png)

## 链表系列

在链表的题目中，十道有九道会用到**哨兵节点。**哨兵节点，其实就是一个**附加在原链表最前面用来简化边界条件的附加节点，它的值域不存储任何东西，只是为了操作方便而引入。**

注意链表的指针更新之后能否找到相关结点

一般使用递归和迭代两种做法

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%209.png)

遇到寻找第k个的问题，可以使用快慢指针，使得只需要遍历一遍

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%2010.png)

环形链表题目一般都是使用双指针法解决的，例如寻找距离尾部第 `K` 个节点、寻找环入口、寻找公共尾部入口等

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%2011.png)

蓄水池算法

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%2012.png)

循环队列

![Untitled](Algorithm%20fb3a5efb67f44233a59a6cbe13536c3f/Untitled%2013.png)

## 字符串

字符串匹配算法：一般来讲，字符串匹配算法第一步，**都是把目标串和模式串对齐**
，不管是KMP，BM，SUNDAY都是这样。在把模式串和目标串对齐后，如果发现不匹配，那肯定需要移动模式串。问题是需要移动多少步。各字符串匹配算法之间的差别也来自于这个地方，对于KMP，是建立部分匹配表来计算。BM，是反向比较计算移动量。对于SUNDAY，就是找到模式串后的第一个字符。因为，无论模式串移动多少步，**模式串后的第一个字符都要参与下一次比较。**

[KMP（上篇） | 小浩算法 (geekxh.com)](https://www.geekxh.com/1.3.%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%B3%BB%E5%88%97/306.html#_01%E3%80%81%E5%9B%BE%E8%A7%A3%E5%88%86%E6%9E%90)

大数计算：因为定义的数据类型往往是有长度限制的，但是字符串是可以无限长的，因此可以用字符串模拟数字的运算

正则表达式：是处理字符串一个必备的算法

## Python内置实用函数

[Python filter() 函数 | 菜鸟教程 (runoob.com)](https://www.runoob.com/python/python-func-filter.html)

## 回溯法

适合排列组合等问题

## 滑动窗口

滑动窗口的实现很简单，但是如何优化在滑动窗口里面寻找解是一个需要考虑的问题，例如需要滑动窗口的最大值，需要用到一个双端队列来维护最大值，而不是每一次就使用max()

## 算法超时间和超空间问题

[(107条消息) 算法面试中时间限制与时间复杂度之间的关系_时间复杂度1s_algsup的博客-CSDN博客](https://blog.csdn.net/qq_43152052/article/details/112112038)

[(5 封私信 / 80 条消息) 算法题而论，一秒大约对应什么样的计算量？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/30182122)