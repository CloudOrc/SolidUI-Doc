# SolidUI Docker-Compose 部署

## 1. 环境准备

[Docker](https://docs.docker.com/engine/install/) 1.13.1+
[Docker Compose](https://docs.docker.com/compose/) 1.11.0+

## 2.以 docker-compose 的方式启动 DolphinScheduler (推荐)

这种方式需要先安装 docker-compose, docker-compose 的安装网上已经有非常多的资料，请自行安装即可

### 2.1 下载部署包或者源码

方式1：从github仓库 https://github.com/CloudOrc/SolidUI 获取项目的源代码。

方式2：从https://github.com/CloudOrc/SolidUI/releases 下载下载所需版本的源码包。

请下载源码包 solidui-x.x.x-src.src.tar.gz 


### 2.2 拉取镜像并启动服务

```shell script
# 进入服务器（以Centos7为例）
tar -zxvf solidui-x.x.x-src.src.tar.gz 

cd solidui-x.x.x-src/solidui-dist/docker/

docker-compose up -d

```

### 2.3 访问服务

访问链接 http://localhost:8099

默认用户名密码：admin/admin