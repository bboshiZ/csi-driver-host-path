1. 默认安装daemonset csi-hostpathplugin 到kube-systerm命名空间下，挂载主机目录 /data/logs
2. 镜像地址配置在deploy/kubernetes-1.21/hostpath/csi-hostpath-plugin.yaml，默认使用registry.ushareit.me/sgt/hostpathplugin:v1.8.1，可根据环境修改


### Install
bash deploy/kubernetes-1.21/deploy.sh

#### Uninstall
bash deploy/kubernetes-1.21/destroy.sh


#### 使用方式

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: sleep
spec:
  replicas: 2
  selector:
    matchLabels:
      app: sleep
  template:
    metadata:
      labels:
        app: sleep
      annotations:
    spec:
      terminationGracePeriodSeconds: 0
      containers:
      - name: sleep
        image: busybox
        command: ["/bin/sleep", "3650d"]
        imagePullPolicy: IfNotPresent
        volumeMounts:
        - mountPath: "/data"
          name: my-csi-volume
      volumes:
        - name: my-csi-volume
          csi:
            driver: hostpath.csi.k8s.io

```