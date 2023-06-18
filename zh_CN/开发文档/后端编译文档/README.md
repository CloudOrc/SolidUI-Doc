# SolidUI 服务端编译

## 1.前置条件

### 1.1 环境要求

编译环境要求： 必须 JDK8 以上，Oracle/Sun 和 OpenJDK都支持。

自行按照Maven环境，建议使用3.5.4以上版本。或者直接使用源码中的maven-wrapper。

### 1.2 源码获取

* 方式1：从github仓库 https://github.com/CloudOrc/SolidUI 获取项目的源代码。

* 方式2：从https://github.com/CloudOrc/SolidUI/releases 下载下载所需版本的源码包。

## 2.服务端编译

```
cd solidui-x.x.x-src

# 编译
mvn clean -N install 
mvn clean install -Dmaven.test.skip=true

```

## 3.全量编译(服务端和前端)

```
cd solidui-x.x.x-src

# 编译
mvn clean -N install 
mvn clean install -Dmaven.test.skip=true -Prelease

```

