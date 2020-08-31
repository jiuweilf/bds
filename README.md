我是光年实验室高级招聘经理。
我在github上访问了你的开源项目，你的代码超赞。你最近有没有在看工作机会，我们在招软件开发工程师，拉钩和BOSS等招聘网站也发布了相关岗位，有公司和职位的详细信息。
我们公司在杭州，业务主要做流量增长，是很多大型互联网公司的流量顾问。公司弹性工作制，福利齐全，发展潜力大，良好的办公环境和学习氛围。
公司官网是http://www.gnlab.com,公司地址是杭州市西湖区古墩路紫金广场B座，若你感兴趣，欢迎与我联系，
电话是0571-88839161，手机号：18668131388，微信号：echo 'bGhsaGxoMTEyNAo='|base64 -D ,静待佳音。如有打扰，还请见谅，祝生活愉快工作顺利。

# BDS 
![logo](./docs/bds-logo.png)

## Introduction
JD Cloud Blockchain Data Service (BDS) is a realtime data aggregating, analyzing and visualization service for chain-like unstructured data from all kinds of 3rd party Blockchains

Splitter is the key module of Blockchain Data Service (BDS) and provides data analysis capability.

Splitter is responsible for consuming blockchain data from message queue (kafka) and inserting data into persistent data storage services (relational database, data warehouse, etc.) for further processing

## Architecture 
![Architecture](./docs/bds-architecture.jpg)

## Environment Deployment
### Install BDS 

#### Environment initialization
Before compiling and running BDS, you must install go's compilation environment locally: [go install](https://golang.org/doc/install)

#### Install Splitter steps

1. Set the path of project : `$GOPATH/src/github.com/jdcloud-bds/bds/`
2. Input`go build -v github.com/jdcloud-bds/bds/cmd/bds-splitter`，compile to get executable file *bds-splitter*
3. Build new configuration file *splitter.conf*,  see `/config/splitter_example.conf` configuration file template
4. Run program `./bds-splitter -c splitter.conf`

### Install confluent and kafka
#### Install kafka
See [kafka](https://kafka.apache.org/quickstart)

##### Modify config/server.properties 

* message.max.bytes=1048576000

#### Install confluent 
see [confluent](https://docs.confluent.io/current/installation/installing_cp/zip-tar.html#prod-kafka-cli-install)

Unzip the confluent package and run Confluent REST Proxy

##### Modify  <path-to-confluent>/etc/kafka-rest/kafka-rest.properties 

* max.request.size = 1048576000
* buffer.memory = 1048576000
* send.buffer.bytes = 1048576000

### Database
Database we now support SQL Server, PostgreSQL, you can choose one as a data storage method.

#### SQL Server
Buy [JCS For SQL Server](https://www.jdcloud.com/cn/products/jcs-for-sql-server)

#### PostgreSQL 
Buy [JCS For PostgreSQL](https://www.jdcloud.com/cn/products/jcs-for-postgresql)

After you run the database, you need to manually create new database and use the database name initialization splitter.conf.

### Install Grafana
See [Grafana Official](https://grafana.com/)

## Source code
[Splitter Modules](./splitter/README.md)

### Development Steps
1. Define the data structure of Kafka messages.
2. Define table structure.
3. Analyze Kafka message and store data in database.

## Contributing
[Contributing guide](./CONTRIBUTING.md)

## License
[Apache License 2.0](./LICENSE)

## Project Demonstration
[Blockchain Data Service](https://bds.jdcloud.com/)
