## Data Import Handler (DIH) concept
通过Solr的DIH机制可以把数据源的数据导出到Solr里

### Datasource
描述了获取数据的源，如何连接它

### Entity
生成一系列文档；如果数据源是数据库，Entity里定义sql语句来查询数据库里的数据组成一个document或document的一部分;可以通过多个Entity生成的Field集合构成一个document

### Processor
processor负责提取数据源里的内容，转换并加入到索引里

### Transformer
Entity提取的fields集合可以经过Transformer转换后放入索引里，例如日期格式转换，数据格式转换

## DIH配置
### 配置solrconfig.xml
#### 配置solr-dataimporthandler-*.jar
```xml
<lib dir="${solr.install.dir:../../../..}/dist/" regex="solr-dataimporthandler-.*\.jar" />
```
#### 配置dataimport handler
```xml
<requestHandler name="/dataimport" class="solr.DataImportHandler">
      <lst name="defaults">
        <str name="config">data-config.xml</str>
        <lst name="datasource">
            <str name="driver">com.mysql.jdbc.Driver</str>
            <str name="url">jdbc:mysql://172.16.xx.xx:3306/dbname?zeroDateTimeBehavior=convertToNull</str>
            <str name="user">user</str>
            <str name="password">passwd</str>
        </lst>
      </lst>
  </requestHandler>
```

### 配置data-config.xml
在上面solrconfig.xml里的dataimport里提到了data-config.xml，data-config.xml定义了如何在数据源里获取数据以及数据源字段和solr字段的对应关系，这个配置文件需要和solrconfig.xml在同一个目录下

```xml
<dataConfig>
    <document>
        <entity name="city" pk="cityid"
            query="SELECT cityid,cityname,provinceid,ename,shortname FROM city">
            <field column="cityid" name="cityid"/>
            <field column="cityname" name="cityname" />
            <field column="provinceid" name="provinceid" />
            <field column="ename" name="ename" />
            <field column="shortname" name="shortname" />
       </entity>
    </document>
</dataConfig>
```




  