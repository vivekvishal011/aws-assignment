# Creating a Custom VPC from scratch

1. Create a VPC 10.0.0.0/16 - 65536 IP addresses\
2. create public and private subnet 10.0.1.0/24, 10.0.2.0/24\
3. Enable Autoassign public ip enable for public subnet\
4. create public and private route table\
5. create internet gateway\
6. Attach Internet gateway to VPC\
7. Add Internet gateway as a route to public route table with
destination 0.0.0.0/0\
8. Create NAT Gateway with an Elastic IP (optional)\
9. Add NAT Gateway as a route in the private route table with
destination 0.0.0.0/0 (optional)\
10. Associate public subnet to Public route table\
11. Associate private subnet to private route table\
12. Create a public instance in public subnet\
13. Create a private instance in private subnet 

```Note: Optional points may charge you/```
`solution starts.../`

1. Create a VPC 10.0.0.0/16 - 65536 IP addresses\

--> login to the console go to the services and select VPC and click on the CREATE VPC\

<img width="1275" alt="Screenshot 2023-04-22 at 11 18 29 PM" src="https://user-images.githubusercontent.com/88605079/233799236-b4b600ec-87d4-4ad1-8bcd-d9e5e72a56c4.png">

--> select Resources to create, give Name tag - optional, choose IPv4 CIDR block, rest keep default for now and click on the create vpc\

<img width="1278" alt="Screenshot 2023-04-22 at 11 22 17 PM" src="https://user-images.githubusercontent.com/88605079/233799382-44b9b5db-5240-4024-8fd9-54fa22058cf8.png">
<img width="1280" alt="Screenshot 2023-04-22 at 11 22 42 PM" src="https://user-images.githubusercontent.com/88605079/233799389-451c6894-6a89-4e74-b006-ebd5df2b304e.png">

--> now your vpc with the name test-vpc is created\

<img width="1272" alt="Screenshot 2023-04-22 at 11 24 48 PM" src="https://user-images.githubusercontent.com/88605079/233799486-e8d32d32-06af-486e-a8ac-43c61d30dc56.png">

`2. create public and private subnet 10.0.1.0/24, 10.0.2.0/24`

--> go to subnet and click on the create subnet\

<img width="1278" alt="Screenshot 2023-04-22 at 11 28 05 PM" src="https://user-images.githubusercontent.com/88605079/233799603-f6570ef8-b862-4419-8d5e-af478867df7f.png">

--> choose VPC ID(vpc under which you want subnet), do Subnet settings like Subnet name, Availability Zone, IPv4 CIDR block,\
<img width="1274" alt="Screenshot 2023-04-22 at 11 32 13 PM" src="https://user-images.githubusercontent.com/88605079/233799788-eacd0bab-4b4b-42c2-8d48-8a90a3d087d9.png">

--> (for public with the name public-subnet for me)\

<img width="1277" alt="Screenshot 2023-04-22 at 11 34 54 PM" src="https://user-images.githubusercontent.com/88605079/233799825-3374d702-7a71-4b50-99c1-0554fc6226d4.png">

--> (for private with the name private-subnet for me)\

<img width="1275" alt="Screenshot 2023-04-22 at 11 37 00 PM" src="https://user-images.githubusercontent.com/88605079/233799915-cace7daf-7246-481b-a7af-8fde816f1d06.png">

--> then click on create subnet and you will subnet is created\

<img width="1278" alt="Screenshot 2023-04-22 at 11 37 52 PM" src="https://user-images.githubusercontent.com/88605079/233799965-f016f995-fa29-42ef-a410-4e3c6486281f.png">

