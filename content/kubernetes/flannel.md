---
title: "Network Policy"
date: 2019-12-11T22:50:21+08:00
draft: false
---

# node 间的网络访问
---
1.udp

    node-A               node-B
    containerA           containerB
      |                     |
    cni0                 cni0
      |                     |
    flannel.1            flannel.1
      |                     |
    flanneld             flanneld
      |                     |
    eth0      --------->   eht0

cni0 网桥

    1. Frame     Mac                           IP    Message
                 containerA mac
                 Destination: node-B cni0Mac
             
             
2.VXLAN


3.host-gw

[IPpub blog](http://blog.itpub.net/28218939/viewspace-2640884/)