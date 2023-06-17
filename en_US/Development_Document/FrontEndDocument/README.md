# SolidUI front-end compilation

## 1. Preconditions

### 1.1 Install Node.js

This step is only required for the first use, if you already have a node environment, you can skip it

Download Node.js locally and install it. Download address: http://nodejs.cn/download/ (It is recommended to use node v16 version >= linkis-1.3.2)

### 1.2 Source code acquisition

Method 1: Obtain the source code of the project from the github repository https://github.com/CloudOrc/SolidUI.

Method 2: Download and download the source package of the required version from https://github.com/CloudOrc/SolidUI/releases.


## 2. Compile

### 2.1 Install npm dependencies

Execute the following command on the terminal command line:

```shell script
#Enter the project WEB root directory
cd solidui-x.x.x/solidui-web
#Install the dependencies required by the project
npm install --legacy-peer-deps
```
This step is only required for the first use.

### 2.2. Package project

Execute the following command on the terminal command line:

```shell script
npm run build
```

After the above command is executed successfully, the installation package dist of the front-end management console will be generated. You can directly put this folder into your static server, or refer to the installation documentation to use scripts for deployment and installation.