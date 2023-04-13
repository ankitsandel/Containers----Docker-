# LAB 8 --Study daemonSet controllers

Daemon set: 

    1. A pod copy is present on each worker node. 
    2. If we have 2 worker nodes and we used daemon set then it will create 2 Pods, 1 each on worker node. 
    3. If one more node is added then, it will deploy one Pod on Node-3. 
    4. If Node-3 is decommissioned from k8s cluster then Pod running on that node will be garbage collected.

• Check the node, pod status – no pod was running
![image](https://user-images.githubusercontent.com/71546848/220204754-7af8c289-0aa9-4b02-bec7-6774c2de54d6.png)

• Check the manifest yaml file for Daemonset.
![image](https://user-images.githubusercontent.com/71546848/220204829-01fe9656-19a7-4a24-8ddd-93d2857ff8dc.png)

• Create the controller for DaemonSet.

• All nodes has the copy of pod running on them.
![image](https://user-images.githubusercontent.com/71546848/220204850-7d1038d2-e071-4dbf-bef3-f79f8e742073.png)

• Check the daemonset
![image](https://user-images.githubusercontent.com/71546848/220204913-67d5cc99-7236-4e91-9194-9370e233373a.png)

• Turning off one worker node – node 2.
• Daemonset reduced to 1 and pod running on node 2 was garbage collected.
![image](https://user-images.githubusercontent.com/71546848/220204925-81228ff2-4798-49d7-b9ce-2f5637613e93.png)
