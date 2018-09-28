# KafkaSession

# install wget for Mac
brew install wget

# Kafka 
wget http://mirrors.fibergrid.in/apache/kafka/2.0.0/kafka_2.11-2.0.0.tgz

tar -zxvf kafka_2.11-2.0.0.tgz

# start zookeeper
bin/zookeeper-server-start.sh config/zookeeper.properties

# start Kafka broker
bin/kafka-server-start.sh config/server.properties

# create and list topics
bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 2 --topic test


bin/kafka-topics.sh --list --zookeeper localhost:2181

# Start consloe producer
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test

# start console consumer
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning


# Start console consumer with group

bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning --consumer-property group.id=mygroup
