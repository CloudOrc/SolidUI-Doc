# SolidUI is deployed separately

## 1. First-time installation preparations
### 1.1 Linux server

#### Hardware Requirements
Install one SolidUI microservice with at least 512M memory. The default jvm -Xmx memory size of each microservice is 512M (if the memory is not enough, you can try to reduce it to 256/128M, and you can also increase it if the memory is enough).

### 1.2 JDK preparation

Java version requirements: jdk1.8.0_201 or above

### 1.3 Database preparation

Mysql5.7 or above


## 2. Configuration modification
### 2.1 Installation package preparation

* Method 1: Download the address from the official website: https://github.com/CloudOrc/SolidUI/releases, and download the corresponding installation package (overall installation package).
* Method 2: Compile the project installation package by yourself according to the SolidUI back-end compilation and front-end compilation.

After uploading the installation package solidui-x.x.x-bin.tar.gz, decompress the installation package
```shell script
 tar -zxvf solidui-x.x.x-bin.tar.gz
```

The directory structure after decompression is as follows:
```shell script
drwxr-xr-x 2 root root 4096 Jun 10 20:31 docker
drwxr-xr-x 6 root root 4096 Jun 11 17:57 entrance-server
-rw-r--r-- 1 root root 27711 Jun 4 21:47 LICENSE
drwxr-xr-x 3 root root 4096 Jun 11 18:03 licenses
-rw-r--r-- 1 root root 24875 Jun 4 19:29 NOTICE
drwxr-xr-x 4 root root 4096 Jun 11 18:26 solidui-web
```

## 3. The server follows and starts

### 3.1 Preparations

```
# Initialize database ddl and dml paths
solidui-x.x.x-bin/entrance-server/conf/sql/mysql/solidui_mysql.sql

# Enter the mysql database
mysql -h192.168.xx.xx -P3306 -uroot -p

# create database
CREATE DATABASE solidui DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;

# Execute the database initialization script

source solidui-x.x.x-bin/entrance-server/conf/sql/mysql/solidui_mysql.sql

```
### 3.2 Configuration modification

```
cd solidui-x.x.x-bin/entrance-server/conf
# Modify database connection information
vi application.yaml
datasource:
url: jdbc:mysql://localhost:3306/solidui?useSSL=false&useUnicode=true&characterEncoding=UTF-8&serverTimezone=Asia/Shanghai
username: root
password: root

# 0.2.0 version adds python service configuration
vi solidui-x.x.x-bin/soliduimodelui/.env
# Modify database connection information
DB_HOST=localhost
DB_PORT=3306
DB_NAME=solidui
DB_USER=root
DB_PASS=SolidUI@123

```

### 3.3 Server start

```shell script
cd solidui-x.x.x-bin/entrance-server
# start the service
sh bin/start.sh
# Out of service
sh bin/stop.sh

# 0.2.0 version adds python service
cd solidui-x.x.x-bin
pip install -e .
modelui
```

## 4. Front-end deployment

### 4.1 Preparations

Refer to [Frontend Deployment](../FrontEendDeployment/DEPLOY_WEB.md)

### 4.2 Startup

Visit the default link http://localhost:8099

Default username and password: admin/admin


