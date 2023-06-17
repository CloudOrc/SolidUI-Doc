# SolidUI 前端部署

## 1 准备工作

* 方式1：从官网下载地址: https://github.com/CloudOrc/SolidUI/releases ，下载对应的安装包（整体安装包）。
* 方式2：根据SolidUI 自行编译出项目安装包。

```
tar -zxvf solidui-x.x.x-bin.tar.gz
#前端目录
cd solidui-x.x.x/solidui-web
```



## 2 部署

> 分为两种部署方式，自动化部署和手动部署

### 2.1 自动化部署(推荐)

#### 2.1.1 修改配置config.sh
```shell script
# solidui 服务地址
solidui_url="http://127.0.0.1:12345"

#可以配置为安装机器的ip 也可以使用默认值
solidui_ipaddr=127.0.0.1
# 访问管理台的端口
solidui_port=12345
```

#### 2.1.2 执行部署脚本

```shell script
# nginx 需要sudo权限进行安装
sudo sh install.sh
```
安装后，solidui的nginx配置文件默认是 在`/etc/nginx/conf.d/solidui.conf`
nginx的日志文件在 `/var/log/nginx/access.log` 和`/var/log/nginx/error.log`
生成的solidui的nginx配置文件示例如下:
```nginx
server {
  listen       8099;
  server_name  localhost;

  location / {
    root   /appcom/Install/solidui-web/dist; # 静态文件目录 
    index  index.html index.html;
  }

  location /solidui {
    proxy_pass http://localhost:12345; # 后端 SolidUI 的地址
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header x_real_ipP $remote_addr;
    proxy_set_header remote_addr $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_http_version 1.1;
    proxy_connect_timeout 4s;
    proxy_read_timeout 600s;
    proxy_send_timeout 12s;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection upgrade;
  }

  error_page   500 502 503 504  /50x.html;
  location = /50x.html {
    root   /usr/share/nginx/html;
  }
}
```

### 2.2 手动部署

#### 2.2.1 安装Nginx
> 如果已经安装过nginx 可以跳过

```shell script
sudo yum install nginx -y
```

#### 2.2.2 修改配置文件
```shell script
sudo vi /etc/nginx/conf.d/solidui.conf
```

添加如下内容：

```
server {
  listen       8080;# 访问端口
  server_name  localhost;
  #charset koi8-r;
  #access_log  /var/log/nginx/host.access.log  main;
  location / {
    root   /opt/solidui/solidui-web/dist; # 前端包解压的目录
    index  index.html index.html;
  }

  location /solidui {
    proxy_pass http://127.0.0.1:12345; # solidui 服务地址
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header x_real_ipP $remote_addr;
    proxy_set_header remote_addr $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_http_version 1.1;
    proxy_connect_timeout 4s;
    proxy_read_timeout 600s;
    proxy_send_timeout 12s;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection upgrade;
  }
 
  error_page   500 502 503 504  /50x.html;
  location = /50x.html {
    root   /usr/share/nginx/html;
  }
}
```

#### 2.2.3 资源部署 

假设前端`npm run build`后的产物路径是:`/opt/solidui/solidui-web/dist`

#### 2.2.4  启动服务

```
sudo systemctl restart nginx
```

## 3 登录

浏览器访问`http://solidui_ipaddr:solidui_port` 其中solidui_port为config.sh里面配置的端口，solidui_ipaddr为安装机器的IP，默认的账号密码是：`admin/admin`

## 4 注意事项 

如果需要修改端口或则静态资源目录等，请修改`/etc/nginx/conf.d/solidui.conf` 文件后执行 `sudo nginx -s reload` 命令
:::caution 注意
- 查看nginx是否正常启动：检查nginx进程是否存在 `ps -ef |grep nginx` 
- 检查nginx的配置是否正确 `sudo nginx -T ` 
- 如果端口被占用，可以修改nginx启动的服务端口`/etc/nginx/conf.d/solidui.conf`listen端口值，保存后重新启动
:::

## 5 常见问题
### 5.1 接口超时

```
sudo vi /etc/nginx/conf.d/solidui.conf
```
更改接口超时时间

```
proxy_read_timeout 600s
```
