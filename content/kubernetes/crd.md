---
title: "Crd"
date: 2019-12-25T09:05:09+08:00
draft: false
---

### 1.CRD
CustomResourceDefinition 是kubernetes的资源扩展方式

### 2.sample-controller 
sample-controller 是 kubernetes 官方提供的 CRD Controller 样例实现，
Git 地址：https://github.com/kubernetes/sample-controller
添加自定义控制器 Bar 示例代码：https://github.com/SataQiu/sample-controller/tree/bar

[博客参考](https://blog.openshift.com/kubernetes-deep-dive-code-generation-customresources/)

### 3.[使用client-go包访问Kubernetes CRD](https://aijishu.com/a/1060000000011204)
####3.1 create CRD
```
apiVersion: "apiextensions.k8s.io/v1beta1"
kind: "CustomResourceDefinition"
metadata:
  name: "projects.example.sealyun.com"
spec:
  group: "example.sealyun.com"
  version: "v1alpha1"
  scope: "Namespaced"
  names:
    plural: "projects"
    singular: "project"
    kind: "Project"
  validation:
    openAPIV3Schema:
      required: ["spec"]
      properties:
        spec:
          required: ["replicas"]
          properties:
            replicas:
              type: "integer"
              minimum: 1
```

#### 3.2 create golang client
- define type
- define DeepCopy Method
> * Kubernetes API（在本例中为Project和ProjectList）提供的每种类型都需要实现该k8s.io/apimachinery/pkg/runtime.Object接口.
   该接口定义了两种方法GetObjectKind()和DeepCopyObject()。第一种方法已经由嵌入式metav1.TypeMeta结构提供; 第二个你必须自己实现。
- registry type
    schema.GroupVersion
    runtime.NewSchemeBuilder(addKnownTypes)
    SchemeBuilder.AddToScheme
    

#### 3.3 build http client


#### 4. informatoryFactory
