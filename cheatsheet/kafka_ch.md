#  Kafka Cheatingsheet 

## Start Kafka in Docker 
```sh
docker run -d -p 9092:9092 -e KAFKA_ADVERTISED_HOST_NAME=192.168.99.100 -e KAFKA_ADVERTISED_PORT=9092 --name kafka --link zookeeper:zookeeper confluent/kafka
```
## Get Kafka CLI 
### Download using shell comnands
```sh
wget http://apache.mirrors.ionfish.org/kafka/0.10.0.1/kafka_2.11-0.10.0.1.tgz
tar xvf kafka_2.11-0.10.0.1.tgz 
mv kafka_2.11-0.10.0.1 kafka
rm kafka_2.11-0.10.0.1 
```
### Play with CLI
Create Kafka Topic
```sh
/kafka-topics.sh --create --zookeeper 192.168.99.100 --replication-factor 1 --partitions 1 --topic bigdata
./kafka-topics.sh --list --zookeeper 192.168.99.100
```
Produce Messages
```sh
./kafka-console-producer.sh --broker-list 192.168.99.100:9092 --topic bigdata
```
Consume Messages
```sh
./kafka-console-consumer.sh --zookeeper 192.168.99.100:2181 --topic bigdata
./kafka-console-consumer.sh --zookeeper 192.168.99.100:2181 --topic bigdata --from-beginning
```
Look into Kafka Broker
```sh
docker exec -it kafka bash
cd /var/lib/kafka
ls
```

