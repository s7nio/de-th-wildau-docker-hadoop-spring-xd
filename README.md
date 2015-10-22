# docker-hadoop-spring-xd

## docker

Docker is an open container platform for distributed applications for developers and sysadmins. The docker tools chain composed of docker it self, docker-machine (aka boot2docker), docker-compose and docker-swarm. More detailed informations under https://docs.docker.com/.

### how to setup docker on OS X

Require a current virtualbox installation for the linux host system.

```
$ brew install docker docker-machine docker-compose docker-swarm
$ brew list | grep docker
$ docker-machine create -d virtualbox dev
$ docker-machine # start / stop / kill / rm NAME
$ docker-machine ls
$ docker-machine env dev
$ docker run -it ubuntu:latest /bin/bash
$ # this is the bash of yout first container
$ docker ps
```

## hadoop

Apache Hadoop is an open source framework for distributed storage and processing of large data sets on computer clusters. Hadoop are designed in different modiles. More detailed informations under https://hadoop.apache.org/docs/current/.

## spring xd

Spring XD simplify the development of big data applications to data ingestion, real time analytics, batch processing and data export. More detailed informations under http://projects.spring.io/spring-xd/.

Alternative are e.g. Apache Spark or Apache Flink
