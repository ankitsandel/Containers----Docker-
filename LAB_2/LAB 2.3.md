# LAB 2.3 Study /assess the different between process and Hyper-V isolation

There are two modes of isolation in Windows Container: 
1. Process Isolation (which is by default in Windows Container) – Sharing Host kernel
![image](https://user-images.githubusercontent.com/71546848/220199908-b59d35c2-aafd-4f28-94b0-1e741529592b.png)

2. Hyper-V Isolation – It has its own kernel, managed within worker process (VMWP).
![image](https://user-images.githubusercontent.com/71546848/220200032-bf8c303d-d67c-48ea-96c4-4b4bee8e2a26.png)

The levels of Isolation in Windows Container are: 
1. Process 
I ran ping process inside the container and as in process isolation container shares the kernel of Host 
so we can see PID 5364 for the container is reflecting on Host.

In 'Process Isolation', all the process running with Job object ID: 676 are Container Process.
![image](https://user-images.githubusercontent.com/71546848/220200065-0d150158-9398-4de6-beea-a94798eb97c8.png)

2. Network 
The Host Network and container network is isolated, container has the IP from the IP range assigned 
by NAT.
![image](https://user-images.githubusercontent.com/71546848/220200114-40a049a0-abc8-4777-9c04-f7ece2d5126d.png)

3. Environment Variable 
Host and container will have their separate environment Variables.
![image](https://user-images.githubusercontent.com/71546848/220200136-3b2f2452-b2a5-4709-8f71-7d8674c2688b.png)

4. Windows Registry 
Host and container will have their separate Windows Registries.
![image](https://user-images.githubusercontent.com/71546848/220200162-226037a8-3e67-4220-adaf-7a5d8b855620.png)

5. File System 
Host and container will have their separate File system for OS.
![image](https://user-images.githubusercontent.com/71546848/220200180-901940c5-3a1f-4b9f-bdec-edbf22cd5d57.png)

6. Storage 
We can see after creating the containers few virtual drives are created. 
![image](https://user-images.githubusercontent.com/71546848/220200202-4ef32952-0e0f-4cc6-acae-9f19512abff4.png)

7. Local Users & Groups
I have created the ankhost user on Host and ankcont use on container and we can see that both are isolated. 
![image](https://user-images.githubusercontent.com/71546848/220200275-4708e414-4a08-438b-a5c0-1f4bab3b2870.png)
