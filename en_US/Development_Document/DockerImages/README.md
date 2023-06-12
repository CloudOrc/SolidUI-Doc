# Docker Build for SolidUI

## 1. Prerequisites

[Docker](https://docs.docker.com/engine/install/) 1.13.1+

Download deployment package https://github.com/CloudOrc/SolidUI/releases

## 2. Image building

### 2.1 Building server-side image

```shell script
tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin/entrance-server 
docker build  -f ./docker/Dockerfile  -t  solidui-entrance:x.x.x . 

```

### 2.2 Building front-end image

```shell script

tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin/solidui-web
docker build  -f ./docker/Dockerfile  -t  solidui-web:x.x.x .

```