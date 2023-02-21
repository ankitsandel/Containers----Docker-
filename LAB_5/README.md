# Steps to create a Linux Master

#Prerequisites:
#Preparation:

#Disable Swap
 
     sudo swapoff -a
     Nano /etc/fstab
     Comment out "#" /swapfile
     
# Disable Linux SE (Security Enhanced Linux)
 
     Setenforce 0
     Sed -I 's/enforcing/disabled/g' /etc/selinux/config
     Grep disabled /etc/selinux/config | grep -v '#'
     
#The control-plane node is the machine where the control plane components run, including etcd (the cluster database) and the API Server (which the kubectl command line tool communicates with)
# 1. Configure Linux Node's iptables to correctly see bridged traffic, ensure net.bridge.bridge-nf-call iptables is set to 1 in sysctl config
    
        ---
        cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
        net.bridge.bridge-nf-call-ip6tables = 1
        net.bridge.bridge-nf-call-iptables = 1
        EOF
        sudo sysctl --system
        ---
 
 
# 2. Add Google's apt repository gpg key

        ---
        sudo apt-get update && sudo apt-get install -y apt-transport-https curl
        curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
        #Add the Kubernetes apt repository
        cat <<EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list
        deb https://apt.kubernetes.io/ kubernetes-xenial main
        EOF
        ---
        
       # Update the package list
       sudo apt-get update
       
# 3. Install following packages Docker, kubelet, kubeadm and kubectl
 
        sudo apt-get install -y docker.io kubelet kubeadm kubectl kubernetes-cni
        
 #Check the status of our kubelet and our container runtime, docker
 
    sudo systemctl status kubelet.service
    sudo systemctl status docker.service
    
 # Ensure both are set to start when the system starts up
 
    sudo systemctl enable kubelet.service
    sudo systemctl enable docker.service
    
Note: We no longer wants 'apt' to maintain the upgrade of these packages rather depends on Kubernetes to maintain its own updates 

        sudo apt-mark hold kubelet kubeadm kubectl
        
#Note: Kublet Config files: /var/lib/kubelet/config.yaml

# 4. Restart Kubelet

       systemctl daemon-reload
       systemctl restart kubelet
 
# 5. Install a single control-plane Kubernetes cluster

1. To initialize the control-plane node run:
    
        sudo kubeadm init --pod-network-cidr=10.240.0.0/16
      
2. To make kubectl work for your nonroot user, run these commands, which are also part of the kubeadm init output:
 
       mkdir -p $HOME/.kube
       sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
       sudo chown $(id -u):$(id -g) $HOME/.kube/config
       
# Alternatively, if you are the root user, you can run: export KUBECONFIG=/etc/kubernetes/admin.conf
---

3. Install a Pod network on the cluster so that Pods can talk to each other

 A. Download & configure Flannel
 
    sudo wget https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kubeflannel.yml
 B. Modify net-conf.json, edit Type: "host-gw"
 
       # net-conf.json section
       # Add following tags
       "Type": "host-gw"
      # This is how net-conf.json should look like
       net-conf.json: |
       {
       "Network": "10.244.0.0/16",
       "Backend": {
       "Type": "host-gw"
       }
       }
      --
      
      
# 4. Apply the Flannel yaml and Validate

    kubectl apply -f kube-flannel.yml
    
a. Validate Flannel Pod Network
    
    PS C:\k> kubectl get pods --all-namespaces

    # Check the status of Kubernetes Cluster Nodes
    PS C:\k> kubectl get node -o wide
