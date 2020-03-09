---
title: "cloud-controller-manager"
date: 2020-03-09T10:19:04+08:00
draft: true
---

### 什么是CCM

### CCM 重构策略


### CCM　架构介绍
![client-go](http://xisheng.vip/images/ccm.png)

node controller
- zone
- instance - ip_address
在CCM还未初始化kubelet所在节点时，需标记此节点类似“NotReady”的状态，防止scheduler调度pod到此节点时产生一系列错误。此功能通过给节点加上如下Taints并在CCM初始化后删去此Taints实现：

service controller
- loadBalancer update
- loadBalancer create
- loadBalancer delete

route controller

pvLabel controller

### 云服务上需要实现哪些接口


### CCM 源码分析
启动流程
node initialized




### 自动动手写一个CCM插件


