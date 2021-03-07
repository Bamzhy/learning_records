### use kubeadm to install kubernetes
- apt-get install kubeadm
- kubeadm init
    - Preflight Checks
        - Check Linux kernel version (above version 3.10)
        - Whether Cgroups provides
        - Whether the working ports 10250/10251/10252 are ocuppied
        - Whether ip/ mount order exist
        - Whether the host
        - name of the machine is standard
        - ...
    - Generate certificates
        - /etc/kubernets/pki/ca.crt && ca.key
        - apiserver-kubelet-client.crt ...
        - ...
    - Generate config file for other components
        - admin.conf
        - controller-mananger.conf
        - kubelet.conf
        - scheduler.conf
    - Generate pod yaml
        - /etc/kubernets/manifests
            - kube-apiserver.yaml
            - etcd.yaml
            - kube-controller-manager.yaml
            - kube-scheduler.yaml
    - Init Pod from yaml files above
        - Check localhost:6443/healthz
        - Wait for these components to start
        - Generate a bootstrap token
        - Install kube-proxy and DNS

### kubeadm join
- when kubeadm init finished and bootstrap token is generated
- you can execute kubeadm join in any machine with kubelet and kubeadm installed

### procedure
- CentOS version
    - CentOS-7-x86_64-Minimal-2009.iso
- VirtualBox version
    - VirtualBox-6.1.16-140961-Win.exe
- yum install kubeadm ( if failed, change the yum source to aliyun)
- kubeadm config print init-defaults | less
    - apiVersion:kubeadm.k8s.io/v1beta2
    - kind:InitConfiguration
    - kubernetesVersion: v1.20.0
- kubeadm init --config kubeadm.yaml
    - if you located in a country which owned an Internet Firewall (like China), and k8s.gcr.io is blocked, you should choose local repository
- this maybe an efficent way to initialize
    - kubeadm init --image-repository=registry.aliyuncs.com/google_containers > abc.txt

- put config file to .kube
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```
- kubectl get nodes
    - the status of master node is 'NotReady'
    - kubectl describle node master | more
        - runtime network not ready: ....
    - we need to install network plugin
    - kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
    - kubectl get pods --all-namespaces -l name=weave-net
        - due to network problem, the status is ImagePullBackOff
        - check it
            - kubectl describe pod weave-net-g5k78 --namespace=kube-system
            - you should specify the namespace
    - check all pods' status
        - kubectl get pods --namespace=kube-system

- untaint the master node
    - kubectl taint nodes --all node-role.kubernetes.io/master-

- kubectl apply -f https://kuboard.cn/install-script/k8s-dashboard/v2.0.0-beta5.yaml
    - or wget  -O https://kuboard.cn/install-script/k8s-dashboard/v2.0.0-beta5.yaml dashboard.yaml
    - kubectl apply -f dashboard.yaml
    - 


### coredns not ready
- install weave first

## install rook
- cluster
    - kubectl apply -f  https://github.com/rook/rook/blob/release-1.5/cluster/examples/kubernetes/ceph/cluster.yaml
- operator
    - kubectl apply -f  https://github.com/rook/rook/blob/release-1.5/cluster/examples/kubernetes/ceph/operator.yaml

