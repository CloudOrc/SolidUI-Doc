# SolidUI Docker 编译

## 1.前置条件

[Docker](https://docs.docker.com/engine/install/) 1.13.1+

* 方式1：从官网下载地址: https://github.com/CloudOrc/SolidUI/releases ，下载对应的安装包（整体安装包）。
* 方式2：根据SolidUI 自行编译出项目安装包。

## 2.镜像构建

### 2.1 服务端镜像构建-entrance-server

```shell script
tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin/entrance-server
docker build  -f ./docker/Dockerfile  -t  solidui-entrance:x.x.x .

```

### 2.2 服务端镜像构建-soliduimodelui (0.2.0版本后)
```shell script
tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin
# 修改.env配置文件
vi soliduimodelui/.env
SNAKEMQ_LISTENER=0.0.0.0
SNAKEMQ_CONNECTOR=soliduimodelui

docker build  -f ./soliduimodelui/docker/Dockerfile  -t  soliduimodelui:x.x.x .
```



### 2.3 前端镜像构建

```shell script

tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin/solidui-web
docker build  -f ./docker/Dockerfile  -t  solidui-web:x.x.x .

```
