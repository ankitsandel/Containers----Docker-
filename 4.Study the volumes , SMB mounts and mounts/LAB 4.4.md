# LAB 4.4 Study the difference between Volumes SMB mount and Bind mount .

**Volume SMB mount**

In container "SMB Global Mapping" makes it possible to mount a SMB share on the host, then pass 
directories on that share into a container. 

    $creds = Get-Credential 
    New-SmbGlobalMapping -RemotePath \\docker2\share1 -Credential $creds -LocalPath G: 
    
![image](https://user-images.githubusercontent.com/71546848/220203507-827fbdd7-129c-4ee2-a948-17d658d09c84.png)

The container doesn't need to be configured with a specific server, share, username or password -
that's all handled on the host instead. 
The container will work the same as if it had local storage. 

**Volume Bind mount**

Bind mounts allow a container to share a directory with the host. This is useful if you want a place to 
store files on the local machine that are available if you restart a container or want to share it with 
multiple containers. If you want the container to run on multiple machines with access to the same 
files, then a named volume or SMB mount should be used.

![image](https://user-images.githubusercontent.com/71546848/220203534-9c913e2e-fc30-4240-bfef-64c47d25f56f.png)
