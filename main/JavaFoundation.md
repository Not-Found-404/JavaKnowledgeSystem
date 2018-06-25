# Java基础

## <a href="https://github.com/wildhunt-unique/JavaKnowledgePoint/blob/master/README.md">返回概览</a>

+ 参考资料
    + > 深入理解Java虚拟机：JVM高级特性与最佳实践 / 周志明著 -2版- 

+ 多态（重载重写）

+ object方法

+ 类访问权限

+ sleep、notify、wait 联系、区别

+ String、stringbuffer、stringbuilder 联系、区别、源码

+ Volatile 原理、源码、与syn区别
    + 关键字volatile是JVM中最轻量的同步机制。volatile变量具有2种特性：
        + 保证变量的可见性。对一个volatile变量的读，总是能看到（任意线程）对这个volatile变量最后的写入，这个新值对于其他线程来说是立即可见的。
        + 屏蔽指令重排序：指令重排序是编译器和处理器为了高效对程序进行优化的手段，下文有详细的分析。

    + volatile语义并不能保证变量的原子性。对任意单个volatile变量的读/写具有原子性，但类似于i++、i–这种复合操作不具有原子性，因为自增运算包括读取i的值、i值增加1、重新赋值3步操作，并不具备原子性。

    + 由于volatile只能保证变量的可见性和屏蔽指令重排序，只有满足下面2条规则时，才能使用volatile来保证并发安全，否则就需要加锁（使用synchronized、lock或者java.util.concurrent中的Atomic原子类）来保证并发中的原子性。
        + 运算结果不存在数据依赖（重排序的数据依赖性），或者只有单一的线程修改变量的值（重排序的as-if-serial语义）
        + 变量不需要与其他的状态变量共同参与不变约束

    + 因为需要在本地代码中插入许多内存屏蔽指令在屏蔽特定条件下的重排序，volatile变量的写操作与读操作相比慢一些，但是其性能开销比锁低很多。
+ 线程间通信方式

+ 线程的各种状态
