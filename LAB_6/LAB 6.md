# LAB 6 Study deployment controller

Deploy POD with the help of deployment controllers

• Check the cluster status
![image](https://user-images.githubusercontent.com/71546848/220203764-9992af94-9e71-469c-ab75-cd423463bddf.png)

• Deployment manifest
![image](https://user-images.githubusercontent.com/71546848/220203779-81c86432-7db0-476d-baaf-5cab5fddde47.png)

• Deploying the POD by using deployment controller Yaml file.
![image](https://user-images.githubusercontent.com/71546848/220203811-009afdb4-5042-490e-b615-293104ca6ddc.png)

• Check the Deployment status
![image](https://user-images.githubusercontent.com/71546848/220203828-6d29092c-be97-4675-a66f-7b940328d730.png)

• In Deployment Replication managed by Replica sets and not by Replication controller.
![image](https://user-images.githubusercontent.com/71546848/220203855-37a1960e-8dbf-4fa4-8bff-3451dcd83b0c.png)

• Checking the deployment properties and strategy type.
![image](https://user-images.githubusercontent.com/71546848/220203875-2e0483b9-718d-472d-881f-49d7d0f3e927.png)

• Scale up the Deployment to 6.
![image](https://user-images.githubusercontent.com/71546848/220203895-046df0f8-0447-428d-ac39-cc0a2b090f64.png)

• Check the deployment and replica sets.
![image](https://user-images.githubusercontent.com/71546848/220203917-c72ebb79-5b62-4a0e-9837-642e271d0571.png)

• Scale down the Deployment to 3.
![image](https://user-images.githubusercontent.com/71546848/220203934-66d94561-98ca-4646-971c-27639a4d5314.png)

• Check the deployment and replica sets.
![image](https://user-images.githubusercontent.com/71546848/220203945-2f3078ad-3453-4817-8452-a73ef14ee493.png)

# Deployment Strategies
There are several different types of deployment strategies available which can be chosen depending 
on the goal. 

Recreate

    In this type of deployment, if we want to upgrade the pods then we can turn off one pod recreate the 
    new with latest upgrade we can test it if all works well the old pods are killed and get replaced with 
    the new ones.
    
Rolling Strategy Deployment

    The rolling deployment is the standard default deployment to Kubernetes. It works by slowly, one by 
    one, replacing pods of the previous version of the application with pods of the new version without 
    any cluster downtime.
    A rolling update waits for new pods to become ready before it starts scaling down the old ones. If 
    there is a problem, the rolling update or deployment can be aborted without bringing the whole 
    cluster down. 
    
Canary

    Canary deployments is the more controlled strategy.
    A canary is used for when we want to test some new functionality typically on the backend of the
    application. Traditionally we may have had two almost identical servers: one that goes to all users and 
    another with the new features that gets rolled out to a subset of users and then compared. When no 
    errors are reported, the new version can gradually roll out to the rest of the infrastructure.
    While this deploy strategy can be done just using Kubernetes resources by replacing old and new pods, 
    it is much more convenient and easier to implement this strategy.
    
Blue/ Green deployments

    In a blue/green deployment strategy the old version of the application (green) and the new version 
    (blue) get deployed at the same time. When both of these are deployed, users only have access to the 
    green, whereas the blue is available to your QA team for test automation on a separate service or via 
    direct port-forwarding.
    After the new version has been tested and is signed off for release, the service is switched to the blue 
    version with the old green version being scaled down:
