# SolidUI Server-side Compilation

## 1. Prerequisites

### 1.1 Environmental requirements

Compilation environment requirements: Must be JDK8 or above, both Oracle/Sun and OpenJDK are supported.

Install Maven environment yourself, version 3.5.4 or above is recommended. Or you can directly use the maven-wrapper in the source code.

### 1.2 Get the source code

Get the project source code from the GitHub repository https://github.com/CloudOrc/SolidUI.

## 2. Server-side compilation

```
cd solidui-x.x.x-src  

# Compile
mvn clean -N install
mvn clean install -Dmaven.test.skip=true
``` 

## 3. Full compilation (server side and front end)

```
cd solidui-x.x.x-src  

# Compile
mvn clean -N install  
mvn clean install -Dmaven.test.skip=true -Prelease
```