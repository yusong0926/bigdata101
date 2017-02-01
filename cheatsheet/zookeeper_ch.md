#  Zookeeper Cheatingsheet 

## Start Zookeepr in Docker 
```sh
docker run -d -p 2181:2181 -p 2888:2888 -p 3888:3888 --name zookeeper confluent/zookeeper
```
## Get Zookeeper CLI 
### Download using shell comnands
```sh
wget http://apache.mirrors.ionfish.org/zookeeper/zookeeper-3.4.8/zookeeper-3.4.8.tar.gz
tar xvf zookeeper-3.4.8.tar.gz
mv zookeeper-3.4.8 zookeeper
rm zookeeper-3.4.8.tar.gz
```
### Play with CLI
```sh
./zkCli.sh -server 192.168.99.100:2181
```
Browse Znode Data
```sh
ls /
ls /zookeeper
get /zookeeper/quota
```
Create Znode Data
```sh
create /workers "bittiger"
```
Delete Znode Data
```sh
delete /workers
```
Create Ephemeral Znode Data
```sh
create -e /workers "unclebarney"
```
Watcher
```sh
get /workers true
```


