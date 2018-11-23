## 基本概念
### Solr instance（solr实例）
instance是一个通用概念，这里指运行在一个JVM上的Solr Server, Solr Server由Solr.war和web容器组成的，默认web容器是Jetty。多个Solr instance可以共用一个Solr Server，一个Solr instance里可以包含多个core

### core
由index及其依赖的文件组成，可提供完整的搜索服务

### Solr home
用来存放Solr core的目录

### Node
SolrCloud模式下一个Solr instance叫做Node

### Collection
分布式环境下，集群中一个完整的逻辑索引的总称。

### shard
在分布式环境下，Collection分成多个partition，每个partition叫做shard。shard也是逻辑上的概念。

### Replica
shard的一个物理拷贝

### Leader
每个shard有多个replica,有一个被选为leader。

### Zookeeper 
Apache开源的分布式协调服务，Solr用ZK来管理集群和选举Leader
