## bin/solr脚本介绍
### 获得帮助
```
./bin/solr -help
```
### 启动/停止/重启/查看状态
```
./bin/solr start
./bin/solr stop
./bin/solr restart
./bin/solr status
```

### 启动参数

#### -d dir
定义服务器目录，默认为server

#### -m memory 
定义JVM堆的大小（solr占用的内存）

#### -p port 
定义Solr端口

#### -s dir
定义solr.solr.home，solr将会在这个目录下创建core目录，默认值是server/solr

#### -c 
在 SolrCloud 模式下启动

### 停止参数

#### -all
停止所有正在运行的具有有效PID的Solr实例

#### -p port
停止在指定端口上运行的Solr

