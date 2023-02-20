# LAB3 -- Study the transparent and NAT driver.

LAB 3.1 Deploy a transparent network to a container
Containers attached to a network created with the 'transparent' driver will be directly connected to 
the physical network through an external Hyper-V switch. 
IPs from the physical network can be assigned statically or dynamically using an external DHCP server. 
When this mode is used in a virtualization scenario (container host is a VM) MAC address spoofing is 
required.
• Create the network driver for transparent network.
![image](https://user-images.githubusercontent.com/71546848/220200464-ff8a4aba-9376-49a0-bdfe-7888e2fac9ab.png)

• List the network present for containers
![image](https://user-images.githubusercontent.com/71546848/220200487-05aeece2-5134-44a4-b3a0-5fe807bfcc13.png)

• On Hyper-V Host – Enable MAC Spoofing
![image](https://user-images.githubusercontent.com/71546848/220200499-f649eb06-c20e-4297-862f-e3f9a150645f.png)

• Deploy a container with Transparent Network
![image](https://user-images.githubusercontent.com/71546848/220200523-aaa7a24b-8952-459d-9e50-b1877cad67f9.png)

• Run a container with Transparent Network
I was able to access bing.com from the container

![image](https://user-images.githubusercontent.com/71546848/220200548-05780570-b451-4358-928c-69c6b4cd5b9c.png)
