# Spring XD distributed mode
# Original von https://github.com/jeanpbond/spring-xd-docker-compose

Using docker-compose to run the containers :
	
	git clone https://github.com/s7nio/docker-hadoop-spring-xd.git
	cd docker-hadoop-spring-xd/docker-compose-springxd
    docker-compose up -d
	
To connect to the running admin server, use the springxd/shell container. dockerhost must be replace by your host running docker : 

	docker run --name shell -it springxd/shell
    xd:>admin config server http://dockerhost:9393
