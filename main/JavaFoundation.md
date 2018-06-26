# Java基础

+ ## <a href="https://github.com/wildhunt-unique/JavaKnowledgePoint/blob/master/README.md">返回概览</a>

+ ## 引用资源
    + > 深入理解Java虚拟机：JVM高级特性与最佳实践 / 周志明著 -2版-
    + > https://www.zhihu.com/question/30082151/answer/46688599 作者：Intopass，来源：知乎
+ ## 多态
    + 重载(Overload)
        + 一个方法名，参数不同，这叫方法重载。
        + <pre> void foo(String str);//参数是String类型
           void foo(int number);//参数是int类型</pre>

    + 重写(Override)
        + 父类与子类有同样的方法名和参数，这叫方法重写。
        + <pre>  class Parent {
                void foo() {
                    System.out.println("Parent foo()");
                }
            }
            class Child extends Parent {
                @Override
                void foo() {//重写父类的方法
                    System.out.println("Child foo()");
                }
            }</pre>
    + 多态
        + 父类引用指向子类对象，调用方法时会调用子类的实现，而不是父类的实现，这叫多态。
        + <pre>  Parent instance = new Child();
            instance.foo(); //==> Child foo()</pre>

+ ## Object类
    + ### <a href="https://github.com/wildhunt-unique/JavaKnowledgePoint/blob/master/jdk1.8/java/lang/Object.java">Object.java源码</a>

    + ### 概览
        + Object类是Java中所有类的父类。即使定义一个类时，没有显式声明继承自任何类，都默认继承自Object，。因此，所有类都继承了Object的所有方法。

    + ### Object有以下几个方法
        + `public final native Class<?> getClass()`
            + 返回此 Object 的运行时类，注意是运行时

        + `public native int hashCode()`
            + 返回该对象的哈希码值

        + `public boolean equals(Object obj)`
            + 指示其他某个对象是否与此对象“相等”

        + `protected native Object clone()`
            + 创建并返回此对象的一个副本。此副本是深克隆
        + `public String toString()`
            + 返回该对象的字符串表示

        + `public final native void notify()`
            + 唤醒在此对象监视器上等待的单个线程

        + `public final native void notifyAll()`
            + 唤醒在此对象监视器上等待的所有线程

        + `public final void wait()`
            + 在其他线程调用此对象的 `notify()` 方法或 `notifyAll()` 方法，或者超过指定的时间量前，导致当前线程等待

        + `protected void finalize()`
            + 当垃圾回收器确定不存在对该对象的更多引用时，由对象的垃圾回收器调用此方法

    + ### `public native int hashCode()`详解
        + 返回对象的hashCode值，支持此方法是为了提高哈希表性能

        + 每当在Java应用程序的执行过程中多次调用同一个对象时， hashCode方法必须始终返回相同的整数，前提是对象中使用的信息没有被修改从一个应用程序的执行到同一个应用程序的另一个执行，这个整数不需要保持一致。

        + 如果根据 equals（Object）方法，两个对象是相等的，那么在这两个对象上调用 hashCode方法必须产生相同的整数结果。

        + 如果两个对象是不相等的，那么根据equals（object）方法，在这两个对象上调用hashCode方法时，必须产生不同的整数结果，理论上不强制那么做。然而，为不相等的对象产生不同的整数结果可能会提高哈希表的性能，所以应该这么做，即若根据equals判断两个对象不同，则两个对象的hashcode方法返回值应该不同。

    + ### `public boolean equals(Object obj)`详解

    + ### `public boolean equals(Object obj)`详解

    + ### sleep、notify、wait将在后面的章节详解
+ ## 类访问权限

+ ## sleep、notify、wait
    + 联系
    + 区别

+ ## String、stringbuffer、stringbuilder 
    + 联系
    + 区别
    + 源码

+ ## Volatile 原理、源码、与syn区别
    + 关键字volatile是JVM中最轻量的同步机制。volatile变量具有2种特性：
        + 保证变量的可见性。对一个volatile变量的读，总是能看到（任意线程）对这个volatile变量最后的写入，这个新值对于其他线程来说是立即可见的。
        + 屏蔽指令重排序：指令重排序是编译器和处理器为了高效对程序进行优化的手段，下文有详细的分析。

    + volatile语义并不能保证变量的原子性。对任意单个volatile变量的读/写具有原子性，但类似于i++、i–这种复合操作不具有原子性，因为自增运算包括读取i的值、i值增加1、重新赋值3步操作，并不具备原子性。

    + 由于volatile只能保证变量的可见性和屏蔽指令重排序，只有满足下面2条规则时，才能使用volatile来保证并发安全，否则就需要加锁（使用synchronized、lock或者java.util.concurrent中的Atomic原子类）来保证并发中的原子性。
        + 运算结果不存在数据依赖（重排序的数据依赖性），或者只有单一的线程修改变量的值（重排序的as-if-serial语义）
        + 变量不需要与其他的状态变量共同参与不变约束

    + 因为需要在本地代码中插入许多内存屏蔽指令在屏蔽特定条件下的重排序，volatile变量的写操作与读操作相比慢一些，但是其性能开销比锁低很多。

+ ## 线程间通信方式

+ ## 线程的各种状态
