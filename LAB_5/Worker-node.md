# Steps to add a Windows Node 

#Perquisite :

a. Enable Nested Virtualization and MAC-Spoofing for Windows Node.

     Get-VMNetworkAdapter -VMName "<name>" | Set-VMNetworkAdapter -MacAddressSpoofing On

     Set-VMProcessor -VMName "<name>" -ExposeVirtualizationExtensions $true
  
  --
  
1.  Install Container feature from Server Manager
  
     Install Container Feature from Add and Remover (Server Manager)
  
2. Install Docker 

    [Net.ServicePointManager]::SecurityProtocol = "tls12, tls11, tls"
    Install-Module -Name DockerMsftProvider -Repository PSGallery -Force

3. Start Docker Service 
  
    net start docker
  
4. Crete C:\k folder for storing Kubernetes Binaries, Cluster Configuration and Kubernetes Components (Kubelet, Kubectl, kubeadm and kube-proxy)

    mkdir C:\k
  
  #Download kube Config file from Linux Master to Windows Node using winscp
  ![image](https://user-images.githubusercontent.com/71546848/220454758-332bdc1b-e0c9-4560-8aef-ece78985d78a.png)

  #Downloading the files to c:\k. âkâ folder should contain below files:
  ![image](https://user-images.githubusercontent.com/71546848/220454885-0830c8f0-57ae-4249-9d1b-af504eb84ec0.png)

5. Set Environment variable for kubectl
 
     $env:Path += ";C:\k"
     [Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\k", 
     [EnvironmentVariableTarget]::Machine)
     $env:KUBECONFIG="C:\k\config"
     [Environment]::SetEnvironmentVariable("KUBECONFIG", "C:\k\config", 
     [EnvironmentVariableTarget]::User)
  
   #Check kubctl configuration:
 
     kubectl config view

6. Download the Flannel start.ps1 script

    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
    wget https://raw.githubusercontent.com/Microsoft/SDN/master/Kubernetes/flannel/start.ps1 -o c:\k\start.ps1
  
7. Run following command to 'Join Node' to the Kubernetes Cluster

    .\start.ps1 -ManagementIP <Windows_node_ip> -NetworkMode overlay -ClusterCIDR 10.244.0.0/16 -ServiceCIDR 10.96.0.0/12 -KubeDnsServiceIP 10.96.0.10 -LogDir C:\k -interface Ethernet
