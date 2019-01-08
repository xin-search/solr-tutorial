## solr 副本类型
* NRT  
* TLOG  
* PULL  

### NRT副本
Leader shard会将更新的文档转发给NRT replica, NRT replica和Leader一样，在本地进行相应数据transaction log和索引的更新，这意味着副本和leader要进行一样的处理过程，文档分析、索引、以及索引合并，这其实有点多余而且代价很高

NRT副本在本地更新索引，维护本地transaction log  
NRT副本是默认的副本类型，这种类型副本可以成为leader
### TLOG副本
通过replication handler从leader复制二进制的segments到本地，只要重新打开索引新增量数据就会对查询生效；这样就不需要在本地更新索引，但仍需要维护本地的  transaction log  
因为不需要在本地进行索引更新和段合并，TLOG副本比NRT副本索引速度快很多  
副本主动轮询向leader拉取二进制数据  
TLOG副本可以成为leader 
### PULL副本  
pull副本只会轮询拉取leader的二进制数据，不会像TLOG副本一样维护transaction log，也不会在本地更新索引，所以这种类型的副本进行索引对查询影响较小，但是实时性最差。  
PULL副本不能成为leader 




