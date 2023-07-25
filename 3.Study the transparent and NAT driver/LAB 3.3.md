# LAB 3.3 Study the difference between NAT and transparent network.
**NAT network:** 

1. When we install Docker, it creates a Hyper-V switch on the local host with scope:local
![image](https://user-images.githubusercontent.com/71546848/220201050-e79310d1-770a-402c-be6f-8a5e1d1f1b87.png)

2. Containers attached to a network created with the ‘NAT’ driver will be connected to an internal 
Hyper-V switch 
3. The default internal IP prefix used for ‘NAT’ is 172.16.0.0/16 
4. 2nd Nat network is not supported in Windows Server 2016, but we can create 2nd NAT network in 
Windows Server 2019. 
5. After the Container Host is Rebooted, 2nd NAT network is deleted. 
Containers attached to the 2nd NAT network will failed to start with error messages,

Solution: Disconnect the Container from 2nd NAT Network 
docker network disconnect <2nd NAT_Network-Name> <Container-Name>

  ![image](https://user-images.githubusercontent.com/71546848/220201074-6a58ef79-a10c-4f2e-80ed-ce58b28f84e3.png)

**Transparent network:**
  
Containers attached to a network created with the 'transparent' driver will be directly connected to 
the physical network through an external Hyper-V switch.
IPs from the physical network can be assigned statically or dynamically using an external DHCP server. 
When this mode is used in a virtualization scenario (container host is a VM) MAC address spoofing is 
required.
  
• Create the network driver for trans
  ![image](https://user-images.githubusercontent.com/71546848/220201150-61abdb99-2d0b-4c29-8f62-64029c156965.png)
