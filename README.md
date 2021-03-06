# 将 gcr.k8s.io 中 kubeadm 使用的镜像同步至阿里云

## 新版本镜像提交说明(二选一)

### ISSUE

新建issue并标明新增k8s版本及通过 ` kubeadm config images list` 获取的 kubeadm 使用镜像列表

### PR 

在 images 目录中以 kubenetes 版本号为文件名称新建镜像配置文件，格式说明：
1. 文件内容按镜像名称按行分割，每行格式为： `<镜像名称>=<标签名称(版本)>`
2. 若镜像名称中包含 `-` ，请使用 `_` (下划线) 代替

具体格式可以参考 [v1.22.2](./images/v1.22.2)

## 镜像使用方式

在 kubeadm 中通过 `--image-repository` 指定镜像地址 `registry.cn-beijing.aliyuncs.com/gcr-k8s-mirror`, 示例如下：

```
kubeadm init --apiserver-advertise-address="192.168.50.10" --apiserver-cert-extra-sans="192.168.50.10"  --node-name k8s-master --pod-network-cidr=192.168.0.0/16 --image-repository registry.cn-beijing.aliyuncs.com/gcr-k8s-mirror
```