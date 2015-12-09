# README

# start up

```
$ docker-compose run namenode hdfs namenode -format
$ docker-compose up -d
$ docker inspect sxd_admin | grep IPAddress
	> 172.17.0.5
$ docker run --name sxd_shell --link sxd_admin -it springxd/shell

$ xd:> admin config server http://172.17.0.5:9393
```

## all up and running?

```
$ docker-machine ip dev
	> 192.168.99.100
```

- Hadoop ui: http://192.168.99.100:50070/
- SpringXD ui: http://192.168.99.100:9393/admin-ui/

## springxd config hdfs connection

```
$ docker inspect dfs_namenode | grep IPAddress
	> 172.17.0.8

$ docker run --link sxd_admin -it springxd/shell
	$ sxd_admin:> hadoop config fs --namenode hdfs://172.17.0.8:8020
	$ sxd_admin:> hadoop fs mkdir /data
	$ sxd_admin:> hadoop fs ls /
Found 1 items
drwxr-xr-x   - springxd supergroup          0 2015-12-09 14:52 /data
```
