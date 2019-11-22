###  docker 安装mysql
命令安装：

1. 映射到主机端口是 3306
2. 持久化MySQL数据到主机目录到  /root/docker-data/mysql-data
3. 设置密码为 123456
4. 设置容器的名称为 mysql8

```shell
docker run --name mysql8 -p 3306:3306 -v /root/docker-data/mysql-data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:8.0.18
```
参考：[docker 官方文档](https://hub.docker.com/_/mysql?tab=description)


### docker 使用nginx 运行vue项目
命令运行
```shell
docker run --name niuwork-admin -v /root/niuwork/niuwork-admin:/usr/share/nginx/html:ro -p 80:80 -d nginx
```
Dockerfile 构建镜像 niuwork-admin-Dockerfile
```shell
FROM nginx
COPY /root/niuwork/niuwork-admin/* /usr/share/nginx/html
```
使用命令构建：
```shell
docker build -t niuwork-admin-Dockerfile .
```
参考：
[docker 官方文档](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
[dockerHub nginx 文档](https://hub.docker.com/_/nginx)
[Dockfile 菜鸟教程](https://www.runoob.com/docker/docker-dockerfile.html)

