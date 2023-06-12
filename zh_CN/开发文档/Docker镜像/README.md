# SolidUI Docker 编译

## 1.前置条件

[Docker](https://docs.docker.com/engine/install/) 1.13.1+

下载部署包https://github.com/CloudOrc/SolidUI/releases

## 2.镜像构建

### 2.1 服务端镜像构建

```shell script
tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin/entrance-server
docker build  -f ./docker/Dockerfile  -t  solidui-entrance:x.x.x .

```


### 2.2 前端镜像构建

```shell script

tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin/solidui-web
docker build  -f ./docker/Dockerfile  -t  solidui-web:x.x.x .

```
