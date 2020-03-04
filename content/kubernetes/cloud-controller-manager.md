### aliyun-ccm log
```shell script
I0303 01:37:55.464314       1 leaderelection.go:199] successfully renewed lease kube-system/cloud-controller-manager
I0303 01:37:56.327291       1 reflector.go:286] k8s.io/cloud-provider-alibaba-cloud/vendor/k8s.io/client-go/informers/factory.go:86: forcing resync
I0303 01:37:57.472805       1 leaderelection.go:199] successfully renewed lease kube-system/cloud-controller-manager
I0303 01:37:58.908233       1 alicloud.go:343] alicloud: ListRoutes 
debug: find endpoint from local cache: https://ecs-cn-hangzhou.aliyuncs.com
I0303 01:37:59.034271       1 route_controller.go:141] ListRoutes: reconcile &{Name:cn-hangzhou.i-bp18n08n4vnige2ekx8e TargetNode:cn-hangzhou.i-bp18n08n4vnige2ekx8e DestinationCIDR:10.200.4.0/24 Blackhole:false}
I0303 01:37:59.034305       1 route_controller.go:141] ListRoutes: reconcile &{Name:cn-hangzhou.i-bp1ab9p10tmhqi641wzw TargetNode:cn-hangzhou.i-bp1ab9p10tmhqi641wzw DestinationCIDR:10.200.0.0/24 Blackhole:false}
I0303 01:37:59.034324       1 route_controller.go:178] Node: cn-hangzhou.i-bp18n08n4vnige2ekx8e, r=&{Name:cn-hangzhou.i-bp18n08n4vnige2ekx8e TargetNode:cn-hangzhou.i-bp18n08n4vnige2ekx8e DestinationCIDR:10.200.4.0/24 Blackhole:false}, node.Spec.PodCIDR=10.200.4.0/24
I0303 01:37:59.034335       1 route_controller.go:178] Node: cn-hangzhou.i-bp1ab9p10tmhqi641wzw, r=&{Name:cn-hangzhou.i-bp1ab9p10tmhqi641wzw TargetNode:cn-hangzhou.i-bp1ab9p10tmhqi641wzw DestinationCIDR:10.200.0.0/24 Blackhole:false}, node.Spec.PodCIDR=10.200.0.0/24
I0303 01:37:59.479468       1 leaderelection.go:199] successfully renewed lease kube-system/cloud-controller-manager

```
### huawei-ccm logs
```shell script
W0303 09:24:30.338382   12459 authentication.go:267] No authentication-kubeconfig provided in order to lookup client-ca-file in configmap/extension-apiserver-authentication in kube-system, so client certificate authentication won't work.
W0303 09:24:30.338409   12459 authentication.go:291] No authentication-kubeconfig provided in order to lookup requestheader-client-ca-file in configmap/extension-apiserver-authentication in kube-system, so request-header client certificate authentication won't work.
W0303 09:24:30.338423   12459 authorization.go:146] No authorization-kubeconfig provided, so SubjectAccessReview of authorization tokens won't work.
I0303 09:24:30.341065   12459 controllermanager.go:120] Version: v0.0.0-master+$Format:%h$
I0303 09:24:30.341404   12459 huawei.go:225] Config, loaded from the config file:
I0303 09:24:30.950314   12459 healthz.go:123] Installing health checkers for (/healthz): "leaderElection"
I0303 09:24:30.951077   12459 tlsconfig.go:179] loaded serving cert ["Generated self signed cert"]: "localhost@1583198669" [serving] validServingFor=[127.0.0.1,localhost,localhost] issuer="localhost-ca@1583198669" (2020-03-03 00:24:29 +0000 UTC to 2021-03-03 00:24:29 +0000 UTC (now=2020-03-03 01:24:30.951059362 +0000 UTC))
I0303 09:24:30.951270   12459 named_certificates.go:52] loaded SNI cert [0/"self-signed loopback"]: "apiserver-loopback-client@1583198670" [serving] validServingFor=[apiserver-loopback-client] issuer="apiserver-loopback-client-ca@1583198670" (2020-03-03 00:24:29 +0000 UTC to 2021-03-03 00:24:29 +0000 UTC (now=2020-03-03 01:24:30.951259892 +0000 UTC))
I0303 09:24:30.951294   12459 secure_serving.go:178] Serving securely on [::]:10258
I0303 09:24:30.951321   12459 leaderelection.go:242] attempting to acquire leader lease  kube-system/cloud-controller-manager...
I0303 09:24:30.951464   12459 tlsconfig.go:219] Starting DynamicServingCertificateController

```