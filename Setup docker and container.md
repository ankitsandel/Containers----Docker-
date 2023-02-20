# LAB 1-- Setup docker and container

LAB 1.1 Pre-requisites for docker installation
For Windows Server OS

    1. Physical Server or Virtual Machine – running with WS2016, WS2019 or WS2022.
    2. For Windows OS (Windows 10 & Windows 11)
    One physical computer system running Windows 10 Professional or Enterprise with Anniversary Update (version 1607) or later. 
    3. Hyper-V feature should be enabled. 
    
System Requirements for Windows Containers: 
OS Requirements: 

    • The Windows container feature is only available on Windows Server 2016 (Core and with 
    Desktop Experience), Windows 10 Professional and Enterprise (Anniversary Edition) and later. 
    • The Hyper-V role must be installed before running Hyper-V Containers. 
    • Windows Server Container hosts must have Windows installed to C:. This restriction does not 
    apply if only Hyper-V Containers will be deployed. 
    
Virtualized Container Hosts: 
If a Windows container host will be run from a Hyper-V virtual machine, and will also be hosting HyperV Containers, nested virtualization will need to be enabled. Nested virtualization has the following 
requirements: 

    • At least 4 GB RAM available for the virtualized Hyper-V host. 
    • Windows Server 2019, Windows Server version 1803, Windows Server version 1709, Windows 
    Server 2016, or Windows 10 on the host system, and Windows Server (Full, Core) in the virtual 
    machine. 
    • A processor with Intel VT-x (this feature is currently only available for Intel processors). 
    • The container host VM will also need at least 2 virtual processors. 
    
Memory Requirements: 
![image](https://user-images.githubusercontent.com/71546848/220198239-ff1c35f7-4be4-4021-a3db-c150cfed82fb.png)


• Checking the prerequisites on Windows Server 2019 OS.

![image](https://user-images.githubusercontent.com/71546848/220197925-d65167cf-318a-453d-81eb-02170a2aa8e6.png)

• Checking the Docker Version 

![image](https://user-images.githubusercontent.com/71546848/220197954-cb0f2e12-ec60-4d33-a0dd-2c00de2574fd.png)

• Checking Docker Info

![image](https://user-images.githubusercontent.com/71546848/220197986-821d00bc-1f4a-4430-b94d-4e32336a3702.png)

