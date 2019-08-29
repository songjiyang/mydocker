
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