
```
./kafka-topics --bootstrap-server localhost:9092 --create --partitions 2 --replication-factor 1 --topic test

./kafka-console-consumer --bootstrap-server localhost:9092 --topic test

./kafka-console-producer --bootstrap-server localhost:9092 --topic test
```

Apache Kafka Java Client Library
- org.apache.kafka.clients.*: This contains the Producer, Consumer, and Admin API classes.
- org.apache.kafka.connect.*: This is used to build source and sink connectors.
- org.apache.kafka.streams.*: This is used to build stream processing applications.
- org.apache.kafka.common.*: This deals with cross-cutting concerns like security, error handling, etc.

