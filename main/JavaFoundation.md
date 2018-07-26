# Java基础

+ ## <a href="https://github.com/wildhunt-unique/JavaKnowledgePoint/blob/master/README.md">返回概览</a>

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

        + 每当在Java应用程序的执行过程中多次调用同一个对象时， hashCode方法必须始终返回相同的整数，前提是对象中使用的信息没有被修改。

        + 如果根据 equals（Object）方法，两个对象是相等的，那么在这两个对象上调用 hashCode方法必须产生相同的整数结果。

        + 如果两个对象是不相等的，那么根据equals（object）方法，在这两个对象上调用hashCode方法时，必须产生不同的整数结果，理论上不强制那么做。然而，为不相等的对象产生不同的整数结果可能会提高哈希表的性能，所以应该这么做，即若根据equals判断两个对象不同，则两个对象的hashcode方法返回值应该不同。

    + ### `public boolean equals(Object obj)`详解
        + 指示其他某个对象是否与此对象“相等”

        + equals 方法在非空对象引用上实现相等关系：
            + 自反性：对于任何非空引用值 x，x.equals(x) 都应返回 true。
            + 对称性：对于任何非空引用值 x 和 y，当且仅当 y.equals(x) 返回 true 时，x.equals(y) 才应返回 true。
            + 传递性：对于任何非空引用值 x、y 和 z，如果 x.equals(y) 返回 true，并且 y.equals(z) 返回 true，那么 x.equals(z) 应返回 true。
            + 一致性：对于任何非空引用值 x 和 y，多次调用 x.equals(y) 始终返回 true 或始终返回 false，前提是对象上 equals 比较中所用的信息没有被修改。
            + 对于任何非空引用值 x，x.equals(null) 都应返回 false。
        + Object 类的 equals 方法实现对象上差别可能性最大的相等关系；即，对于任何非空引用值 x 和 y，当且仅当 x 和 y 引用同一个对象时，此方法才返回 true（x == y 具有值 true）。

        + 注意：当此方法被重写时，通常有必要重写 hashCode 方法，以维护 hashCode 方法的常规协定，该协定声明相等对象必须具有相等的哈希码。
    + ### `protected native Object clone()`详解
        + 创建并返回此对象的一个副本。对于任何对象 x
            + x.clone() != x
                + 为true

            + x.clone().getClass() == x.getClass()
                + 为true

            + x.clone().equals(x) 
                + 为true

        + Object 类的 clone 方法执行特定的复制操作。首先，如果此对象的类不能实现接口 Cloneable，则会抛出 CloneNotSupportedException。注意，所有的数组都被视为实现接口 Cloneable。否则，此方法会创建此对象的类的一个新实例，并像通过分配那样，严格使用此对象相应字段的内容初始化该对象的所有字段；这些字段的内容没有被自我复制。所以，此方法执行的是该对象的“浅表复制”，而不“深层复制”操作。

        + Object 类本身不实现接口 Cloneable，所以在类为 Object 的对象上调用 clone 方法将会导致在运行时抛出异常。
    + ### `public final native Class<?> getClass()`详解
        + 返回此 Object 的运行时类。返回的 Class 对象是由所表示类的 static synchronized 方法锁定的对象。

        + 实际结果类型是 Class<? extends |X|>，其中 |X| 表示清除表达式中的静态类型，该表达式调用 getClass。 
    + ### notify、wait将在后面的章节详解

+ ## 类访问权限
    +   
        | 修饰词 |本类 | 同包的类 |  子类  | 其他类 |
        | :-: | :-: | :-:    | :-: | :-: |
        | private | ✔   | ✖ | ✖| ✖|
        | friend(默认)  | ✔  |  ✔   |✖ | ✖|
        | protected  | ✔ |  ✔  | ✔ | ✖ |
        | public | ✔ | ✔  | ✔ |  ✔|

