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

### 思想
+ 堆排序是对简单选择排序的改进

+ 简单选择排序是从n个记录中找出一个最小的记录，需要比较n-1次。但是这样的操作并没有把每一趟的比较结果保存下来，在后一趟的比较中，有许多比较在前一趟已经做过了，但由于前一趟排序时未保存这些比较结果，所以后一趟排序时又重复执行了这些比较操作，因而记录的比较次数较多。

+ 堆是具有下列性质的完全二叉树：每个结点的值都大于或等于其左右孩子结点的值，称为大顶堆；或者每个结点的值都小于或等于其左右孩子结点的值，称为小顶堆。 
### 代码
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/heapsort_4.png)
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/heapsort_2.png)
![Image text](http://static.qtu404.com/imgLab/github/JavaNote/heapsort_3.png)
## 归并排序
