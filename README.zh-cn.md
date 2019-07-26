# BDS
## 介绍
京东云区块链数据服务（BDS）是一款针对各类区块链非结构化数据, 提供了实时数据聚合、分析和可视化服务的产品。

Splitter 是开源项目区块链数据服务（BDS）的其中一个独立模块 - 提供数据解析服务。

Splitter 负责从消息队列（kafka）中消费区块链数据，并将数据插入到持久化的数据存储服务中（关系型数据库、数据仓库等），可用于进一步加工处理。

## 架构
![架构](./docs/bds-architecture.jpg)

## 环境部署 
### 安装 BDS
#### 环境初始化
在编译和运行 BDS 之前，必须先在本机安装 go 的编译环境: [go 语言安装](https://golang.org/doc/install)

#### Splitter 安装步骤

1. 设置项目路径为 `$GOPATH/src/github.com/jdcloud-bds/bds/`
2. 输入`go build -v github.com/jdcloud-bri/themis/cmd/bds-splitter`，编译得到可执行文件 *bds-splitter*
3. 新建配置文件 *splitter.conf*, 参考 `/config/splitter_example.conf` 配置文件模板
4. 运行程序 `./bds-splitter -c splitter.conf`

### 安装 confluent 和 kafka
#### 安装kafka
参见 [kafka 官网](http://kafka.apache.org/quickstart)

修改 config/server.properties 文件

* message.max.bytes=1048576000

#### 安装 confluent
参见 [confluent](https://docs.confluent.io/current/installation/installing_cp/zip-tar.html#prod-kafka-cli-install)

解压缩 confluent 安装包并运行Confluent Rest Proxy

修改 /etc/kafka-rest/kafka-rest.properties 文件

* max.request.size = 1048576000
* buffer.memory = 1048576000
* send.buffer.bytes = 1048576000

### 数据库
我们现在支持 SQL server 和 PostgreSQL 两种数据库，您可以选择其中一种作为数据存储方法。

#### SQL Server
购买 [云数据库 SQL Server](https://www.jdcloud.com/cn/products/jcs-for-sql-server)

#### PostgreSQL 
购买 [云数据库 PostgreSQL](https://www.jdcloud.com/cn/products/jcs-for-postgresql)

### 安装 Grafana 
参见 [Grafana 官网](https://grafana.com/)

## 源码
[Splitter 模块参考](./splitter/README.md)

### 开发步骤

1. 定义 kafka 消息的数据结构
2. 定义表结构
3. 解析 kafka 消息，并将数据存入数据库中

## 贡献
[贡献指南](./CONTRIBUTING.md)

## 开源许可 
[Apache License 2.0](./LICENSE)

## 项目展示
[区块链数据服务](https://bds.jdcloud.com/)

