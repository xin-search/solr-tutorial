## Collections API
Collections API 用于创建、删除或重新加载collection

## 创建Collection
/admin/collections?action=CREATE&name=name

**name**   
collection的名字

**router.name**  
路由名称，有`implicit`和`compositeId`两种选择。  
使用`implicit`时，写索引需要指出具体的shard，否则文档不会自动路由到不同的shard里  
使用`compositeId`时，路由会对uniqueKey做hash处理,并根据collection的clusterstate决定哪个shard接收文档。  
使用implicit路由器时，该shards参数是必需的。使用compositeId路由器时，该numShards参数是必需的。

**numShards**  
指定collection里shard数量  

**shards**
以逗号分隔的分片名称列表，例如shard-x,shard-y,shard-z。当router.name是implicit时，这是一个必需的参数。  

**replicationFactor**  
指定集群里副本数量  

**router.field**  
如果指定这个参数，创建索引时会使用这个field进行hash否则会报错  

**createNodeSet**  
定义节点的名称集合，用于集合之间传播用，其实创建时不必提供，会自动创建，但是`新加节点(replica)要手动指定`的。

**nrtReplicas**
为此Collection中创建的NRT（近实时）副本的数量。这种副本维护一个事务日志，并在本地更新其索引。如果你想要所有的副本都是这种类型的，你可以直接使用replicationFactor。


示例
```shell
curl "http://localhost:8983/solr/admin/collections?action=CREATE&name=xin_suggest_v2&numShards=1&replicationFactor=2&wt=xml"
```
增加replica
```shell
curl "http://localhost:8983/solr/admin/collections?action=ADDREPLICA&collection=xin_suggest_v2&shard=shard1&node=192.168.1.188:8983_solr"
```
这里虽然成功增加了一个replica但是在集群的state.json里replicationFactor仍然为2

此处需要测试
## 修改集合属性
/admin/collections?action=MODIFYCOLLECTION&collection=collection-name&attribute-name=attribute-value&another-attribute-name=another-value

示例
```shell
curl "http://localhost:8983/solr/admin/collections?action=MODIFYCOLLECTION&collection=xin_suggest_v2&replicationFactor=3&wt=json"
```
改变这些属性信息只会改变zk里信息，不会更改collection的拓扑结构

## RELOAD: 重新加载 Collection
/admin/collections?action=RELOAD&name=name

示例
```shell
http://localhost:8983/solr/admin/collections?action=RELOAD&name=newCollection&wt=xml
```

## SPLITSHARD: 拆分 Shard
/admin/collections?action=SPLITSHARD&collection=name&shard=shardID

示例
```shell
curl "http://localhost:8983/solr/admin/collections?action=SPLITSHARD&collection=xin_suggest_v2&shard=shard1"
```






