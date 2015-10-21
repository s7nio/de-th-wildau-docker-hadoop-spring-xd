# docker-compose-hadoop

This path based on the [badele](https://github.com/badele/docker-recipes/debian-hadoop) and use docker-compose for a hadoop cluster with 3 datanodes and 1 namenode.

## How to setup

They are two easy steps.

1. Initialise HDFS
    - Erase all data!
	- ```$ docker-compose run namenode hdfs namenode -format```
2. Start hadoop cluster
	- Launching the namenode and 3 datanodes with following command (as daemon)
	- ```$ docker-compose up -d```

## How to use

- HDFS
    - ```$ docker exec -it hadoop_namemode bash```
	- ```$ hadoop fs -put LOCAL_FILE /HDFS_LOCATION```
	- ```$ hadoop fs -ls /```

- Container
    - ```docker start $(docker ps -a -q)```
    - ```docker stop $(docker ps -a -q)```
