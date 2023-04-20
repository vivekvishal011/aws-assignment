# Working with EC2 and EFS

``` lab WORK :-- ```

1. Create a security group with NFS protocol open\
2. Create a EFS with above security group and make sure you don’t\
enable encryption and Lifecycle management and automated\
backups to avoid charges\
3. Create an EC2 instance (Ubuntu 16.04 LTS) using the 7 step\
workflow in 2 different availability zones(1a and 1b)\
4. Login into 2 EC2 instances and install required packages\
5. Mount to EFS and start creating files to check if the data is sharing\
between 2 instances\
6. FINAL goal to attand this:-
<img width="805" alt="Screenshot 2023-04-21 at 12 24 12 AM" src="https://user-images.githubusercontent.com/88605079/233461516-39020287-d7e3-4a2d-a3dd-983a983dde42.png">


7. Cleanup\
 Terminate 2 EC2 instances\
 Delete EFS

`ANSWER STARTS:- `

` 1. Create a security group with NFS protocol open `

--> Login to the aws console and go to EC2 Dashboard and select SECURITY GROUP\

<img width="1280" alt="Screenshot 2023-04-20 at 10 43 51 PM" src="https://user-images.githubusercontent.com/88605079/233440102-081b36d2-4fea-401f-a72f-572ecf13ab73.png">

--> AFTER  that clicking on the security group select create security group\

<img width="1268" alt="Screenshot 2023-04-20 at 10 45 52 PM" src="https://user-images.githubusercontent.com/88605079/233440629-d67374aa-ba62-4e86-8f1b-a147645af09f.png">

--> fill the Basic details like Security group name, Description, etc\

<img width="1266" alt="Screenshot 2023-04-20 at 10 48 02 PM" src="https://user-images.githubusercontent.com/88605079/233440961-97039b30-605f-4a80-a5a1-c43f19000fbe.png">

--> scroll down and edit INBOUND RULE and open the NFS protocol\

<img width="1279" alt="Screenshot 2023-04-20 at 10 52 15 PM" src="https://user-images.githubusercontent.com/88605079/233441613-f393bea7-c34b-4579-9fb6-f5b064454dbd.png">

-->  give tags name and create security group\

<img width="1236" alt="Screenshot 2023-04-20 at 10 53 22 PM" src="https://user-images.githubusercontent.com/88605079/233441928-295f81c2-ae8f-446d-8da7-8ebc39af6cf8.png">

--> now your security group is created\

<img width="1280" alt="Screenshot 2023-04-20 at 10 55 21 PM" src="https://user-images.githubusercontent.com/88605079/233442294-9ad08f03-459a-4314-badf-9979db65e1cc.png">

--> finally you'll get output like this, here it is clear that one securiy group is dafault and other is that we made\

<img width="1280" alt="Screenshot 2023-04-20 at 10 57 31 PM" src="https://user-images.githubusercontent.com/88605079/233442967-9b1a7337-f66a-487a-805c-e15608f60676.png">

` 2. Create a EFS with above security group and make sure you don’t
enable encryption and Lifecycle management and automated
backups to avoid charges `

--> from the search bar search EFS and select& open efs\

<img width="1148" alt="Screenshot 2023-04-20 at 11 01 11 PM" src="https://user-images.githubusercontent.com/88605079/233443753-273fde6e-2b8c-4f45-ac11-c02c0fce34c8.png">

--> now click on the create file system \

<img width="1277" alt="Screenshot 2023-04-20 at 11 03 08 PM" src="https://user-images.githubusercontent.com/88605079/233444044-83dcdbf7-6511-4f85-b3e7-1cffc9a3012f.png">

--> give the name and select the VPC from where you want to create and then select CUSTOMIZE for adjusting efs as  per your need\

<img width="1280" alt="Screenshot 2023-04-20 at 11 04 51 PM" src="https://user-images.githubusercontent.com/88605079/233444636-fbc47d84-9768-4ab9-a112-ff844cecb07b.png">

--> make sure that encryption is off to avoid billing and all\
    (highlited in blue as well)\
<img width="1280" alt="Screenshot 2023-04-20 at 11 09 04 PM" src="https://user-images.githubusercontent.com/88605079/233445321-c7472446-c94f-435b-973b-1c1ba7b630cd.png">

--> for Performance settings go with brusting and select next\

<img width="1280" alt="Screenshot 2023-04-20 at 11 12 16 PM" src="https://user-images.githubusercontent.com/88605079/233445942-06cbcc61-9359-4fe6-8b76-4475a10f7a94.png">

--> In the Network attached the security group that we made earlier with open NFS protocol and select next\

<img width="1280" alt="Screenshot 2023-04-20 at 11 14 54 PM" src="https://user-images.githubusercontent.com/88605079/233446611-46fadca1-c246-4e48-a52d-42d7d5ad64f9.png">
<img width="1280" alt="Screenshot 2023-04-20 at 11 15 19 PM" src="https://user-images.githubusercontent.com/88605079/233446682-a0c51230-900e-4cc6-9257-bfd059618b65.png">


--> File system policy - optional: keep this default and select next\

<img width="1280" alt="Screenshot 2023-04-20 at 11 17 42 PM" src="https://user-images.githubusercontent.com/88605079/233447945-cdb18625-59e1-4aa3-a248-5091d3d1a235.png">

--> Review and create\

<img width="1280" alt="Screenshot 2023-04-20 at 11 18 57 PM" src="https://user-images.githubusercontent.com/88605079/233448174-328792fe-f8b6-47e1-aa93-fc29474c5623.png">

--> you will see that nfs is created..\

