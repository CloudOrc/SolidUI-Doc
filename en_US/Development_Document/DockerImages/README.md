# Docker Build for SolidUI

## 1. Prerequisites

[Docker](https://docs.docker.com/engine/install/) 1.13.1+

* Method 1: Download the address from the official website: https://github.com/CloudOrc/SolidUI/releases, and download the corresponding installation package (overall installation package).
* Method 2: Compile the project installation package according to SolidUI.

## 2. Image building

### 2.1 Building server-side image build-entrance-server

```shell script
tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin/entrance-server 
docker build  -f ./docker/Dockerfile  -t  solidui-entrance:x.x.x . 

```


### 2.2 Server-side image build-soliduimodelui (after version 0.2.0)
```shell script
tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin
docker build  -f ./soliduimodelui/docker/Dockerfile  -t  soliduimodelui:x.x.x .
```

### 2.3 Building front-end image

```shell script

tar -zxvf solidui-x.x.x-bin.tar.gz
cd solidui-x.x.x-bin/solidui-web
docker build  -f ./docker/Dockerfile  -t  solidui-web:x.x.x .

```