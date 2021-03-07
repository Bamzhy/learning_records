### some tips
- if you use virtualbox to install kubernetes nodes
    - you shut down the virtual machine
    - restart it
    - kubectl get nodes —— not ready
    - kubectl describe node master
        - NetworkUnavailable / MemoryPressure / DiskPressure ...
        - Kubelet stopped posting node status
- sudo swapoff -a
- systemctl restart kubelet
- check status of kubelet
    - systemctl status kubelet
        - Active: active (running)
    - journalctl -e -u kubelet
        - node bogon not found
- turn to hostname problem

### hostname problem
- a weird thing happend, the hostname changed
    - root@localhost ——> root@bogon
- get your ip address
    - ip addr
    - record your ip
- vim /etc/hosts
    - add a line
        - your-ip localhost
- restart

### use xargs to make file content into arguments for next orders
- rook.txt
    - https://github.com/rook/rook/blob/release-1.5/cluster/examples/kubernetes/ceph/cluster.yaml
    - https://github.com/rook/rook/blob/release-1.5/cluster/examples/kubernetes/ceph/operator.yaml
- cat rook.txt | head -n 1 | xargs kubectl apply -f
    - equals "kubectl apply -f https://github.com/rook/rook/blob/release-1.5/cluster/examples/kubernetes/ceph/cluster.yaml"
- be concerned about the line break problem (%0D)
    - do it each line if necessary
- it may failed due to download policy from github, but i did the right thing