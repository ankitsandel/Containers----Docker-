# LAB 1.2 Pull any image from docker hub and deploy it.

• Pull an image using pull command from Docker Hub https://hub.docker.com/: **docker pull <image_name>:<tag>**

![image](https://user-images.githubusercontent.com/71546848/220198499-04ee766e-158a-4e32-a254-5532c777264f.png)

    Example: 
    PS C:\Users\Ankit> docker pull mcr.microsoft.com/windows/servercore:ltsc2019
    ltsc2019: Pulling from windows/servercore
    8185ee4ed646: Already exists
    d1629109497f: Pull complete
    Digest: sha256:12c61b7da616ca0065030ada32e78ba5bea0a1721affd994f40736b9b48620ae
    Status: Downloaded newer image for mcr.microsoft.com/windows/servercore:ltsc2019
    mcr.microsoft.com/windows/servercore:ltsc2019

Validate the image: docker images

• Create a container: **docker run -it -d  --name=<name_of_container> <image_name>:<image_tag>**

![image](https://user-images.githubusercontent.com/71546848/220198522-0ff85907-103f-4a8e-b16f-0a2e7ee14ff4.png)

    Example:
    PS C:\Users\Ankit> docker run -it -d --name=testcont mcr.microsoft.com/windows/servercore:ltsc2019
    0bbb49135bb1772f1592814c8233dbc2c9c662a2db1ecdfd6aed69ed566eee01    Container is created with name testcont

• Display the list of running containers: **docker ps / docker container ls **
Above command lists existing docker containers in running state. 
ps stands for “Process Status”

• Dislpay list of all the containers (Includes running/stopped/Exited) :** docker ps -a / docker container ls –all**

• Login into a container: **docker exec -it <Container_Name> Powershell or docker exec -it <container_name> cmd**

![image](https://user-images.githubusercontent.com/71546848/220198564-f08c0041-d063-49af-84f1-47d9d1d54ac9.png)

• Run hostname, ipconfig /all inside the container to confirm if you are inside the container. 

• Run hostname, ipconfig /all on the host and compare.

• Run Exit command to get out off container

• Inspect a container: **docker container inspect <container_name> / docker inspect <container_name>**

    PS C:\Users\Ankit> docker inspect 0bbb49135bb1
        

• Got to any web browser and enter: IP address of container -- <Ip address of container>: <Container Port>

![image](https://user-images.githubusercontent.com/71546848/220198604-93ffbb96-58e5-4631-acfb-cf2139909d0d.png)

