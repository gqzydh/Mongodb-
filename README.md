# Mongodb入门

> MongoDB 是一个基于分布式文件存储的数据库。由 C++ 语言编写。旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。
>
> MongoDB 是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像关系数据库的。



- ### 重要的网站###

  1. Mongodb官网：[www.mongodb.org](http://www.mongodb.org/)
  2. Mongodb国内官方网站：[www.mongoing.com](http://www.mongoing.com/)
  3. Mongodb中文社区：[http://docs.mongoing.com/manual-zh/](http://docs.mongoing.com/manual-zh/)
  4. Mongodb gitHub地址：[https://github.com/mongodb](https://github.com/mongodb)
  5. Mongodb bug问题解答：[https://jira.mongodb.org/browse/TOOLS-352?jql=](https://jira.mongodb.org/browse/TOOLS-352?jql=)


- ### MongoDB的慨念###

  - MongoDB
  - mongo
  - 索引
  - 集合
  - 复制集
  - 分片
  - 数据均衡

- ### MongoDB的使用

  - 基本的文档的读写更新删除
  - 各种不同类型的索引的创建与使用
  - 复杂的集合查询
  - 对数据集合进行分片，在不同分片间维持数据均衡
  - 数据备份与恢复
  - 数据迁移

- ### 简单运维

  - 部署Mongodb集群
  - 处理多种常见的故障
    - 单节点失效，如何恢复工作
    - 数据库意外被杀死如何进行数据恢复
    - 数据库发生拒绝服务时如何排查原因
    - 数据库磁盘快满时如何处理

- ### 相关工具###

  - [Robomongo](https://robomongo.org/) - 基于Shell的MongoDB图形化客户端管理软件。


-   [MongoBooster](http://www.mongobooster.com/) - MongoDB图形化管理软件，内嵌MongoShell，ES6语法，流畅查询及智能感知。
-   [Mongo Management Studio](http://www.litixsoft.de/english/mms/) - MongoDB图形化客户端管理软件。
    - [MongoChef](http://3t.io/mongochef) - MongoDB图形化客户端管理软件。
    - [mongoDB.app](https://gcollazo.github.io/mongodbapp/) - 在Mac 上最简单的使用MongoDB。

-   ### Mongodb启动命令，mongod的主要参数有

    -  ##### 基本配置#####

    | --quiet                | # 安静输出                                   |
    | ---------------------- | ---------------------------------------- |
    | --port arg             | # 指定服务端口号，默认端口27017                      |
    | --bind_ip arg          | # 绑定服务IP，若绑定127.0.0.1，则只能本机访问，不指定默认本地所有IP |
    | --logpath arg          | # 指定MongoDB日志文件，注意是指定文件不是目录              |
    | --logappend            | # 使用追加的方式写日志                             |
    | --pidfilepath arg      | # PID File 的完整路径，如果没有设置，则没有PID文件         |
    | --keyFile arg          | # 集群的私钥的完整路径，只对于Replica Set 架构有效         |
    | --unixSocketPrefix arg | # UNIX域套接字替代目录,(默认为 /tmp)                |
    | --fork                 | # 以守护进程的方式运行MongoDB，创建服务器进程              |
    | --auth                 | # 启用验证                                   |
    | --cpu                  | # 定期显示CPU的CPU利用率和iowait                  |
    | --dbpath arg           | # 指定数据库路径                                |
    | --diaglog arg          | # diaglog选项 0=off 1=W 2=R 3=both 7=W+some reads |
    | --directoryperdb       | # 设置每个数据库将被保存在一个单独的目录                    |
    | --journal              | # 启用日志选项，MongoDB的数据操作将会写入到journal文件夹的文件里 |
    | --journalOptions arg   | # 启用日志诊断选项                               |
    | --ipv6                 | # 启用IPv6选项                               |
    | --jsonp                | # 允许JSONP形式通过HTTP访问（有安全影响）               |
    | --maxConns arg         | # 最大同时连接数 默认2000                         |
    | --noauth               | # 不启用验证                                  |
    | --nohttpinterface      | # 关闭http接口，默认关闭27018端口访问                 |
    | --noprealloc           | # 禁用数据文件预分配(往往影响性能)                      |
    | --noscripting          | # 禁用脚本引擎                                 |
    | --notablescan          | # 不允许表扫描                                 |
    | --nounixsocket         | # 禁用Unix套接字监听                            |
    | --nssize arg (=16)     | # 设置信数据库.ns文件大小(MB)                      |
    | --objcheck             | # 在收到客户数据,检查的有效性，                        |
    | --profile arg          | # 档案参数 0=off 1=slow, 2=all               |
    | --quota                | # 限制每个数据库的文件数，设置默认为8                     |
    | --quotaFiles arg       | # number of files allower per db, requires --quota |
    | --rest                 | # 开启简单的rest API                          |
    | --repair               | # 修复所有数据库run repair on all dbs           |
    | --repairpath arg       | # 修复库生成的文件的目录,默认为目录名称dbpath              |
    | --slowms arg (=100)    | # value of slow for profile and console log |
    | --smallfiles           | # 使用较小的默认文件                              |
    | --syncdelay arg (=60)  | # 数据写入磁盘的时间秒数(0=never,不推荐)               |
    | --sysinfo              | # 打印一些诊断系统信息                             |
    | --upgrade              | # 如果需要升级数据库                              |

    - ##### Replicaton 参数#####

    | --fastsync      | # 从一个dbpath里启用从库复制服务，该dbpath的数据库是主库的快照，可用于快速启用同步 |
    | --------------- | ---------------------------------------- |
    | --autoresync    | # 如果从库与主库同步数据差得多，自动重新同步，                 |
    | --oplogSize arg | # 设置oplog的大小(MB)                         |

    - ##### 主/从参数#####

    | --master         | # 主库模式          |
    | ---------------- | --------------- |
    | --slave          | # 从库模式          |
    | --source arg     | # 从库 端口号        |
    | --only arg       | # 指定单一的数据库复制    |
    | --slavedelay arg | # 设置从库同步主库的延迟时间 |

    - ##### Replica set(副本集)选项

    | --replSet arg | # 设置副本集名称 |
    | ------------- | --------- |
    |               |           |

    - ##### Sharding(分片)选项#####

    | --configsvr      | # 声明这是一个集群的config服务,默认端口27019，默认目录/data/configdb |
    | ---------------- | ---------------------------------------- |
    | --shardsvr       | # 声明这是一个集群的分片,默认端口27018                  |
    | --noMoveParanoia | # 关闭偏执为moveChunk数据保存                     |

    - ##### 上述参数都可以写入 mongod.conf 配置文档里例如：######

      dbpath = /data/mongodb
      logpath = /data/mongodb/mongodb.log
      logappend = true
      port = 27017
      fork = true
      auth = true


    e.g：./mongod -shardsvr -replSet shard1 -port 16161 -dbpath /data/mongodb/data/shard1a -oplogSize 100 -logpath /data/mongodb/logs/shard1a.log -logappend -fork -rest

- ### Mac安装Mongodb ###

  > 参考官方文档 ： [http://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/)

  - 用HomeBrew方式 简单速度

  ```brew
  $ brew update     //更新Homebrew的package数据库
  ```

  ```brew
  $ brew install mongodb  //Install the MongoDB Binaries
  ```

  ```brew
  $ brew install mongodb --with-openssl    //Install the MongoDB Binaries with TLS/SSL Support
  ```

  - 启动Mongodb的方法：

  ```mongodb
  $ mongod —config /usr/local/etc/mongod.conf
  ```

  - 连接到Mongodb,可以用命令行工具mongo连接

  ```mongodb
  $ mongo
  ```

  > `mongo` 启动时报下列错误
  >
  > ```code
  > $ mongo
  > MongoDB shell version: 3.2.11
  > connecting to: test
  > 2016-11-24T17:09:26.753+0800 W NETWORK  [thread1] Failed to connect to 127.0.0.1:27017, reason: errno:61 Connection refused
  > 2016-11-24T17:09:26.755+0800 E QUERY    [thread1] Error: couldn't connect to server 127.0.0.1:27017, connection attempt failed :
  > connect@src/mongo/shell/mongo.js:229:14
  > @(connect):1:6
  >
  > exception: connect failed
  > ```

  解决方法：

  1.  查看保存数据库的目录是否存在

  ```code
     $ ls -ld data/db
  ```

  2. 启动Mongodb的同时指定数据库保目录

     ```code
     $ mongod --dbpath data/db
     ```

     ​


# Docker创建mongodb

1. `docker run -d --name mongo mongo`  使用docker创建mongodb容器和mongodb镜像
2. `docker exec -it mongo bash` 进入到mongodb容器
3. `mongo`  启动
4. `db`  返回当前正在使用的数据库
5. `use 数据库名字`  使用其他数据库

- #### 插入文档####

  - 插入一个文档：db.albums. insertOne({title: "再见理想"})

  - `db.albums.find（）` 查看albums集合里的所有的文档

  - `db.albums.insertMany([{},{}])` 向集合里插入多个文档

  - `db.albums.insert([{},{}])`  可以向集合里插入一个或者多个文档

  - 更新文档

    ```mongo
    db.albums.updateMany(    
    {},	 
    {$set: { artist: "Beyond"}}  
    )
    ```

    ```mongo
    db.albums.updateOne(    
    {title: "Parachutes"},	 
    {$set: { artist: "Coldplay"}}  
    )
    ```

  - 删除文档

    - `deleteOne` 删除找到的一个文档

    - `deleteMany` 删除找到的所有文档

    - `remove`  删除

      >db.albums.remove({})

- ### 查询###

  - 查询文档

  > 使用[Postman](https://www.getpostman.com/)  
  >
  > **Postman主要功能**
  >
  > 1. 主要用于模拟网络请求包
  > 2. 快速创建请求
  > 3. 回放、管理请求
  > 4. 快速设置网络代理

  - 查询year:1994

  ```db
  db.albums.find({year: "1994"},{title: 1, year:1 })
  ```

  - 查询所有字段 

  ```db
  db.albums.find({},{title: 1, year:1,"rating.average":1, _id:0  }).size()
  ```

  - 查询跳过前10位的字段 

  ```db 
  db.albums.find({},{title: 1, year:1,"rating.average":1, _id:0  }).skip(10)
  ```

  - 显示查询出来的前3位的字段 

  ```db 
  db.albums.find({},{title: 1, year:1,"rating.average":1, _id:0  }).limit(3)
  ```

  - 显示跳过查询出来的前3位的字段，显示后3位

  ```db 
  db.albums.find({},{title: 1, year:1,"rating.average":1, _id:0  }).limit(3).skip(3)
  ```

  - 排序，按照评分升序排列

  ```db 
  db.albums.find({},{title: 1, year:1,"rating.average":1, _id:0  }).sort({"rating.average:1"}) //-1 按照降序排列
  ```

  - 查询操作，查询评分大于9.5的，$gt - 大于/ $lt - 小于

  ```db 
  db.albums.find({"rating.average": {$gt: 9.5},{title:1, "rating.average":1, _id:0})
  ```

  - 查询操作，查找冒一类，$in：- 包含

  ```db 
  db.albums.find({genres{"$in":["动作"] }}，{title:1,genres:1,_id:0})
  ```

  - 查询操作，查找不包含冒一类，$nin：- 不包含

  ```db 
  db.albums.find({genres{"$in":["动作"] }}，{title:1,genres:1,_id:0})
  ```

  > 更对操作符 参考mongodb官方文档：https://docs.mongodb.com/
  >
  > 国内mongodb文档：http://docs.mongoing.com/manual-zh/

   

   

  ​
