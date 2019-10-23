# helm 入门实践

## 下载二进制文件
echo "Helm由客户端命helm令行工具和服务端tiller组成，Helm的安装十分简单。 下载helm命令行工具到master节点"
```
wget https://storage.googleapis.com/kubernetes-helm/helm-v2.15.0-linux-amd64.tar.gz
tar -zxvf ../soft_package/helm-v2.15.0-linux-amd64.tar.gz
mv -f ./linux-amd64/helm /usr/local/bin/
rm -rf ./linux-amd64
```


## 创建RBAC角色
```
echo "apiVersion: v1
kind: ServiceAccount
metadata:
  name: tiller
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
  name: tiller
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
  - kind: ServiceAccount
    name: tiller
    namespace: kube-system" > tiller_rbac.yaml
```

```
kubectl create -f tiller_rbac.yaml
```

## 创建 tiller deployment
```
helm init --service-account tiller --skip-refresh -i registry.cn-hangzhou.aliyuncs.com/launcher/tiller:v2.15.0
```


## 使用默认仓库创建应用
```
helm repo list
helm search redis
helm install stable/redis
```
复杂点的
```
# 5.dashboard
# 当使用Ingress将HTTPS的服务暴露到集群外部时，需要HTTPS证书，这里将*.frognew.com的证书和秘钥配置到Kubernetes中。
# 后边部署在kube-system命名空间中的dashboard要使用这个证书，因此这里先在kube-system中创建证书的secret
kubectl create secret tls frognew-com-tls-secret --cert=/etc/kubernetes/pki/ca.crt --key=/etc/kubernetes/pki/ca.key -n kube-system
helm del --purge kubernetes-dashboard
cat <<EOF > kubernetes-dashboard.yaml
ingress:
  enabled: true
  hosts:
  annotations:
    nginx.ingress.kubernetes.io/ssl-redirect: "true"
    nginx.ingress.kubernetes.io/secure-backends: "true"
  tls:
    - secretName: frognew-com-tls-secret
      hosts:
rbac:
  clusterAdminRole: true
EOF

helm install ./charts/stable/kubernetes-dashboard \
-n kubernetes-dashboard \
--namespace kube-system  \
-f kubernetes-dashboard.yaml

```


## 创建私有charts 仓库
```
yum install supervisor -y

cat  <<EOF> /etc/supervisord.d/helm-server.ini
[program:helm]
command = helm serve --address 0.0.0.0:8881 --repo-path /data/loca-char-repo
autostart = true
autorestart = true
user = root
startretries = 3
stdout_logfile_maxbytes = 20MB
stdout_logfile_maxbytes = 10
stdout_logfile = /var/log/helm.log
EOF

systemctl restart supervisord

mkdir -p /data/loca-char-repo

```

## 在私有helm 仓库添加应用
```
cd /data/loca-char-repo
helm create myapp
helm lint ./myapp
helm package myapp/
helm repo index --url=http://xxxxx:8881 .

## 官方示例git clone https://github.com/XishengCai/charts.git
```



## helm 通过私有仓库创建应用
```
helm repo add local-repo http://xxxx:8881
helm update
helm search redis
helm install local-repo/myapp
```

