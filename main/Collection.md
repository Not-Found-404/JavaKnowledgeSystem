# Java集合类

## <a href="https://github.com/wildhunt-unique/JavaNote/blob/master/README.md">返回概览</a>

## 集合类概述

### 集合框架的类图
+  ![Image text](http://www.qtu404.com/imageLib/github/20140628144205625%20.jpg)

### 集合类的分类
+ 从类图里看出，集合类大致分为两类： Collection 以及 Map。而一般来说，应该更加细致得分为三类：List、Set、Map

+ List接口表示一个列表，列表中的元素是可重复的，而且列表是有先后顺序的。此接口的用户可以对列表中每个元素的插入位置进行精确地控制。用户可以根据元素的整数索引（在列表中的位置）访问元素，并搜索列表中的元素。

+ Set接口表示一个集合，这里的集合表示数学概念上的集合，即内部的元素是不可重复的

+ Map接口表示一组键值对的集合，可以将键映射到值的对象。不能包含重复的键，每个键最多可以映射一个值。
 
## List   

### ArrayList
+ <a href="https://github.com/wildhunt-unique/JavaKnowledgeSystem/blob/master/jdk1.8/java/util/ArrayList.java">ArrayList源码</a>

+ 概述：ArrayList是内部是以动态数组的形式来存储数据的,这里的动态数组不是意味着去改变原有内部生成的数组的长度、而是保留原有数组的引用、将其指向新生成的数组对象、这样会造成数组的长度可变的假象。

+ ArrayList具有数组所具有的特性、通过索引支持随机访问、所以通过随机访问ArrayList中的元素效率非常高、但是执行插入、删除时效率比较地下。

+ ArrayList不是线程安全的

### LinkedList

### Vector

## Map

### HashMap
+ HashMap是数组+链表+红黑树（在链表长度超过8以后，就会转化成红黑树）

+ 根据键的hashCode值存储数据，大多数情况下可以直接定位到它的值，因而具有很快的访问速度，但遍历顺序却是不确定的。 HashMap最多只允许一条记录的键为null，允许多条记录的值为null。HashMap非线程安全，即任一时刻可以有多个线程同时写HashMap，可能会导致数据的不一致。如果需要满足线程安全，可以用 Collections的synchronizedMap方法使HashMap具有线程安全的能力，或者使用ConcurrentHashMap

+ HashMap的`put`方法
        ![Image text](http://www.qtu404.com/imageLib/github/58e67eae921e4b431782c07444af824e_r.jpg)

+ 扩容(resize)就是重新计算容量，向HashMap对象里不停的添加元素，而HashMap对象内部的数组无法装载更多的元素时，对象就需要扩大数组的长度，以便能装入更多的元素。当然Java里的数组是无法自动扩容的，方法是使用一个新的数组代替已有的容量小的数组，就像我们用一个小桶装水，如果想装更多的水，就得换大水桶。

### Hashtable
+ Hashtable是遗留类，很多映射的常用功能与HashMap类似，不同的是它承自Dictionary类，并且是线程安全的，任一时间只有一个线程能写Hashtable，并发性不如ConcurrentHashMap，因为ConcurrentHashMap引入了分段锁。Hashtable不建议在新代码中使用，不需要线程安全的场合可以用HashMap替换，需要线程安全的场合可以用ConcurrentHashMap替换


## Set
### LinkedHashSet
### TreeSet


## 参考资料
+ > https://blog.csdn.net/crave_shy/article/details/17436773 java_集合体系之ArrayList详解、源码及示例——03

+ > https://zhuanlan.zhihu.com/p/21673805
来源：知乎
作者：美团技术团队
