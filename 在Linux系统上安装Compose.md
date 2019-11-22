###  在Linux系统上安装Compose
在Linux上，您可以从[GitHub]( https://github.com/docker/compose/releases )上的Compose存储库发行页面下载Docker Compose二进制文件。按照链接中的说明进行操作，其中包括curl在终端中运行命令以下载二进制文件。这些分步说明也包含在下面。对于alpine，需要以下依赖包： py-pip，python-dev，libffi-dev，openssl-dev，gcc，libc-dev，和make

##### 1. 运行以下命令以下载Docker Compose的当前稳定版本：
```shell
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# 要安装其他版本的Compose，请替换1.24.1 为要使用的Compose版本。
```
##### 2. 将可执行权限应用于二进制文件：
```shell
$ sudo chmod +x /usr/local/bin/docker-compose
```
注意：如果命令docker-compose在安装后失败，请检查您的路径。您也可以创建指向/usr/bin或路径中任何其他目录的符号链接。
例如：

```shell
$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```
##### 3. 测试安装。
```shell
$ docker-compose --version 
docker-compose version 1.24.1, build 1110ad01
```
##### 4. 解除安装
如果使用curl以下命令进行安装，则要卸载Docker Compose ：
```shell
$ sudo rm /usr/local/bin/docker-compose
```
如果使用pip以下命令进行安装，则要卸载Docker Compose ：
```shell
$ pip uninstall docker-compose
```

参考：
[docker 官方文档](https://docs.docker.com/compose/install/)
[菜鸟教程 docker-compose](https://www.runoob.com/docker/docker-compose.html)