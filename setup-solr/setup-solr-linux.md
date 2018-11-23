## 安装准备
1. java运行环境，1.8及以上版本
2. [Solr安装包](https://lucene.apache.org/solr/mirrors-solr-latest-redir.html)， tutorial基于Solr7.5版本编写
## Stand-Alone Server
1. Solr安装包下载后，解压之后即可使用
2. `./bin/solr start` 启动solr，通过浏览器访问[http://localhost:8983/solr)](http://localhost:8983/solr)可以看到Solr的管理界面
>  通过命令```./bin/solr -e dih```启用solr自带的dih示例,在Solr管理界面选择db这个core，执行full dataimport可以导入数据。

## Solr目录结构
* **bin/**  
 此目录中包含Solr服务控制脚本，上传文件脚本以及服务器参数配置脚本等。  
 **solr 和 solr.cmd**  
 这是Solr的控制脚本，在Linux下用bin/solr，在Windows下用bin/solr.cmd。这个脚本是启动和停止 Solr 的首选工具。您也可以在SolrCloud模式下创建collections或cores、配置身份验证以及配置文件。  
 **post**  
 Post Tool，它提供了用于发布内容到 Solr 的一个简单的命令行界面。  
 **solr.in.sh 和 solr.in.cmd**  
 这些分别是为 *nix 和 Windows 系统提供的属性文件。在这里配置了 Java、Jetty 和 Solr 的系统级属性。许多这些设置可以在使用bin/solr或者bin/solr.cmd时被覆盖，但这允许您在一个地方设置所有的属性。  
 **install_solr_services.sh**
 该脚本用于 *nix 系统以安装 Solr 作为服务。

* **contrib**  
  contrib目录包含Solr特定功能的第三方插件。 

* **dist**   
dist目录包含主要的 Solr发行jar 文件。

* **docs**  
 docs目录包含一个链接到在线的 Solr Javadocs。  
* **example**   
 example目录包括演示各种 Solr 功能的几种类型的示例。

* **licenses**   
 licenses目录包括 Solr 使用的第三方库的所有许可证。

* **server** 
server目录是 Solr 应用程序的核心所在。此目录中的 README 提供了详细的概述，以下是一些特点:  
  * Solr 的 Admin UI（server/solr-webapp）  
  * Jetty库（server/lib）  
  * 日志文件（server/logs）和日志配置（server/resources）
  * 示例配置（server/solr/configsets）

