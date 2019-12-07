# xisheng.blog
## what is hugo
Hugo是一种静态网站生成器。适用于搭建个人博客、小型公司主页等网站，是一种小型的CMS系统

## install hugo
go get -v hugo

## start create you blog
hego new xisheng.blog

# 生成public 静态文件
hugo -t casper

# 配置nginx代理
在 nginx 中配置public文件的位置

