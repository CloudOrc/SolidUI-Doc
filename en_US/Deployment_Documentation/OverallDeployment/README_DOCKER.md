# SolidUI Docker-Compose deployment

## 1. Environment preparation

[Docker](https://docs.docker.com/engine/install/) 1.13.1+
[Docker Compose](https://docs.docker.com/compose/) 1.11.0+

## 2. Start DolphinScheduler with docker-compose (recommended)

This method needs to install docker-compose first, there are already a lot of information on the installation of docker-compose on the Internet, please install it yourself

### 2.1 Download deployment package or source code

Download at https://github.com/CloudOrc/SolidUI/releases

Please download the source package solidui-x.x.x-src.src.tar.gz


### 2.2 Pull the image and start the service

```shell script
# Enter the server (take Centos7 as an example)
tar -zxvf solidui-x.x.x-src.src.tar.gz

cd solidui-x.x.x-src/solidui-dist/docker/

docker-compose up -d

```

### 2.3 Accessing Services

Access link http://localhost:8099

Default username and password: admin/adm