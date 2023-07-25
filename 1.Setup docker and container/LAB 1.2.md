# LAB 1.2 Pull any image from docker hub and deploy it.




• Check the status of the deployed container image
![image](https://user-images.githubusercontent.com/71546848/220198604-93ffbb96-58e5-4631-acfb-cf2139909d0d.png)

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
[
    {
        "Id": "0bbb49135bb1772f1592814c8233dbc2c9c662a2db1ecdfd6aed69ed566eee01",
        "Created": "2023-06-05T19:06:34.3068095Z",
        "Path": "c:\\windows\\system32\\cmd.exe",
        "Args": [],
        "**State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,**
            "Pid": 5168,
            "ExitCode": 0,
           ** "Error": "",**
            "StartedAt": "2023-06-05T19:06:35.2053806Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:66a1a48cbc112ec01f8af22153b50e4d1a0e8b74e190594222ef9d3b0d4a7b9b",
        "ResolvConfPath": "",
        "HostnamePath": "",
        "HostsPath": "",
        "LogPath": "C:\\ProgramData\\docker\\containers\\0bbb49135bb1772f1592814c8233dbc2c9c662a2db1ecdfd6aed69ed566eee01\\0bbb49135bb1772f1592814c8233dbc2c9c662a2db1ecdfd6aed69ed566eee01-json.log",
        "Name": "/testcont",
        "RestartCount": 0,
       "Driver": "windowsfilter",
        "Platform": "windows",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                43,
                178
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
           "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 0,
        **    "Isolation": "process",**
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": null,
            "ReadonlyPaths": null
        },
        "GraphDriver": {
            "Data": {
                "dir": "C:\\ProgramData\\docker\\windowsfilter\\0bbb49135bb1772f1592814c8233dbc2c9c662a2db1ecdfd6aed69ed566eee01"
            },
            "Name": "windowsfilter"
        },
        "Mounts": [],
        "Config": {
           ** "Hostname": "0bbb49135bb1",**
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": true,
            "OpenStdin": true,
            "StdinOnce": false,
            "Env": null,
            "Cmd": [
                "c:\\windows\\system32\\cmd.exe"
            ],
          **  "Image": "mcr.microsoft.com/windows/servercore:ltsc2019",**
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "0bbb49135bb1772f1592814c8233dbc2c9c662a2db1ecdfd6aed69ed566eee01",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {},
            "SandboxKey": "0bbb49135bb1772f1592814c8233dbc2c9c662a2db1ecdfd6aed69ed566eee01",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "",
            "Gateway": "",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "",
            "IPPrefixLen": 0,
            "IPv6Gateway": "",
            "MacAddress": "",
            "Networks": {
                "nat": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "cf324197a116016275dc79593fe3071a0360ea26f6ee0bdd1e3291558f835aea",
                    "EndpointID": "bd8d4e97588934037ec91634914b766f889da434655db78e75c0d43d208a9935",
                    "Gateway": "172.18.112.1",
                    **"IPAddress": "172.18.122.157",**
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "00:15:5d:b3:1f:a7",
                    "DriverOpts": null
                }
            }
        }
    }
]
PS C:\Users\Ankit>


Got to any web browser and enter: IP address of container -- <Ip address of container>: <Container Port>
