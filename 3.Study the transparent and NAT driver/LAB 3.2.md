# LAB 3.2 Deploy a NAT network to a container

NAT is the default configuration mode for containers, if we create the container without specifying 
the network, container will be created by using NAT network.

• List the container networks

![image](https://user-images.githubusercontent.com/71546848/220200701-4c9307de-ba05-495c-91f0-218e7b52a147.png)

• Deploy the container without specifying network.

![image](https://user-images.githubusercontent.com/71546848/220200742-f8d1be45-9c89-4871-84e9-f4363470508d.png)

• Check the container IP, I got one from NAT.

![image](https://user-images.githubusercontent.com/71546848/220200818-14a77778-ade0-427d-983a-ac26c4d0116f.png)

• I was able to connect to bing.com from container via the gateway of NAT network.

![image](https://user-images.githubusercontent.com/71546848/220200850-8fbddc22-4da0-4c0b-a18b-4998df7e106b.png)

• Deploy Custom NAT Network by specifying the subnet and gateway.

![image](https://user-images.githubusercontent.com/71546848/220200873-2da50868-061b-4036-90f4-0ddc6713d728.png)

• Deploy the container using custom NAT.

![image](https://user-images.githubusercontent.com/71546848/220200782-10c2a999-9891-40c8-865e-f0c6414c6956.png)

• Check the container IP

![image](https://user-images.githubusercontent.com/71546848/220200906-714ad659-068a-45e4-af60-b1b8e372189c.png)

• Get into the container and I was able to reach google.com from container

![image](https://user-images.githubusercontent.com/71546848/220200934-e7e4c8d7-224e-4a56-8377-c6965a15856f.png)
