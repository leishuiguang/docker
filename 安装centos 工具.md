###  安装centos 工具
#### 1. centos7没有安装ifconfig命令的解决方法
```shell
# 查询ifconfig 这个命令所在的工具包
# 显示 net-tools.x86_64 : Basic networking tools
sudo yum search ifconfig
# 安装net-tools.x86_64
sudo yum -y install net-tools.x86_64
```

#### 2. 安装vim编辑器
```shell
sudo yum -y install vim
```

