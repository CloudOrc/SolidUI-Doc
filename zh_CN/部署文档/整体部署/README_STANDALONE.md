# SolidUI 单独部署

## 1.首次安装准备事项
### 1.1 Linux 服务器

#### 硬件要求
安装SolidUI 微服务1个，至少512M内存。每个微服务默认配置启动的jvm -Xmx 内存大小为 512M（内存不够的情况下，可以尝试调小至256/128M，内存足够情况下也可以调大）。

### 1.2 JDK准备

java版本要求：jdk1.8.0_201 或以上版本

### 1.3 数据库准备

Mysql5.7 或以上版本


## 2.配置修改
### 2.1 安装包准备

* 方式1：从官网下载地址: https://github.com/CloudOrc/SolidUI/releases ，下载对应的安装包（整体安装包）。
* 方式2：根据SolidUI 后端编译和前端编译自行编译出项目安装包。

上传安装包solidui-x.x.x-bin.tar.gz后，进行解压安装包
```shell script
 tar -zxvf solidui-x.x.x-bin.tar.gz
```

解压后的目录结构如下：
```shell script
drwxr-xr-x 2 root root  4096 Jun 10 20:31 docker
drwxr-xr-x 6 root root  4096 Jun 11 17:57 entrance-server
-rw-r--r-- 1 root root 27711 Jun  4 21:47 LICENSE
drwxr-xr-x 3 root root  4096 Jun 11 18:03 licenses
-rw-r--r-- 1 root root 24875 Jun  4 19:29 NOTICE
drwxr-xr-x 4 root root  4096 Jun 11 18:26 solidui-web
```

## 3.服务端按照和启动

### 3.1 准备工作

```
# 初始化数据库ddl 和 dml 路径
solidui-x.x.x-bin/entrance-server/conf/sql/mysql/solidui_mysql.sql

# 进入mysql数据库
mysql -h192.168.xx.xx -P3306 -uroot -p

# 创建数据库
CREATE DATABASE solidui DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;

# 执行数据库初始化脚本

source solidui-x.x.x-bin/entrance-server/conf/sql/mysql/solidui_mysql.sql

```

### 3.2 配置修改

```
cd solidui-x.x.x-bin/entrance-server/conf
#修改数据库连接信息
vi application.yaml
datasource:
url: jdbc:mysql://localhost:3306/solidui?useSSL=false&useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai
username: root
password: root

#0.2.0 版本增加python服务配置
vi solidui-x.x.x-bin/soliduimodelui/.env
#修改数据库连接信息
DB_HOST=localhost
DB_PORT=3306
DB_NAME=solidui
DB_USER=root
DB_PASS=SolidUI@123

```

### 3.3 服务端启动

```shell script
cd solidui-x.x.x-bin/entrance-server
# 启动服务
sh bin/start.sh
# 停止服务
sh bin/stop.sh

#0.2.0 版本增加python服务
cd solidui-x.x.x-bin
pip install -e .
modelui
```

## 4.前端部署

### 4.1 准备工作

参考[前端部署](../SolidUI前端部署文档/DEPLOY_WEB.md)

### 4.2 启动

访问默认链接 http://localhost:8099

默认用户名密码：admin/admin






