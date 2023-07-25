# Steps to create a Linux Master

# Environment Details

        Hyper-v Host
        On top of Hyper-V host create 3 VM's
        1st VM will be a Linux Control plane VM
        2nd and 3rd VM will be Windows Worker nodes


# Prerequisites:

**Preparation:**

#Update the node

        sudo apt update
        sudo apt -y full-upgrade
        [ -f /var/run/reboot-required ] && sudo reboot -f

#Disable Swap
 
         sudo swapoff -a
         nano /etc/fstab
        Comment out "#" /swapfile
     
#Disable Linux SE (Security Enhanced Linux)
 
        setenforce 0
       
     
#The control-plane node is the machine where the control plane components run, including etcd (the cluster database) and the API Server (which the kubectl command line tool communicates with)
# 1. Enable kernel modules and configure sysctl.
    
       
       # Enable kernel modules
         sudo modprobe overlay
         sudo modprobe br_netfilter

         # Add some settings to sysctl
         Vi /etc/sysctl.d/kubernetes.conf 
         
  Add below lines in kubernetes.conf
  
         net.bridge.bridge-nf-call-ip6tables = 1
         net.bridge.bridge-nf-call-iptables = 1
         net.ipv4.ip_forward = 1
         

         # Reload sysctl
         sudo sysctl --system

       
 
 
# 2. Install kubelet, kubeadm and kubectl

Adding Kubernetes repository

        sudo apt install curl apt-transport-https -y
        curl -fsSL  https://packages.cloud.google.com/apt/doc/apt-key.gpg|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/k8s.gpg
        curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
        echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
        
Install required package

        sudo apt update
        sudo apt install wget curl vim git kubelet kubeadm kubectl -y
        sudo apt-mark hold kubelet kubeadm kubectl

Confirm installation by checking the version of kubectl.

        kubectl version --client && kubeadm version

# 3.  Install Container runtime 

# Install Docker 

#Add repo and Install packages

        sudo apt update
        sudo apt install -y curl gnupg2 software-properties-common apt-transport-https ca-certificates
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
        sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
        sudo apt update
        sudo apt install -y containerd.io docker-ce docker-ce-cli

#Create required directories

        sudo mkdir -p /etc/systemd/system/docker.service.d

#Create daemon json config file
        sudo tee /etc/docker/daemon.json <<EOF
        {
          "exec-opts": ["native.cgroupdriver=systemd"],
          "log-driver": "json-file",
          "log-opts": {
            "max-size": "100m"
          },
          "storage-driver": "overlay2"
        }
        EOF

#Start and enable Services

          sudo systemctl daemon-reload 
          sudo systemctl restart docker
          sudo systemctl enable docker

#Configure persistent loading of modules

          sudo tee /etc/modules-load.d/k8s.conf <<EOF
          overlay
          br_netfilter
          EOF

#Ensure you load modules
                                                     
          sudo modprobe overlay
          sudo modprobe br_netfilter

#Set up required sysctl params
                                                     
         Vi /etc/sysctl.d/kubernetes.conf 
         
Add below lines in kubernetes.conf
  
         net.bridge.bridge-nf-call-ip6tables = 1
         net.bridge.bridge-nf-call-iptables = 1
         net.ipv4.ip_forward = 1
                                                     
# Install ContainerD                                                     

#Reload configs

        sudo sysctl --system

#Install required packages

        sudo apt install -y curl gnupg2 software-properties-common apt-transport-https ca-certificates

#Add Docker repo

        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
        sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

#Install containerd

        sudo apt update
        sudo apt install -y containerd.io

#Configure containerd and start service

        sudo su -
        mkdir -p /etc/containerd
        containerd config default>/etc/containerd/config.toml

#restart containerd

        sudo systemctl restart containerd
        sudo systemctl enable containerd
        systemctl status containerd
                                                     
                                                     
# 4. Initialize control plane (run on first master node)

Login to the server to be used as master and make sure that the br_netfilter module is loaded:

        lsmod | grep br_netfilter

        sudo systemctl enable kubelet
        
Now initialize the machine that will run the control plane components which includes etcd (the cluster database) and the API Server.

#Pull container images:

        sudo kubeadm config images pull
                                                     
#Docker
                                                     
        sudo kubeadm config images pull --cri-socket /run/cri-dockerd.sock 
        
# 5. Bootstrap the control plane node 
        sudo kubeadm init  --pod-network-cidr=10.244.0.0/16
        
        
  Copy below output we will need this to join worker node.
  
  
       kubeadm join 10.0.0.17:6443 --token ldyz94.90d888brs5yja280 \
               --discovery-token-ca-cert-hash sha256:4d1317360d450622771db09f038ef6ae438623a590479266012a0b3
        
        
        
After successfully deploying control plane, node may go into NotReady state.
You will need to setup Networking on control plane node to fix the issue.
You can use flannel or calico depending on your choise.
        
        
