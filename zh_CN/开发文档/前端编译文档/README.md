# SolidUI 前端编译

## 1.前置条件

### 1.1 安装Node.js

该步骤仅第一次使用时需要执行,如果已有node环境，可跳过

将Node.js下载到本地，安装即可。下载地址：http://nodejs.cn/download/ （建议使用node v16版本 >= linkis-1.3.2）

### 1.2 源码获取

方式1：从github仓库 https://github.com/CloudOrc/SolidUI 获取项目的源代码。

方式2：从https://github.com/CloudOrc/SolidUI/releases 下载下载所需版本的源码包。


## 2.编译

### 2.1 安装npm依赖

在终端命令行中执行以下指令：

```shell script
#进入项目WEB根目录
cd solidui-x.x.x/solidui-web
#安装项目所需依赖
npm install --legacy-peer-deps 
```
该步骤仅第一次使用时需要执行。

### 2.2. 打包项目

在终端命令行中执行以下指令：

```shell script
npm run build
```

上述命令执行成功后，会生成前端管理台安装包 dist，可以直接将该文件夹放进您的静态服务器中，或者参考安装文档，使用脚本进行部署安装。