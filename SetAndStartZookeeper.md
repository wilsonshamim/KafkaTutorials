ZooKeeper is a distributed, open-source coordination service for distributed applications.
It exposes a simple set of primitives that distributed applications can build upon to implement higher level services for synchronization, configuration maintenance, and groups and naming.
It is designed to be easy to program to, and uses a data model styled after the familiar directory tree structure of file systems. It runs in Java and has bindings for both Java and C.
zooKeeper allows distributed processes to coordinate with each other through a shared hierarchal namespace which is organized similarly to a standard file system. The name space consists of data registers - called znodes, in ZooKeeper parlance - and these are similar to files and directories. Unlike a typical file system, which is designed for storage, ZooKeeper data is kept in-memory, which means ZooKeeper can achieve high throughput and low latency numbers.
 

Role of ZooKeeper
A critical dependency of Apache Kafka is Apache Zookeeper, which is a distributed configuration and synchronization service. Zookeeper serves as the coordination interface between the Kafka brokers and consumers. The Kafka servers share information via a Zookeeper cluster. Kafka stores basic metadata in Zookeeper such as information about topics, brokers, consumer offsets (queue readers) and so on.
Since all the critical information is stored in the Zookeeper and it normally replicates this data across its ensemble, failure of Kafka broker / Zookeeper does not affect the state of the Kafka cluster. Kafka will restore the state, once the Zookeeper restarts. This gives zero downtime for Kafka. The leader election between the Kafka broker is also done by using Zookeeper in the event of leader failure.
 
 Steps to Start Zookeeper.

 update zookeeper.properties file located at CONFLUENT_HOME/etc/kafka.

clientPort=2181 [you can change your port]
 b.  start zookeeper using the below command.

 nohup  ./zookeeper-server-start $CONFLUENT_HOME/etc/kafka/zookeeper.properties  2>&1 > CONFLUENT_HOME/logs/zookeeper.log &

 c. verify the status of the zookeeper in the log file CONFLUENT_HOME/logs/zookeeper.log. you should not see any error.

d. additionally you can check if the zookeeper is started by running ps -ef | grep zookeeper.

 