`3. Enable Autoassign public ip enable for public subnet\`

--> select the public subnet and go to action and then select subnet settings\
<img width="1271" alt="Screenshot 2023-04-22 at 11 40 20 PM" src="https://user-images.githubusercontent.com/88605079/233800062-370c25d9-3c4f-4237-95ba-099ea7ed541a.png">

--> enable the autoassign public ip by blue tik and then scroll down and save the changes\
<img width="1279" alt="Screenshot 2023-04-22 at 11 41 52 PM" src="https://user-images.githubusercontent.com/88605079/233800148-bbbcd6c8-16c4-4c78-bd1a-155e43fc5980.png">

`4. create public and private route table`

--->  go to route tables and selct create route table\
<img width="1272" alt="Screenshot 2023-04-22 at 11 44 32 PM" src="https://user-images.githubusercontent.com/88605079/233800253-a49ef926-c0c4-470e-880c-2c6ee7f29282.png">

--> give the Name - optional, VPC, Tags, etc and create route table\
`for public i gave name public-rt`
<img width="1263" alt="Screenshot 2023-04-22 at 11 47 51 PM" src="https://user-images.githubusercontent.com/88605079/233800366-836ad7a5-9294-432e-9425-e92869b1f3ad.png">

`for private i gave name private-rt`
<img width="1275" alt="Screenshot 2023-04-22 at 11 49 51 PM" src="https://user-images.githubusercontent.com/88605079/233800438-97575220-7e57-41f7-a9dc-fe0b4fecafea.png">

`5. create internet gateway`
--> go to internet gateway and click on create internet gateway\
<img width="1274" alt="Screenshot 2023-04-22 at 11 53 13 PM" src="https://user-images.githubusercontent.com/88605079/233800555-53a7e063-1ae5-4955-bc50-7b754adaaced.png">

--> give Name tag & all and create internet gateway\
<img width="1276" alt="Screenshot 2023-04-22 at 11 55 47 PM" src="https://user-images.githubusercontent.com/88605079/233800627-07338372-05f3-4bdd-a086-65010a520dcc.png">

`6. Attach Internet gateway to VPC`
--> select the internet gateway go to action select attach vpc\
<img width="1270" alt="Screenshot 2023-04-22 at 11 57 04 PM" src="https://user-images.githubusercontent.com/88605079/233800728-7a474419-e3fd-477d-b168-20579b187faf.png">

--> from the Available VPCs choose the right vpc to which you want to attach\
<img width="1280" alt="Screenshot 2023-04-22 at 11 57 37 PM" src="https://user-images.githubusercontent.com/88605079/233800768-0b97d8c5-3919-4324-ba4e-aecf79ce89d4.png">

`7. Add Internet gateway as a route to public route table with destination 0.0.0.0/0`
--> go to route table there choose the public route table and then go to route option in the down side and edit route\
<img width="1280" alt="Screenshot 2023-04-23 at 12 02 59 AM" src="https://user-images.githubusercontent.com/88605079/233800904-f29d6fbd-4fc0-4a6f-90f3-1c09d9f2ac40.png">

--> now by choosing edit route then add route choose internet gateway by ig we'll communicate with internet world.\
<img width="1277" alt="Screenshot 2023-04-23 at 12 04 50 AM" src="https://user-images.githubusercontent.com/88605079/233801011-3d58ee39-12be-45bf-9664-82aa463be420.png">

--> select the right igw that you created in case you have more than one and do the save changes\
<img width="1273" alt="Screenshot 2023-04-23 at 12 06 09 AM" src="https://user-images.githubusercontent.com/88605079/233801037-2bdbd8d6-a1c6-4b31-b88c-a3f1944c9578.png">

`10. Associate public subnet to Public route table`

--> scroll down and choose subnet association and choose edit subnet association\
<img width="1280" alt="Screenshot 2023-04-23 at 12 09 52 AM" src="https://user-images.githubusercontent.com/88605079/233801166-1da2a32d-bfc5-4a0a-9151-262eec98c0d0.png">

--> select the public subnet (or the one that you want to associate) and do the save shanges\
<img width="1280" alt="Screenshot 2023-04-23 at 12 11 04 AM" src="https://user-images.githubusercontent.com/88605079/233801236-50d6905f-040f-4483-9e1a-4d205590aff9.png">

`11. Associate private subnet to private route table`
-->> select the public-rt from route table and go to action and select edit subnet association\
<img width="1276" alt="Screenshot 2023-04-23 at 12 14 22 AM" src="https://user-images.githubusercontent.com/88605079/233801345-39986591-3207-4658-8f91-db6c99cb6680.png">

-->> choose the right subnet there (in my case private-subnet) and do the save association\
<img width="1277" alt="Screenshot 2023-04-23 at 12 15 53 AM" src="https://user-images.githubusercontent.com/88605079/233801407-105b77dd-d0ae-4519-89f7-71692b0f7319.png">

`12. Create a public instance in public subnet`

--> go to ec2 select launch instance and give Name and tags, Application and OS Images (Amazon Machine Image, Instance type, Key pair (login)\
<img width="1276" alt="Screenshot 2023-04-23 at 12 25 59 AM" src="https://user-images.githubusercontent.com/88605079/233801788-9cb86c40-60bb-4293-8509-6909fb2af08a.png">
--> In the network settings choose edit option and do the following changes like -- choose the vpc that you created, public subnet that created by you,
    make sure that auto-assign public ip is enabled\
    <img width="1279" alt="Screenshot 2023-04-23 at 12 31 34 AM" src="https://user-images.githubusercontent.com/88605079/233802030-3844643f-3ca9-4362-9fc5-db2776abe2e1.png">

--> make sure in the security group ssh protocol is open and go with the default storage settings and we are good to launch instance\

<img width="1277" alt="Screenshot 2023-04-23 at 12 33 36 AM" src="https://user-images.githubusercontent.com/88605079/233802092-95d48ea3-bb1b-4220-a3f1-988045bf80e1.png">

`13. Create a private instance in private subnet`
-->> go to ec2 select launch instance and give Name and tags, Application and OS Images (Amazon Machine Image, Instance type, Key pair (login)\
<img width="1280" alt="Screenshot 2023-04-23 at 12 37 40 AM" src="https://user-images.githubusercontent.com/88605079/233802243-12847723-e40c-4623-9ede-b2ed3fcbc29e.png">

-->In the network settings choose edit option and do the following changes like -- choose the vpc that you created, choose private-subnet that created by you, make sure that auto-assign public ip is disable\
<img width="1274" alt="Screenshot 2023-04-23 at 12 37 07 AM" src="https://user-images.githubusercontent.com/88605079/233802283-e58137f7-f4fe-4951-9f3f-d818eb595880.png">

--> make sure in the security group ssh protocol is open and go with the default storage settings and we are good to launch instance\
<img width="1277" alt="Screenshot 2023-04-23 at 12 33 36 AM" src="https://user-images.githubusercontent.com/88605079/233802311-b46ab9c9-381e-4ca1-a67e-593433e6daa0.png">
 ===>> now your both public and private instance are launched from their respective subnets\
 <img width="1279" alt="Screenshot 2023-04-23 at 12 43 32 AM" src="https://user-images.githubusercontent.com/88605079/233802435-6ebd1bd8-e039-4926-860b-6fdd082d2373.png">

`=============================================================================================================================`
 
 --> now lets do ssh in the public instance--\
--> open the terminal go the folder where your pem is there and use the command = ssh -i [PEM file name] ubuntu@[PUBLIC IP] \
   (before that don't forget to run this command= chmod 400 [PEM file name])\
   
   ---> use the following command...\
       1. sudo apt-get update\
       2. sudo su\
       3. chmod 777 /opt\
       4. exit\
       5. exit
  <img width="610" alt="Screenshot 2023-04-23 at 12 52 50 AM" src="https://user-images.githubusercontent.com/88605079/233802791-10dbd50c-8749-4e32-b055-4a40c8cfcf4c.png">

--> here actually we are trying to do ssh from public instance to private instance because cross-ip communication is allowed in same vpc,\
   for this we open ssh protocol in both the instance and now i am coping the pem that is for private instance to the public instace /opt folder so that from there i can do ssh to private instance.to do this need to folloow this command ---\
   
   1. scp -i public.pem ./private.pem ubuntu@publicip:/opt\
   2. <img width="747" alt="Screenshot 2023-04-23 at 1 02 26 AM" src="https://user-images.githubusercontent.com/88605079/233803170-dd841cb3-3660-42d1-a6fe-95b87088309c.png">


   3. ssh -i public.pem ubuntu@publicip\
   4. cd /opt\
   5. ls\
   6. chmod 400 private.pem\

  <img width="734" alt="Screenshot 2023-04-23 at 1 05 22 AM" src="https://user-images.githubusercontent.com/88605079/233803259-512e2700-c9ba-441b-a04a-4d33d8fada11.png">


   7. ssh -i private.pem ubuntu@privateip\
   8. sudo apt-get update ( u will not be able to connect to\
internet as private instance is in the private subnet if you don’t\
create NAT Gateway)\

--> see its not responding because of it is in private subnet\
<img width="744" alt="Screenshot 2023-04-23 at 1 09 11 AM" src="https://user-images.githubusercontent.com/88605079/233803438-eab0af32-1347-464e-9e6a-6c41ffda2dea.png">

==>> to solve this we need to attach nat instance/nat gateway in private route table(in my case i'm taking nat gateway)\

--> go to NAT gateway and click on create NAt gateway\
<img width="1277" alt="Screenshot 2023-04-23 at 1 40 11 AM" src="https://user-images.githubusercontent.com/88605079/233804416-42a7df18-abb4-4a29-bb6f-0721aafb5f4a.png">

--> give the Name - optional, choose the subnet (in public subnet), Connectivity type(go with either public with elastic ip pr private),and create nat-gateway\
<img width="1277" alt="Screenshot 2023-04-23 at 1 44 11 AM" src="https://user-images.githubusercontent.com/88605079/233804518-bb79bfcc-08df-472d-a1ed-ab4d198a7a09.png">

--> now go to route table and select the private route table and go to action and select edit route\
<img width="1277" alt="Screenshot 2023-04-23 at 1 46 30 AM" src="https://user-images.githubusercontent.com/88605079/233804632-4ca360eb-9dc2-44e2-847d-ecf6bfe2a0cc.png">

--> do add route and search for nat-gateway and the right nat-gatway(or if you through nat instance then select instance and then right nat-instance)\
---> and do the save change.\

<img width="1275" alt="Screenshot 2023-04-23 at 1 49 26 AM" src="https://user-images.githubusercontent.com/88605079/233805120-22c5694c-8964-4d3d-8879-e5993c859acb.png">
<img width="1271" alt="Screenshot 2023-04-23 at 1 49 49 AM" src="https://user-images.githubusercontent.com/88605079/233805128-82348d4b-0b5c-45ee-b8be-71c774469590.png">


--> now wait for few seconds and go to terminal and again do the ping this time you will get the result.\
<img width="748" alt="Screenshot 2023-04-23 at 1 35 32 AM" src="https://user-images.githubusercontent.com/88605079/233805187-2ecff0af-b8c3-462e-9fa4-ca1d76bf84df.png">
 ==>> finally you you will able to update your machine\
 
 <img width="753" alt="Screenshot 2023-04-23 at 1 39 03 AM" src="https://user-images.githubusercontent.com/88605079/233805207-6fabd75c-b40f-41b0-93f7-2ab5a29b6466.png">


`Cleanup`
` Terminate 2 EC2 instances`
` Delete NAT Gateway and Elastic IP (If created)`
` Delete VPC and its components`

1. Terminate 2 EC2 instances\

--> select all the instance go to instance state and select terminate instance.\
<img width="1278" alt="Screenshot 2023-04-23 at 1 56 12 AM" src="https://user-images.githubusercontent.com/88605079/233805312-757068bd-48c1-40b7-97cf-d50c203f6f2e.png">

2. Delete NAT Gateway and Elastic IP (If created)\

--> go to nat gateway and select the nat gateway and go to action and select delete nat gateway\
<img width="1274" alt="Screenshot 2023-04-23 at 1 57 58 AM" src="https://user-images.githubusercontent.com/88605079/233805386-79e0a245-ba87-4089-8c14-3a5d0cef535f.png">
--> you need to confirm by typing delete and then select delete.\
<img width="1271" alt="Screenshot 2023-04-23 at 1 59 28 AM" src="https://user-images.githubusercontent.com/88605079/233805422-a09a6fae-ab26-466d-957f-151c30cfad67.png">

--> if you created elastic ip then go to elaspic ip and select the ip and go to action select REALESE ip and relese the ip\
<img width="1277" alt="Screenshot 2023-04-23 at 2 01 39 AM" src="https://user-images.githubusercontent.com/88605079/233805525-33130044-780a-4523-a4e1-3895c1b5436d.png">

3. Delete VPC and its components\
--> go to vpc , select the vpc, go to action  and select delete vpc\

<img width="1272" alt="Screenshot 2023-04-23 at 2 04 15 AM" src="https://user-images.githubusercontent.com/88605079/233805572-bcd392d3-15d1-4f1e-93f0-146bf0502e3d.png">

--> confirm the deletetion by typing delete and then delete.\
<img width="1275" alt="Screenshot 2023-04-23 at 2 05 23 AM" src="https://user-images.githubusercontent.com/88605079/233805610-4d2435bd-9cf0-4f58-aa46-94d0775bdada.png">

`this ends the project vpc`

### Treasure hunt: what is egress-only Internet Gateway?

An egress-only Internet Gateway (EGW) is a horizontally scaled, redundant, and highly available component in Amazon Web Services (AWS) that enables traffic from an Amazon VPC (Virtual Private Cloud) to the internet. It provides a single path for traffic to leave the VPC, but it does not allow any traffic to enter the VPC.

The main purpose of an egress-only Internet Gateway is to allow outgoing communication from resources within a VPC to the internet while preventing incoming traffic from the internet. It provides IPv6-only connectivity and is used when you need to restrict inbound access to your resources while still allowing outbound communication.

In summary, an egress-only Internet Gateway is an AWS service that allows resources within a VPC to access the internet while blocking all incoming traffic from the internet.


```THANK YOU```

THIS ENDS WITH THE PROJECT 1.











