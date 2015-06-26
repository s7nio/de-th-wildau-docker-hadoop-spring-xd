# docker-hadoop

Die folgenden Schritte sind notwenig um ein hadoop cluster auf zu setzen.

1. Docker image erstellen mit
	- ```$ docker build --force-rm -t hadoopmaster .```
2. Container erzeugen für Name- und Datanode
	1. Namenode
		- ```$ docker run -it --name=namenode -p 50070:50070 hadoopmaster:latest```
	2. Datanode
		- ```$ docker run -it --name=datanode hadoopmaster:latest```
3. Starten des namenode's
	- ```$ docker start namenode```
	- Liefert die bash des laufenden Containers
		- ```$ docker exec -it namenode bash```
