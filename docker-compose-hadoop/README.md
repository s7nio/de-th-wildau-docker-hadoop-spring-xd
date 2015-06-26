# docker-compose-hadoop

This path based on the [badele](https://github.com/badele/docker-recipes/debian-hadoop) and use docker-compose for a hadoop cluster with 3 datanodes and 1 namenode.

## How to use

They are three easy steps.

1. Initialise HDFS
	- Run this only one time
	- ```$ docker-compose run namenode hdfs namenode -format```
2. Start the hadoop cluster
	- Launching the namenode and 3 datanodes with following command
	- ```$ docker-compose up -d```
3. Use the HDFS
	- ```$ hadoop fs -put LOCAL_FILE hdfs://localhost:8020/```
