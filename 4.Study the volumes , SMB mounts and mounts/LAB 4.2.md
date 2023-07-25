# LAB 4.2 Create a SMB mount and attach to a container

• On the container host, globally map the remote SMB share:
![image](https://user-images.githubusercontent.com/71546848/220202953-d42ce843-cbb4-422f-ad58-c59daac13c76.png)

• Create the mapping on container host of the remote path as local path G.
![image](https://user-images.githubusercontent.com/71546848/220202970-7f353ce8-8024-48c4-b0b9-09a104dff328.png)

• Create the folder inside the G drive.
![image](https://user-images.githubusercontent.com/71546848/220203010-fee2a28b-68bf-4cc3-98e2-3980f8e36694.png)

• Map the folder inside the G drive with the container.
![image](https://user-images.githubusercontent.com/71546848/220203082-8f7076bf-2d1c-4761-ad92-6a598cd54c9e.png)

• Inside the container, G:\containerdata will then be mapped to the remote share’s 
"SMBmount" directory. Any data stored on globally mapped remote share will be available to 
applications inside the container. Multiple containers can get read/write access to this shared 
data with the same command.

• I validated the data created inside the container reflecting on containerdata folder and on SMBMount.

![image](https://user-images.githubusercontent.com/71546848/220203114-bc12ea25-32de-4594-807d-fdd03fc19ba8.png)
![image](https://user-images.githubusercontent.com/71546848/226448817-1f6213bd-264a-4be3-9250-56f985c5f6be.png)
