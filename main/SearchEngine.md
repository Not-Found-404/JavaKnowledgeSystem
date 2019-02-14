# 搜索引擎

## <a href="https://github.com/wildhunt-unique/JavaNote/blob/master/README.md">返回概览</a>

## ElasticSearch

### 概述
ElasticSearch是一个搜索引擎，建立在全文搜索引擎库Lucene之上。Lucene非常复杂，ElasticSearch对其进行了封装，提供了一套RESTful的API,
### 特点
1. 一个分布式的实时文档存储，每个字段 可以被索引与搜索
1. 一个分布式实时分析搜索引擎
1. 支持水平扩展，支持结构化或者非结构化的数据

### 基本概念
#### Node
ElasticSearch 本质上是一个分布式数据库，允许多台服务器协同工作，每台服务器可以运行多个ES实例。单个ES节点称为`Node`，一组节点构成一个集群`cluster`

#### index
ES会检索所有字段，经过处理后，写入一个反向索引`Inverted Index`， 查找数据的时候，直接查找改索引。
ES的顶层管理单位就是`index` ，某种程度上来说，`index` 可以类比为数据库中的一个`database` 

#### document
`index` 里面的单条记录为 `document` 。一条条的`document` 组成 `index`。`document` 使用json表示，如下面这个例子
<pre>
{
    "name":"张三",
    "age":13,
    "sex":"female"
}
</pre>

#### type
`document` 可以进行分组，比如有一个     weather 的`index` ，weather可以按照城市进行分组，比如按照杭州、上海进行分组。或者按照天气进行分组。每种分组就是一个type


### 轶事
> <br>许多年前，一个刚结婚的名叫 Shay Banon 的失业开发者，跟着他的妻子去了伦敦，他的妻子在那里学习厨师。 在寻找一个赚钱的工作的时候，为了给他的妻子做一个食谱搜索引擎，他开始使用 Lucene 的一个早期版本。<br><br/> 直接使用 Lucene 是很难的，因此 Shay 开始做一个抽象层，Java 开发者使用它可以很简单的给他们的程序添加搜索功能。 他发布了他的第一个开源项目 Compass。<br/><br>后来 Shay 获得了一份工作，主要是高性能，分布式环境下的内存数据网格。这个对于高性能，实时，分布式搜索引擎的需求尤为突出， 他决定重写 Compass，把它变为一个独立的服务并取名 Elasticsearch。<br><br> 第一个公开版本在2010年2月发布，从此以后，Elasticsearch 已经成为了 Github 上最活跃的项目之一，他拥有超过300名 contributors(目前736名 contributors )。 一家公司已经开始围绕 Elasticsearch 提供商业服务，并开发新的特性，但是，Elasticsearch 将永远开源并对所有人可用。<br><br> 据说，Shay 的妻子还在等着她的食谱搜索引擎…<br><br>

### 安装与运行
ElasticSearch开箱即可使用，在官网上下载之后，在bin目录运行elasticSearch即可。

### RESTFul的交互
#### 检测Elastic是否启动成功
运行命令 `curl 'http://localhost:9200` ，或者浏览器地址输入 `localhost:9200`。如果有类似以下响应，则表示成功。
<pre>
{
  "name" : "SnM5iev",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "bvIvqYf0R_qBFy1YXzvBmA",
  "version" : {
    "number" : "5.5.0",
    "build_hash" : "260387d",
    "build_date" : "2017-06-30T23:16:05.735Z",
    "build_snapshot" : false,
    "lucene_version" : "6.6.0"
  },
  "tagline" : "You Know, for Search"
}
</pre>
到这步，意味着已经启动了一个节点，可以与之进行交互。

#### 新建index


