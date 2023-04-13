# LAB 7: Study replica and replication controllers

Deploy POD with the help of replica and replication controllers.
• Check the replication controller manifest.
![image](https://user-images.githubusercontent.com/71546848/220204299-0bbe1e61-17a8-44e7-ac3b-4d661271c8f6.png)

• Create the replication controller using the replicationcontroller.yaml file.

• Check the replication controller status – 3 replica sets were created

• Check the node status.

• Check the pod status and they were running.

![image](https://user-images.githubusercontent.com/71546848/220204317-c34eee2e-ded3-4fc1-9c7c-7ab7de8d5466.png)

• Check the replication controller status and all 3 replicas were running.
![image](https://user-images.githubusercontent.com/71546848/220204375-81b1c899-211e-4bf0-a60f-264c2a713adf.png)

• All 3 pods were running

![image](https://user-images.githubusercontent.com/71546848/220204388-95139d8f-384b-41bf-a893-d7c2276cefa0.png)

• On node 1 login into the container created for the POD.
![image](https://user-images.githubusercontent.com/71546848/220204413-14b22152-104f-42d0-a365-f9b4dd2babc9.png)

• Check the IP for the container running inside the POD.
![image](https://user-images.githubusercontent.com/71546848/220204448-0fee616b-babf-4cd0-9f27-580781e62d71.png)

• I was able to access the iis application running on Pod from master node.
![image](https://user-images.githubusercontent.com/71546848/220204460-f51c668f-1861-4716-8088-ad3f1d5894a8.png)

• Scaling up the replicas
![image](https://user-images.githubusercontent.com/71546848/220204489-b5de65e5-d521-46e5-809a-6b8d59544078.png)

• Replicas scaled up to 6.
![image](https://user-images.githubusercontent.com/71546848/220204502-de8c93f0-ffa3-438e-8572-f1cfce81fb0b.png)

• Scaling down the replicas
![image](https://user-images.githubusercontent.com/71546848/220204522-4edb0511-98e5-4553-a65d-8c7a27f4886b.png)

• Replicas was scaled down to 2

![image](https://user-images.githubusercontent.com/71546848/220204534-cfceba0f-dfa2-49e9-b5da-af692db437e4.png)


Difference between Replica Set and Replication controller
![image](https://user-images.githubusercontent.com/71546848/226432483-d0ff3877-105c-43d1-b46f-d2ad263b85b7.png)