+ ## sleep、nofity、wait
    + ### sleep
        + `Thread.sleep(long millis)`

        + `sleeo()`方法是 Thread类的一个静态方法，作用是强制当前则能够在执行的线程休眠(暂停执行)，以减慢线程

        + 如果从操作系统的层面去描述，这个方法是将当前所在的线程挂起，比如`Thread.sleep(1000)`，即是表明当前线程在未来1000毫秒内都不会去参与CPU使用权限的竞争，不管当前线程优先级如何。也就说，即使当前线程优先级很高，调用此函数，线程也不会得到CPU资源，也就不会被执行。同时，也并不是说，过了1000ms之后，该线程必定执行，只是说继续参与到线程之间的CPU资源竞争中。线程是否执行，取决于其优先级(windos系统，类unix
        系统采用时间片轮转)。

        + `Thread.Sleep(0)`的作用是“触发操作系统立刻重新进行一次CPU竞争”

        + 线程休眠不会丢失当前线程获取的任何监视器或锁

    + ### wait
        + 对象调用`wait()`方法导致当前线程等待。可以无参，也可以是`wait(long timeout)`

        + 当前线程必须拥有此对象监视器。也就是说，此对象应该是一个临界资源。

        + `wait()`方法是Object的一个final、native方法。也就是说，此方法是一个本地方法，其次此方法不可以被重写。同时每个对象都可调用此方法。

        + 从操作系统来说，若有一个临界资源，那么在某一时刻内，临界资源只能被一个线程占用。该线程会对此临界资源加锁，之后，其他线程若要使用此临界资源，需要等待当前使用的线程释放锁。所有在等待锁的线程都在此临界资源的等待集中。那么如果某些类是临界资源，`wait()` 方法实际上是，将当前线程加入到此对象的等待集中，也就是说，即使当前此线程在占用此对象，也将释放锁，同时放弃此对象的所有同步要求，并且将自身挂起，并等待唤醒。

        + 由于 wait 方法将当前线程放入了对象的等待集中，所以它只能解除此对象的锁定；可以同步当前线程的任何其他对象在线程等待时仍处于锁定状态

        + 显而易见，只有当前线程拥有该对象的锁，才能有权利调用该对象的 `wait()`方法，否则会抛出IllegalMonitorStateException

    + ### notify
        + 相对应的，` notify()`方法用于唤醒在此对象监视器上等待的单个线程。如果所有线程都在此对象上等待，则会选择唤醒其中一个线程。选择是任意性的，并在对实现做出决定时发生。

        + 直到当前线程放弃此对象上的锁定，才能继续执行被唤醒的线程。也就是说，即使当前线程唤醒了对象上某一等待的线程，那么也必须等待当前线程结束同步操作并且释放锁，唤醒线程才能执行。但其实也不见得被唤醒的线程就能马上执行，被唤醒的线程将以常规方式与在该对象上主动同步的其他所有线程进行竞争。和上面进程被唤醒，竞争CPU资源差不多意思，毕竟CPU也是临界资源。

        + 当然，如果当前线程不是此对象锁的所有者，而强行调用对象的`notify()`方法，则抛出IllegalMonitorStateException异常

+ ## String、stringbuffer、stringbuilder （**重中之重**）
    + 联系
    + 区别
    + 源码

+ ## Volatile 原理、源码、与syn区别 （**重中之重**）
    + 关键字volatile是JVM中最轻量的同步机制。volatile变量具有2种特性：
        + 保证变量的可见性。对一个volatile变量的读，总是能看到（任意线程）对这个volatile变量最后的写入，这个新值对于其他线程来说是立即可见的。
        + 屏蔽指令重排序：指令重排序是编译器和处理器为了高效对程序进行优化的手段，下文有详细的分析。

    + volatile语义并不能保证变量的原子性。对任意单个volatile变量的读/写具有原子性，但类似于i++、i–这种复合操作不具有原子性，因为自增运算包括读取i的值、i值增加1、重新赋值3步操作，并不具备原子性。

    + 由于volatile只能保证变量的可见性和屏蔽指令重排序，只有满足下面2条规则时，才能使用volatile来保证并发安全，否则就需要加锁（使用synchronized、lock或者java.util.concurrent中的Atomic原子类）来保证并发中的原子性。
        + 运算结果不存在数据依赖（重排序的数据依赖性），或者只有单一的线程修改变量的值（重排序的as-if-serial语义）
        + 变量不需要与其他的状态变量共同参与不变约束

    + 因为需要在本地代码中插入许多内存屏蔽指令在屏蔽特定条件下的重排序，volatile变量的写操作与读操作相比慢一些，但是其性能开销比锁低很多。

+ ## 线程间通信方式 （**重中之重**）

+ ## 线程的各种状态

+ ## 引用资源
    + > http://tool.oschina.net/apidocs/apidoc?api=jdk-zh jdk中文API
    + > https://www.zhihu.com/question/30082151/answer/46688599 作者：Intopass，来源：知乎

    + > https://www.cnblogs.com/565261641-fzh/p/5756242.html java中Thread.sleep()函数使用