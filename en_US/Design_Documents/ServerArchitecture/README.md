SolidUI Service Architecture
-------------------------



### 1. Architecture Overview

![soliduiv0.1.0](images/soliduiv0.1.0structure.jpg)

Divide SolidUI into Entrance, MasterServer, ZkCluster, Worker, PublicEnhancement modules

Entrance: API interface layer, mainly responsible for the request of the front-end UI layer, the service uniformly provides RESTful api to provide request services to the outside

MasterServer: task segmentation, task submission

ZkCluster: ZooKeeper service, the MasterServer and WorkerServer nodes in the system perform cluster management and fault tolerance through ZooKeeper, and the system also performs event monitoring and distributed locks based on ZooKeeper

Worker: Mainly responsible for task execution and providing log services. When the WorkerServer service starts, register the temporary node with Zookeeper and maintain the heartbeat

PublicEnhancement: public enhancement services, such as data source management


