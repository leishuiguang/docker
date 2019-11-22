### centos7 安装社区版docker (docker ce)
##### 1. 卸载旧版本

	较旧的Docker版本称为docker或docker-engine。如果已安装这些程序，请卸载它们以及相关的依赖项。
```shell
$ sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```
##### 2. 使用存储库安装
在新主机上首次安装Docker Engine-Community之前，需要设置Docker存储库。之后，您可以从存储库安装和更新Docker。

设置存储库
①安装所需的软件包。yum-utils提供了yum-config-manager 效用，并device-mapper-persistent-data和lvm2由需要 devicemapper存储驱动程序。
```shell
$ sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
```
②使用以下命令来设置稳定的存储库。
```shell
$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```
##### 3. 安装DOCKER ENGINE-社区
① 安装最新版本的Docker Engine-Community和containerd，或者转到下一步安装特定版本：
```shell
$ sudo yum install docker-ce docker-ce-cli containerd.io
```
如果提示您接受GPG密钥，请验证指纹是否匹配 060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35，如果是，则接受它。
② 要安装特定版本的Docker Engine-Community，请在存储库中列出可用版本，然后选择并安装一种。列出并排序您存储库中可用的版本。此示例按版本号（从高到低）对结果进行排序，并被截断：
```shell
$ yum list docker-ce --showduplicates | sort -r
```
返回的列表取决于启用的存储库，并且特定于您的CentOS版本（.el7在此示例中以后缀表示）。
通过其完全合格的软件包名称安装特定版本，该软件包名称是软件包名称（docker-ce）加上版本字符串（第二列），从第一个冒号（:）一直到第一个连字符，并用连字符（-）分隔。例如，docker-ce-18.09.1。
```shell
$ sudo yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io
```
例如：
```shell
yum install docker-ce-19.03.5-3.el7  docker-ce-cli-19.03.5-3.el7  containerd.io
```
Docker已安装但尚未启动。docker创建该组，但没有用户添加到该组。
③ 启动Docker。
```shell
$ sudo systemctl start docker
```
④ 通过运行hello-world 映像来验证是否正确安装了Docker Engine-Community 。
```shell
$ sudo docker run hello-world
```
⑤ 重启Docker
```shell
$ sudo systemctl restart docker
```
⑥ 停止Docker
```shell
$ sudo systemctl stop docker
```
此命令下载测试图像并在容器中运行。容器运行时，它会打印参考消息并退出。
Docker Engine-Community已安装并正在运行。您需要使用sudo来运行Docker命令。继续进行Linux后安装，以允许非特权用户运行Docker

参考：[docker 官方文档](https://docs.docker.com/install/linux/docker-ce/centos/)