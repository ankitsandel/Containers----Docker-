# Steps to add a Windows Node 
#Perquisite :
1. Enable Nested Virtualization and MAC-Spoofing for Windows Node.
2. Get-VMNetworkAdapter -VMName "<name>" | Set-VMNetworkAdapter -MacAddressSpoofing On
3. Set-VMProcessor -VMName "<name>" -ExposeVirtualizationExtensions $true
  --
  
1.  Install Container feature from Server Manager
  
    Install Container Feature from Add and Remover (Server Manager)
  
# 2. Install Docker 

    [Net.ServicePointManager]::SecurityProtocol = "tls12, tls11, tls"
         Install-Module -Name DockerMsftProvider -Repository PSGallery -Force
# Docker 19.03.5 DockerDefault Contains Docker EE for use with Windows Server.
# 3. Start Docker Service 
net start docker
# 4. Crete C:\k folder for storing Kubernetes Binaries, Cluster Configuration and Kubernetes Components 
(Kubelet, Kubectl, kubeadm and kube-proxy)
mkdir C:\k
# Download kube Config file from Linux Master to Windows Node using winsc