<img width="1280" alt="Screenshot 2023-04-20 at 11 23 42 PM" src="https://user-images.githubusercontent.com/88605079/233448536-045c0a1c-a0e2-4216-b6fe-c12b7512f2b6.png">

--> select the nfs and click on attached\

<img width="1269" alt="Screenshot 2023-04-20 at 11 58 12 PM" src="https://user-images.githubusercontent.com/88605079/233455525-54440863-6d9c-4da4-ac42-1c3f2cbde302.png">

--> after you will get mount command that we'll use in instance for mounting\

<img width="1269" alt="Screenshot 2023-04-20 at 11 58 59 PM" src="https://user-images.githubusercontent.com/88605079/233455809-86498027-5def-46c9-97f0-60ef8528bebb.png">


`3. Create an EC2 instance (Ubuntu 16.04 LTS) using the 7 step
workflow in 2 different availability zones(1a and 1b)`

--> go to the eec2, select launch instance fill the information like :- Name and tags, Application and OS Images (Amazon Machine Image), Instance type,\
    Key pair (login),\
    
 <img width="1280" alt="Screenshot 2023-04-20 at 11 30 39 PM" src="https://user-images.githubusercontent.com/88605079/233449963-0c37981b-3b81-4b3d-949d-fd5d4b101934.png">

--> For the availability zone :- edit NETWORK SETTINGS and in the subnet section choose 1a for AZ 1a and select sg and launch the instance\

<img width="1280" alt="Screenshot 2023-04-20 at 11 35 21 PM" src="https://user-images.githubusercontent.com/88605079/233451079-3056abaa-31cc-4dd7-8e6f-56afe86e5e42.png">

===>> note:--> for the AZ 1b do same as previous step and in the network settings choose 1b in the subnet and launch the instance\

<img width="1280" alt="Screenshot 2023-04-20 at 11 39 15 PM" src="https://user-images.githubusercontent.com/88605079/233452024-b1e02946-159a-4228-a030-650ee5c982a8.png">

--> now your both the instance is ready.. in different AZ\

<img width="1280" alt="Screenshot 2023-04-20 at 11 42 35 PM" src="https://user-images.githubusercontent.com/88605079/233452359-70f1e0e7-905a-4dad-b5be-62e97b808d1a.png">


`4. Login into 2 EC2 instances and install required packages`

--> open the terminal in two different tab\
--> go to the same folder where your pem key is stored. via using ( cd [folder_name] )\
--> in my case " cd downloads "\
--> use the command "chmod 400 your.pem"\
--> use the command "ssh -i your.pem ubuntu@publicip"\

<img width="1210" alt="Screenshot 2023-04-20 at 11 50 43 PM" src="https://user-images.githubusercontent.com/88605079/233454002-549904d2-fe35-46c2-8df1-21e7e60dfcea.png">

--> now use the following commands:-\
1. sudo apt-get update\
2. sudo su\
3. sudo apt-get install nfs-common\
(in both instance connection)\
4. mkdir vishu (for 1a) and mkdir ram (for 1b)\
   `[ note:-- mount (follow mount instructions from EFS console)]\`
5. IN the 1a use this command because our folder name is vishu so remove efs at last and add vishu:-\
 "sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-05f88babad401b523.efs.ap-south-1.amazonaws.com:/ vishu"
6.  IN the 1b use this command because our folder name is ram so remove efs at last and add ram:-\
"sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-05f88babad401b523.efs.ap-south-1.amazonaws.com:/ ram"

`5. Mount to EFS and start creating files to check if the data is sharing
between 2 instances`

7. cd vishu (in 1a) and cd ram (in 1b)\

<img width="1260" alt="Screenshot 2023-04-21 at 12 08 06 AM" src="https://user-images.githubusercontent.com/88605079/233457780-9c59a326-d7ac-450e-afe1-756597a22f05.png">

8. now touch vivek.txt (create in instance1 and check if its reflecting in instance2)\

<img width="1253" alt="Screenshot 2023-04-21 at 12 10 42 AM" src="https://user-images.githubusercontent.com/88605079/233458275-c60fb6c0-1b1e-4071-baab-d77c5f603564.png">

9. touch file2.txt (create in instance2 and check if its reflecting in Instance1)

<img width="1216" alt="Screenshot 2023-04-21 at 12 12 56 AM" src="https://user-images.githubusercontent.com/88605079/233458720-cf6cce8b-3710-412d-a9fd-c562ca521614.png">

10. cd .. 
11. umount vishu (to unmount from EFS) {from 1a} and umount ram {from 1b}\

<img width="1236" alt="Screenshot 2023-04-21 at 12 15 56 AM" src="https://user-images.githubusercontent.com/88605079/233459338-f8843cce-473e-4f8a-a5bc-ce8b870e6450.png">

`7. Cleanup
 Terminate 2 EC2 instances
 Delete EFS`

a.Terminate 2 EC2 instances\

--> select all the instance go to instance state and select terminate option and terminate the instance\

<img width="1277" alt="Screenshot 2023-04-21 at 12 20 07 AM" src="https://user-images.githubusercontent.com/88605079/233460256-8079cd8b-f500-4f79-93c5-4f8fc7a73305.png">

b. Delete EFS

-->> select the efs and choose the delete option and by giveing id and after confirmation, it will get deleted\

<img width="1280" alt="Screenshot 2023-04-21 at 12 21 44 AM" src="https://user-images.githubusercontent.com/88605079/233460851-ff525ed0-d3c7-4b88-8258-9fb6bdbc5de3.png">

<img width="1278" alt="Screenshot 2023-04-21 at 12 22 10 AM" src="https://user-images.githubusercontent.com/88605079/233460889-e633a0dc-0f91-4949-975b-a374d7430c23.png">

`This ends the assignment`

# THANK YOU
