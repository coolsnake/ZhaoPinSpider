# 招聘信息爬虫<small>Powered By PySpider</small>

- 目前已完成信息源信息抓取,抓取内容如下(尚未清洗)：
  - Job51

    1. url
    2. 地点
    3. 公司名称
    4. 公司状况
    5. 薪资
    6. 职位描述
    7. 相关信息
    8. 福利
    9. 上班地址
    10. 发布日期

- 使用分布式爬取，Master负责消息队列、数据储存和爬虫调度，Slaver负责页面抓取和页面解析
  - Master `config.json`配置文件
  ```
  {
      "taskdb": "mongodb+taskdb://host:port/taskdb",
      "projectdb": "mongodb+projectdb://host:port/projectdb",
      "resultdb": "mongodb+resultdb://host:port/resultdb",
      "message_queue": "redis://host:6379/db",
      /*PhantomJS配置,目前尚未使用该自动化测试工具*/
      /*"phantomjs-proxy":"host:port",*/
      "webui":{
                  "host":"host",
                  "port":"80",
                  "scheduler-rpc":"http://master_scheduler_host:scheduler_port",
                  "fetcher-rpc":"http://192.168.218.102:5002"
      },
      "scheduler":{
                  "xmlrpc":true,
                  "xmlrpc-host":"0.0.0.0",
                  "xmlrpc-port":"5001"
      },
      "fetcher":{
                  "xmlrpc":true,
                  "xmlrpc-host":"0.0.0.0",
                  "xmlrpc-port":"5002"
      }
    }
    ```


    > [参考资料](http://tingyun.site/2017/09/08/pyspider%E5%88%86%E5%B8%83%E5%BC%8F%E9%83%A8%E7%BD%B2/)
