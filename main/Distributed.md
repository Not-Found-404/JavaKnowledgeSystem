# 分布式

## <a href="https://github.com/wildhunt-unique/JavaNote/blob/master/README.md">返回概览</a>

## zookeeper
### 简介
+ zookeeper是一个分布式的服务框架，用于解决分布式中一致性的数据管理问题，如: 统一命名服务、状态同步服务、集群管理、分布式应用配置项管理。什么是一致性问题，如参考资料1所示

+ zookeeper实际上是yahoo开发的，最初其作为研发Hadoop时的副产品。由于分布式系统中一致性处理较为困难，其他的分布式系统没有必要 费劲重复造轮子，故随后的分布式系统中大量应用了zookeeper，以至于zookeeper成为了各种分布式系统的基础组件。著名的hadoop、kafka、dubbo 都是基于zookeeper而构建。

### 数据模型

+ 为了能够解决一致性问题，zookeeper维护了一个类似于文件系统的基本结构。

+ 

## 参考资料

1. > https://mp.weixin.qq.com/s?__biz=MzI4MTY5NTk4Ng==&mid=2247489421&amp;idx=1&amp;sn=66cc057427b239c8246714882df03bd8&source=41#wechat_redirect 解决分布式系统的一致性问题，我们需要了解哪些理论？

1. > https://www.jianshu.com/p/50becf121c66 Zookeeper入门看这篇就够了

1. > http://www.importnew.com/24411.html zookeeper入门系列：概述
