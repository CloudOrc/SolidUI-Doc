# SolidUI front-end deployment

## 1 Preparations

* Method 1: Download the address from the official website: https://github.com/CloudOrc/SolidUI/releases, and download the corresponding installation package (overall installation package).
* Method 2: Compile the project installation package according to SolidUI.

```
tar -zxvf solidui-x.x.x-bin.tar.gz
# front-end directory
cd solidui-x.x.x/solidui-web
```



## 2 deployment

> Divided into two deployment methods, automated deployment and manual deployment

### 2.1 Automated deployment (recommended)

#### 2.1.1 Modify configuration config.sh
```shell script
# solidui service address
solidui_url="http://127.0.0.1:12345"

#It can be configured as the ip of the installation machine or use the default value
solidui_ipaddr=127.0.0.1
# Port to access the management console
solidui_port=12345
```

#### 2.1.2 Execute the deployment script
```shell script
# nginx needs sudo permission to install
sudo sh install.sh
```
After installation, the nginx configuration file of solidui is in `/etc/nginx/conf.d/solidui.conf` by default
The log files of nginx are in `/var/log/nginx/access.log` and `/var/log/nginx/error.log`
An example of the generated solidui nginx configuration file is as follows:
```nginx
server {
  listen 8099;
  server_name localhost;

  location / {
    root /appcom/Install/solidui-web/dist; # Static file directory
    index index.html index.html;
  }

  location /solidui {
    proxy_pass http://localhost:12345; # The address of the backend SolidUI
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

  error_page 500 502 503 504 /50x.html;
  location = /50x.html {
    root /usr/share/nginx/html;
  }
}
```

### 2.2 Manual deployment

#### 2.2.1 Install Nginx
> If you have already installed nginx, you can skip it

```shell script
sudo yum install nginx -y
```

#### 2.2.2 Modify configuration file
```shell script
sudo vi /etc/nginx/conf.d/solidui.conf
```
Add the following:

```
server {
  listen 8080;# access port
  server_name localhost;
  #charset koi8-r;
  #access_log /var/log/nginx/host.access.log main;
  location / {
    root /opt/solidui/solidui-web/dist; # The directory where the front-end package is decompressed
    index index.html index.html;
  }

  location /solidui {
    proxy_pass http://127.0.0.1:12345; # solidui service address
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
 
  error_page 500 502 503 504 /50x.html;
  location = /50x.html {
    root /usr/share/nginx/html;
  }
}
```

#### 2.2.3 Resource deployment

Suppose the product path after the front-end `npm run build` is: `/opt/solidui/solidui-web/dist`

#### 2.2.4 Start service

```
sudo systemctl restart nginx
```

## 3 login

Browser access `http://solidui_ipaddr:solidui_port` where solidui_port is the port configured in config.sh, solidui_ipaddr is the IP of the installation machine, and the default account password is: `admin/admin`

## 4 Notes

If you need to modify the port or static resource directory, etc., please modify the `/etc/nginx/conf.d/solidui.conf` file and execute the `sudo nginx -s reload` command
:::caution Caution
- Check whether nginx starts normally: check whether the nginx process exists `ps -ef |grep nginx`
- Check if the configuration of nginx is correct `sudo nginx -T`
- If the port is occupied, you can modify the service port `/etc/nginx/conf.d/solidui.conf`listen port value started by nginx, save and restart
  :::

## 5 Frequently Asked Questions
### 5.1 Interface timeout

```
sudo vi /etc/nginx/conf.d/solidui.conf
```
Change interface timeout

```
proxy_read_timeout 600s
```
