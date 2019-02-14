# 搜索引擎

## <a href="https://github.com/wildhunt-unique/JavaNote/blob/master/README.md">返回概览</a>

## ElasticSearch

-----
### 概述
ElasticSearch是一个搜索引擎，建立在全文搜索引擎库Lucene之上。Lucene非常复杂，ElasticSearch对其进行了封装，提供了一套RESTful的API

-----
### 特点
1. 一个分布式的实时文档存储，每个字段 可以被索引与搜索
1. 一个分布式实时分析搜索引擎
1. 支持水平扩展，支持结构化或者非结构化的数据

-----
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

-----
### 轶事
> <br>许多年前，一个刚结婚的名叫 Shay Banon 的失业开发者，跟着他的妻子去了伦敦，他的妻子在那里学习厨师。 在寻找一个赚钱的工作的时候，为了给他的妻子做一个食谱搜索引擎，他开始使用 Lucene 的一个早期版本。<br><br/> 直接使用 Lucene 是很难的，因此 Shay 开始做一个抽象层，Java 开发者使用它可以很简单的给他们的程序添加搜索功能。 他发布了他的第一个开源项目 Compass。<br/><br>后来 Shay 获得了一份工作，主要是高性能，分布式环境下的内存数据网格。这个对于高性能，实时，分布式搜索引擎的需求尤为突出， 他决定重写 Compass，把它变为一个独立的服务并取名 Elasticsearch。<br><br> 第一个公开版本在2010年2月发布，从此以后，Elasticsearch 已经成为了 Github 上最活跃的项目之一，他拥有超过300名 contributors(目前736名 contributors )。 一家公司已经开始围绕 Elasticsearch 提供商业服务，并开发新的特性，但是，Elasticsearch 将永远开源并对所有人可用。<br><br> 据说，Shay 的妻子还在等着她的食谱搜索引擎…<br><br>

-----
### 安装与运行
ElasticSearch开箱即可使用，在官网上下载之后，在bin目录运行elasticSearch即可。

-----
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
新建index可以向ES发送一个put请求。请求格式为 `host:port/index` 。比如创建一个weather 的`index`。可以使用 `curl -X PUT 'localhost:9200/weather'` 。运行命令之后，会有如下response，即表示成功
<pre>
{
  "acknowledged":true,
  "shards_acknowledged":true
}
</pre>
response 是一个json 对象。其中acknowledged 字段表示此次操作是否成功

#### 删除index
删除`index` 可以发送delete 请求，格式和新建一样。只不过新建是 put 请求，删除是delete 请求。比如删除weather 这个index，可以使用`curl -X DELETE 'localhost:9200/weather'` 这个命令

#### 设置中文分词
新建`index` 的时候，需要制定分词的字段，凡是需要搜索的中文字段，都需要单独设置一下。

`curl -X PUT 'localhost:9200/accounts' -d 
{
  "mappings": {
    "person": {
      "properties": {
        "user": {
          "type": "text",
          "analyzer": "ik_max_word",
          "search_analyzer": "ik_max_word"
        },
        "title": {
          "type": "text",
          "analyzer": "ik_max_word",
          "search_analyzer": "ik_max_word"
        },
        "desc": {
          "type": "text",
          "analyzer": "ik_max_word",
          "search_analyzer": "ik_max_word"
        }
      }
    }
  }
}'`

命令中请的部分json对象如下
<pre>
{
  "mappings": {
    "person": {
      "properties": {
        "user": {
          "type": "text",
          "analyzer": "ik_max_word",
          "search_analyzer": "ik_max_word"
        },
        "title": {
          "type": "text",
          "analyzer": "ik_max_word",
          "search_analyzer": "ik_max_word"
        },
        "desc": {
          "type": "text",
          "analyzer": "ik_max_word",
          "search_analyzer": "ik_max_word"
        }
      }
    }
  }
}
</pre>
上面的命令中，新建了一个名为 account 的 `index` ，里面有一个名为 person 的`type` ，person 有三个字段，分别为 user ， title ， desc 

这三个字段类型都是文本，而且都是中文，需要设置分词。analyzer 是字段文本的分词器，search_analyzer 是搜索词的分词器。ik_max_word分词器是插件ik提供的，可以对文本进行最大数量的分词

#### 新增记录
向指定的index/type 发送put请求，就可以在index里，新增一条记录。比如向/account/person 新增记录，命令如下
<pre>
curl -X PUT 'localhost:9200/accounts/person/1' -d '
{
    "user":"张三",
    "title":"工程师",
    "desc":"数据库管理"
}
'
</pre>
运行命令之后，会返回如下格式的json
<pre>
{
	"_index": "accounts",
	"_type": "person",
	"_id": "1",
	"_version": 1,
	"result": "created",
	"_shards": {
		"total": 2,
		"successful": 1,
		"failed": 0
	},
	"created": true
}
</pre>

由于用的是put 请求，请求的url中，最后一项是id。若是使用post请求，则不指定id，id为随机字符串。

#### 查看记录
向 index/type/id 发送get 请求，即可按照id查看单条记录。如 `curl 'localhost:9200/accounts/person/1?pretty=true'` ，这个命令请求查看id 为1的person记录。返回的结果中，found 字段表示否查询成功
<pre>
{
	"_index": "accounts",
	"_type": "person",
	"_id": "1",
	"_version": 3,
	"found": true,
	"_source": {
		"user": "张三",
		"title": "工程师",
		"desc": "数据库管理"
	}
}
</pre>

## 参考资料
+ > http://www.ruanyifeng.com/blog/2017/08/elasticsearch.html 全文搜索引擎 Elasticsearch 

+ > https://www.elastic.co/guide/cn/elasticsearch/guide/current/index.html Elasticsearch: 权威指南