SolidUI服务架构
-------------------------



### 1. 架构总览

![soliduiv0.1.0](images/soliduiv0.1.0structure.jpg)

将SolidUI 分为Entrance，MasterServer，ZkCluster，Worker，PublicEnhancement模块

Entrance:API接口层，主要负责前端UI层的请求，该服务统一提供RESTful api向外部提供请求服务

MasterServer:任务切分、任务提交

ZkCluster:ZooKeeper服务，系统中的MasterServer和WorkerServer节点都通过ZooKeeper来进行集群管理和容错，另外系统还基于ZooKeeper进行事件监听和分布式锁

Worker：主要负责任务的执行和提供日志服务。 WorkerServer服务启动时向Zookeeper注册临时节点，并维持心跳

PublicEnhancement：公共增强服务，例如数据源管理


