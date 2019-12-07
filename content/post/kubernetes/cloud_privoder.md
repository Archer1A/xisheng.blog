---
title: "cloud_provider"
date: 2019-10-18T16:08:36+08:00
draft: true
---

[cloudprovider.Interface](https://github.com/kubernetes/kubernetes/blob/master/pkg/cloudprovider/cloud.go)


在 Kubernetes v1.6，引入了 Cloud Controller Manager（CCM），目的就是最终替代 Cloud Provider。截止到最新的 Kubernetes v1.11，还是处于 beta 阶段。

Cloud Provider 的作用
在 Kubernetes 中有三个组件对 Cloud Provider 有依赖，分别是：
 - kube-controller-manager
 - kubelet
 - kube-apiserver
 
## alicloud
https://github.com/kubernetes/cloud-provider-alibaba-cloud/blob/b83e89ae7bbd482fbabac79d2704c1266092c0a9/docs/getting-started.md

Update kubelet info with provider id info and restart kubelet:You should provide 
--hostname-override=${REGION_ID}.${INSTANCE_ID}
 --provider-id=${REGION_ID}.${INSTANCE_ID} arguments in all of your kubelet unit file. 
 The format is ${REGION_ID}.${INSTANCE_ID}. See kubelet.service for more details.