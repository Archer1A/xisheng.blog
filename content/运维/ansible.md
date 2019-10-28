---
title: "ansible useage"
date: 2019-10-25 T16:08:36+08:00
draft: false
---

## 基本概念
Tasks：任务，由模板定义的操作列表
Variables：变量
Templates：模板，即使用模板语法的文件
Handlers：处理器 ，当某条件满足时，触发执行的操作
Roles：角色

## 定制返回信息
[official example](https://github.com/ansible/ansible/blob/devel/lib/ansible/plugins/callback/log_plays.py)

### modify config
```
bin_ansible_callbacks = True
callback_plugins = callback_plugins
callback_whitelist = self_logout
```
[task cost time codes](https://github.com/jlafon/ansible-profile)

## 命令行工具
ansible

ansible-playbook

## modules
### template 和 wget 下载文件的速度对比
    wget 要比 template 快
        
      2s
      shell: wget https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo -O /etc/yum.repos.d/docker-ce.repo
        
      8s
      template:
        src: templates/docker-ce.repo
        dest: /etc/yum.repos.d/docker-ce.repo


### yum
是否可以 多个一起

### 优化大量的shell一起执行的速度

### 回掉脚本

### python ansible api

### ansible 数组写在一行不好看