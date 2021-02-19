# rt-flink-kafka-java

# What is Apache Flink?
Apache Flink is a framework and distributed processing engine for stateful computations over unbounded and bounded data streams. Flink has been designed to run in all common cluster environments, perform computations at in-memory speed and at any scale.

#### Data can be processed as unbounded or bounded streams.

#### Unbounded Streams:
Unbounded streams have a start but no defined end. They do not terminate and provide data as it is generated.

#### Bounded Streams:
Bounded streams have a defined start and end. Bounded streams can be processed by ingesting all data before performing any computations.

- Apache Flink excels at processing unbounded and bounded data sets. 
- Precise control of time and state enable Flink’s runtime to run any kind of application on unbounded streams. 
- Bounded streams are internally processed by algorithms and data structures that are specifically designed for fixed sized data sets, yielding excellent performance.

#### USES:
- Apache Flink is an excellent choice to develop and run many different types of applications due to its extensive features set. Flink’s features include support for stream and batch processing, sophisticated state management, event-time processing semantics, and exactly-once consistency guarantees for state.

#### Run Applications at any Scale:
- applications processing multiple trillions of events per day,
- applications maintaining multiple terabytes of state, and
- applications running on thousands of cores.

# Apache Flink and Apache Kafka

This project is use a simple Flink job to show how to integrate Apache Kafka to Flink using the Flink Connector for Kafka.


## Start Kafka and Create Topic

Kafka uses ZooKeeper, if you do not have Zookeeper running, you can start it using the following command:

```bash
./bin/zookeeper-server-start.sh config/zookeeper.properties
```

Start a Kafka broker by running the following command in a new terminal:

``` bash
./bin/kafka-server-start.sh config/server.properties
```

In another terminal, run the following command to create a Kafka topic called `flink-demo`:

``` bash
./bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic flink-demo

```


## Build and Run the Application

In the project folder:

```
$ mvn clean package 
```

And run the Flink Consumer:

```
$ mvn exec:java -Dexec.mainClass=com.grallandco.demos.ReadFromKafka
```

and Producer: 

```
mvn exec:java -Dexec.mainClass=com.grallandco.demos.WriteToKafka
```

You should see messages printed in the Consumer console.

You can run this application directly in a Flink cluster.


