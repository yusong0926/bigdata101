#  Kafka Cheatingsheet 

## Start Cassandra in Docker 
```sh
docker run -d -p 7199:7199 -p 9042:9042 -p 9160:9160 -p 7001:7001 --name cassandra cassandra:3.9
```
## Get Cassandra CLI 
### Download using shell comnands
```sh
wget http://apache.mirrors.ionfish.org/cassandra/3.9/apache-cassandra-3.9-bin.tar.gz
tar xvf apache-cassandra-3.9-bin.tar.gz
mv apache-cassandra-3.9 cassandra 
rm apache-cassandra-3.9-bin.tar.gz 
```
### Play with CLI
```sh
./cqlsh 192.168.99.100 9042
```
Creqte Keyspace
```sh
CREATE KEYSPACE "stock" WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1} AND durable_writes = 'true';
USE stock;
DESCRIBE KEYSPACE;
```
Create Table
```sh
CREATE TABLE user ( first_name text, last_name text, PRIMARY KEY (first_name));
DESCRIBE TABLE user;
```

Insert Data
```sh
INSERT INTO user (first_name, last_name) VALUES ('uncle', 'barney');
```

Query Data
```sh
SELECT COUNT (*) FROM USER;
SELECT * FROM user WHERE first_name='uncle';
SELECT * FROM user WHERE last_name='barney';
```

Delete Data
```sh
DELETE last_name FROM user WHERE first_name='uncle';
DELETE FROM user WHERE first_name='uncle';
```

Remove Table
```sh
TRUNCATE user;
DROP TABLE user;
```
Look into Cassandra Node
```sh
docker exec -it cassandra bash
cd /var/lib/cassandra
ls
```
