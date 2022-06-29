1. 默认安装daemonset csi-hostpathplugin 到kube-systerm命名空间下，挂载主机目录 /data/logs
2. 镜像地址配置在deploy/kubernetes-1.21/hostpath/csi-hostpath-plugin.yaml，默认使用registry.ushareit.me/sgt/hostpathplugin:v1.8.1，可根据环境修改


### Install
bash deploy/kubernetes-1.21/deploy.sh

#### Uninstall
bash deploy/kubernetes-1.21/destroy.sh