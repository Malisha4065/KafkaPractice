## Kafka basics

### first bash into the container

docker exec -it kafka-kafka-1 bash

### create topic

kafka-topics --bootstrap-server kafka:9092 --create --topic products --partitions 3 --replication-factor 1

### produce

kafka-console-producer --bootstrap-server kafka:9092 --topic products
(then enter messages)

### produce with keys

kafka-topics --bootstrap-server kafka:9092 --create --topic keyed --partitions 3 --replication-factor 1
(create the topic)

kafka-console-producer --bootstrap-server kafka:9092 --topic keyed --property parse.key=true --property key.separator=:

### consume

kafka-console-consumer --bootstrap-server kafka:9092 --topic products --from-beginning

#### consume with key

kafka-console-consumer --bootstrap-server kafka:9092 --topic keyed --from-beginning --property print.key=true --property key.separator=:

#### also print partition number

kafka-console-consumer --bootstrap-server kafka:9092 --topic keyed --from-beginning --property print.key=true --property key.separator=: --property print.partition=true

### consumer group

kafka-console-consumer --bootstrap-server kafka:9092 --topic keyed --property print.key=true --property key.separator=: --property print.partition=true --group group1

### describe the topic

kafka-topics --bootstrap-server kafka:9092 --describe --topic products