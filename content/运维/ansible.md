---
title: "ansible useage"
date: 2019-10-04T16:08:36+08:00
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