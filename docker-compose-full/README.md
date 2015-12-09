# README

```
$ docker-compose run namenode hdfs namenode -format
$ docker-compose up -d
$ docker inspect sxd_admin | grep IPAddress
	> 172.17.0.5
$ docker run --name sxd_shell --link sxd_admin -it springxd/shell
	>xd:> admin config server http://<sxd_adminIPADDRESS>:9393
```

## check

```
$ docker-machine ip dev
	> 192.168.99.100
```

- Hadoop ui: http://192.168.99.100:50070/

- SpringXD ui: http://192.168.99.100:9393/admin-ui/

