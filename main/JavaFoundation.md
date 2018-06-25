# Java基础

## <a href="https://github.com/wildhunt-unique/JavaKnowledgePoint/blob/master/README.md">返回概览</a>

+ Java内存模型
    + JMM(Java Memory Model)，Java虚拟机在执行Java程序的过程会把它所管理的内存划分为若干不同的区域。这些区域都有各自的用途，以及创建和销毁的时间。有的区域随着虚拟机的启动而存在，有的区域则依赖用户线程的启动和结束来创建
    + JMM运行时数据区如图所示
    + ![Image text](http://www.qtu404.com/imageLib/github/20180625095148.png)
    + Java运行时数据区分为以下几个部分
        + 线程共享的部分
            + 方法区
            + 堆

        + 线程私有的部分
            + 虚拟机栈
            + 本地方法栈
            + 程序计数器

    + 程序计算器(Program Counter Register)
        + 程序计数器是一块较小的线程私有的内存空间，可以看作是当前线程锁执行的字节码的行号指示器。字节码解释器工作时，就参考这个数值来选取下一条执行的指令，分支、循环、跳转、异常处理、线程回复都等基础功能都要需要依赖这个计数器来完成。

        + Java通过线程轮换并分配处理器执行时间来实现多线程。因此，在一个确定的时刻，一个处理器都只会执行一条线程的指令。为了在切换线程之后，各线程都能恢复到正确的执行位置，每个线程都要需要一个独立的计数器。各个线程的计数器都互不影响，独立存储。为“线程私有”的内存。

        +  如果线程正在执行的是一个Java方法，记录的是正在执行的虚拟机字节码指令的地址

        +  如果执行的是Native方法，计数器值为空（Undefined）

        +  程序计数器是唯一一个在Java虚拟机规范中没有规定任何OutOfMemoryError情况的区域

    + Java虚拟机栈(Java Virtaul Machine Stacks)
        + Java虚拟栈也是线程私有的内存。其生命周期与线程相同，虚拟栈描述的是**Java方法**执行的内存模型。每个方法在执行的时候，都会创建一个栈帧(Stack Frame)用于存储局部变量表、操作数栈、动态链接、方法出口等信息。每一个方法的调用、执行和结束，都对应着栈帧在虚拟机栈入栈、出栈的过程。

        + 在规范中，此区域规定了两种异常。
            + 如果线程请求栈的深度大于虚拟机所允许的深度，则会抛出StackOverflowError异常
            + 如果栈可以动态扩展，当时扩展时，没有申请到足够的内存，就会抛出 OutOfMemoryError异常

    + 本地方法栈(Native Method Stack)
        + 与Java虚拟机栈功能相同，不同的是，Java虚拟机栈为虚拟机执行Java方法(.class字节码)服务，而本地方法栈为Native方法服务。什么是Native方法，自行百度JNI。

        + 值得注意的是，我们默认使用的JVM —— SunHotSpot，直接把 本地方法栈 和 Java虚拟机栈合二为一。同样会抛出StackOverflowError异常和OutOfMemoryError异常
+ 多态（重载重写）

+ object方法

+ 类访问权限

+ sleep、notify、wait 联系、区别

+ String、stringbuffer、stringbuilder 联系、区别、源码

+ Volatile 原理、源码、与syn区别

+ 线程间通信方式

+ 线程的各种状态
