---
title: "Nginx"
date: 2019-12-20T14:19:02+08:00
draft: false
---

### install
- yum install
```
rpm -ivh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
yum install nginx
```
- apt-get install

- source code install

- build your image

### module introduce


### common setting


### real ip process
```
      server {
          listen       80;
          server_name   xxxx;
          root         /usr/share/nginx/html/xxx;
          client_max_body_size 10m;
          location / {
              root     /usr/share/nginx/html/xxx;
              index    index.html;
              try_files $uri $uri/ /index.html last;
          }
          location /api/lsh/ {
              proxy_buffer_size 64k;
              proxy_buffers   32 32k;
              proxy_busy_buffers_size 128k;
              proxy_connect_timeout    600;
              proxy_read_timeout       600;
              proxy_send_timeout       600;
              proxy_set_header X-Real-IP  $remote_addr;
              proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
              proxy_pass http://xxxxx;
          }
      }
```

### deny

### statistics


### tls 
> 生成秘钥key
```
openssl genrsa -des3 -out server.key 2048
```

>去除输入密码
```
openssl rsa -in server.key -out server.key
```

>创建服务器证书的申请文件server.csr,运行
```
openssl req -new -key server.key -out server.csr
```

>创建CA证书
```
openssl req -new -x509 -key server.key -out ca.crt -days 3650
```

>服务器证书server.crt
```
openssl x509 -req -days 3650 -in server.csr -CA ca.crt -CAkey server.key -CAcreateserial -out server.crt
```

[nginx blog](https://juejin.im/post/5aa7704c6fb9a028bb18a993)