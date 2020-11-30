solr client

```ru
List<String> zkHosts = new ArrayList<String>();
zkHosts.add("127.0.0.1:9983");
Optional<String> zkChroot = Optional.empty();
CloudSolrClient cloudSolrClient = (new CloudSolrClient.Builder(zkHosts, zkChroot)).build();

```

- 如何定义schema

  使用cloud方式，是看不到managed-schema的，配置文件在zookeeper中，要查看这些文件，需要使用zkCli命令

  - 下载文件

  SOLR_HOME 代表solr的安装路径

  首先进入`{SOLR_HOME}\server\scripts\cloud-scripts`中，执行如下命令

  ·zkcli -zkhost localhost:2181 -cmd getfile /configs/mydemo/managed-schema d:\\\test.txt·

  意思是将zookeeper中的/configs/mydemo/managed-schema文件下载到d\\test.txt中

  - 上传配置文件

    现在还有问题，无法上传修改配置

  zkcli的官方文档https://lucene.apache.org/solr/guide/6_6/command-line-utilities.html#CommandLineUtilities-Uploadaconfigurationdirectory

- 如何导入数据

  使用DIH导入数据

  https://blog.csdn.net/qq_32352565/article/details/79241866

https://www.cnblogs.com/leeSmall/p/9094946.html

如何定时更新数据