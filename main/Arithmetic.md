# 算法

## <a href="https://github.com/wildhunt-unique/JavaKnowledgePoint/blob/master/README.md">返回概览</a>

## 直接插入排序
### 思想
+ 直接插入排序的基本操作是将一个记录插入到已经排序好的有序表中，从而得到一个新的、记录数+1的有序表。


+ 当然，需要进行排序的数据不需要有序，可以先将第一个元素看成一个有序表。后面的元素，插入到前面的有序表中，就像扑克牌开始时，拿牌一样。
+ O{n^2}
### 代码
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/StraightInsertionSort.png)
## 二分插入排序
## 希尔插入排序
### 思想
+ 希尔排序是把记录按下标的一定增量分组，对每组使用直接插入排序算法排序；随着增量逐渐减少，每组包含的关键词越来越多，当增量减至1时，整个文件恰被分成一组，算法便终止。

+ 最坏：O{n^2} 最好：O{n^(1.3)}   
### 代码
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/ShellSort.png)
## 冒泡排序
### 思想
+ 冒泡排序的基本思想就是：从无序序列头部开始，进行两两比较，根据大小交换位置，直到最后将最大（小）的数据元素交换到了无序队列的队尾，从而成为有序序列的一部分；下一次继续这个过程，直到所有数据元素都排好序。

+ 算法的核心在于每次通过两两比较交换位置，选出剩余无序序列里最大（小）的数据元素放到队尾。

+ O{n^2}
### 代码
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/BubbleSort.png)
## 快速排序
### 思想
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/quickSort.gif)
### 代码
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/QuickSort_1.png)
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/QuickSort_2.png)
## 选择排序
### 思想
+ 首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。

+ 选择排序的主要优点与数据移动有关。如果某个元素位于正确的最终位置上，则它不会被移动。选择排序每次交换一对元素，它们当中至少有一个将被移到其最终位置上，因此对n个元素的表进行排序总共进行至多n+1次交换。在所有的完全依靠交换去移动元素的排序方法中，选择排序属于非常好的一种。
+ O{n^2}
### 代码
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/SimpleSelectSort.png)
## 堆排序
## 归并排序
