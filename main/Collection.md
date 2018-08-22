# Java集合类

+ ## <a href="https://github.com/wildhunt-unique/JavaKnowledgePoint/blob/master/README.md">返回概览</a>

+ ## 集合类概述
    + ### 集合框架的类图
        +  ![Image text](https://qtu404.oss-cn-beijing.aliyuncs.com/JavaPoint/20140628144205625%20.jpg?Expires=1534909409&OSSAccessKeyId=TMP.AQEOe8ugWWlhAk6WJB6RIAaU4sQM3WKYNSpfC6-jvItqkqlLjYFOjRiNoj_fADAtAhUA_JReOWZHA4vJ3hrYBwESSK-oCGYCFCInLm9Q8gjhzVb-v5DNClsSK6Lc&Signature=ZMqT6w3DrVwUMQF2ZTVrMmv%2F1FA%3D)

    + ### 集合类的分类
        + 从类图里看出，集合类大致分为两类： Collection 以及 Map。而一般来说，应该更加细致得分为三类：List、Set、Map

        + List接口表示一个列表，列表中的元素是可重复的，而且列表是有先后顺序的。此接口的用户可以对列表中每个元素的插入位置进行精确地控制。用户可以根据元素的整数索引（在列表中的位置）访问元素，并搜索列表中的元素。

        + Set接口表示一个集合，这里的集合表示数学概念上的集合，即内部的元素是不可重复的

        + Map接口表示一组键值对的集合，可以将键映射到值的对象。不能包含重复的键，每个键最多可以映射一个值。
 
+ ## List   

    + ### ArrayList
        + 概述：ArrayList是内部是以动态数组的形式来存储数据的、知道数组的可能会疑惑：数组不是定长的吗？这里的动态数组不是意味着去改变原有内部生成的数组的长度、而是保留原有数组的引用、将其指向新生成的数组对象、这样会造成数组的长度可变的假象。

        + ArrayList具有数组所具有的特性、通过索引支持随机访问、所以通过随机访问ArrayList中的元素效率非常高、但是执行插入、删除时效率比较地下。

    + ### LinkedList

    + ### Vector

+ ## Set

    + ### LinkedHashSet

    + ### TreeSet

+ ## Map

    + ### HashMap

    + ### Hashtable

+ ## 参考资料
    + > https://blog.csdn.net/crave_shy/article/details/17436773 java_集合体系之ArrayList详解、源码及示例——03
