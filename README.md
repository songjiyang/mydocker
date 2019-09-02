
使用docker在本地搭建mysql服务

#### mysql

```bash
cd mysql
docker-compose up -d
```

- 如果本地有正在运行的mysql,可以停掉，或者在docker-compose.yml配置文件更换端口
- 如果没有mysql客户端可以装MySQLWorkbench, 然后将`export PATH=$PATH:/Applications/MySQLWorkbench.app/Contents/MacOS` 放入.bashrc或者.zshrc文件中，使用MySQLWorkbench的客户端
- 如果报`ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)`错误， 将`mysql --host localhost -u root -p`改成`mysql --host 127.0.0.1 -u root -p`, 因为127.0.0.1会让客户端使用tcp/ip连接而不是socket，具体可以查看[stackoverflow](https://stackoverflow.com/questions/16325607/cant-connect-to-local-mysql-server-through-socket-tmp-mysql-sock)
- mysql的数据存在dbData目录里面，如果不删除这个目录，原来的数据是存在的，如果想更换密码只改docker-compose.yml不会生效，可以使用mysql客户端去改密码或者当数据不再有用的时候，直接删除dbData目录


#### mongodb

```bash
cd mongodb
docker-compose up -d
```

- 客户端`docker exec -it mongodb mongo`, mongodb是容器名称
#### redis

```bash
cd redis
docker-compose up -d
```

- 客户端`docker exec -it redis redis-cli`, redis是容器名称

#### elasticsearch

[官方文档](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)

- 将数据放入dbData, 加入kibana, 要放入同一个网络，kibana要等elasticsearch加载好才能加载，时间可能稍微有点长，macbook air等了快10分钟。
- [Kibana server is not ready yet解决方法](https://blog.csdn.net/qq_38796327/article/details/90480314)