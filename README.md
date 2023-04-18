### 1. Create an EC2 instance(Instance_1) ubuntu using the 7 step
workflow in N. Virginia Region\
--> SSH to the instance\
--> Install a simple Apache server\
--> configure http in security group\
--> Test the web server from a browser tab
### 2. Create an AMI from Instance_1
### 3. Create another EC2 instance (Instance_2) from that AMI
--> Test the web server from a browser tab
### 4. Cleanup
--> Terminate 2 EC2 instances\
--> De-register AMI\
--> Delete the snapshot\
--> Delete Volumes (if any)

#Assignment starts..\
1. login into the AWS console and search for ec2 or In the console go to service and choose ec2.\
2. From there go to or choose LAUNCH INSTANCE.
 <img width="1278" alt="Screenshot 2023-04-18 at 10 58 18 PM" src="https://user-images.githubusercontent.com/88605079/232866081-e10a1ccd-877a-4c35-b4c3-bbeb5cb5faff.png">
3. After that fill the information that are asked by service provider.(like name and tags, choose the AMI, keypair, network configuration, etc) to launch the instance.\
<img width="1280" alt="Screenshot 2023-04-18 at 11 42 17 PM" src="https://user-images.githubusercontent.com/88605079/232867800-31bb1365-47ed-4145-a528-0a42dd4bd7dd.png">
<img width="1277" alt="Screenshot 2023-04-18 at 11 43 08 PM" src="https://user-images.githubusercontent.com/88605079/232867856-c518430d-2ad3-466d-85bb-7c04e834e8b8.png">
<img width="1280" alt="Screenshot 2023-04-18 at 11 43 42 PM" src="https://user-images.githubusercontent.com/88605079/232867898-9bb165d1-a6e3-4336-adb5-e9eaac4bf5e7.png">
<img width="1274" alt="Screenshot 2023-04-18 at 11 44 33 PM" src="https://user-images.githubusercontent.com/88605079/232867953-4a6def37-25de-4d47-b07b-086442f2b6f7.png">
<img width="1280" alt="Screenshot 2023-04-18 at 11 45 01 PM" src="https://user-images.githubusercontent.com/88605079/232868015-0270a596-10f3-4f60-9710-05338fd3a90d.png">
4. After clicking on the LAUNCH INSTANCE you will see this type of page confirmation.\
 <img width="1280" alt="Screenshot 2023-04-18 at 11 50 37 PM" src="https://user-images.githubusercontent.com/88605079/232868807-37fb7bdc-4786-4a4f-8216-542edb53e23a.png">
 5. scroll down and choose view instance.\
  <img width="1273" alt="Screenshot 2023-04-18 at 11 51 07 PM" src="https://user-images.githubusercontent.com/88605079/232869014-f27669c3-92af-47ac-880d-b8620e27e577.png">
6. you will see the instance is launched.\
<img width="1280" alt="Screenshot 2023-04-18 at 11 54 38 PM" src="https://user-images.githubusercontent.com/88605079/232869327-65863e26-58b2-433f-8388-34d3f0491ecf.png">

### SSH to the instance
(I'm a mac user so i going by terminal for ssh, but it depends on user if you are window you can use putty,mobaxtrm, or git bash as well)\
1. open the terminal and go to the folder/dir where you downloaded the .pem key.\
2. (in my case i have downloaded in downloads folder with the name staragile) and use this command.\
3. command = ssh -i {pem key name} ubuntu@{public ipv4 adress of instance}.  [i have choosen ubuntu ami thats why i am ussing ubuntu other than ubuntu you have to write ec2_user].\
4. in my case the command is= ssh -i staragile.pem ubuntu@43.205.210.54 -y
 <img width="553" alt="Screenshot 2023-04-19 at 12 08 11 AM" src="https://user-images.githubusercontent.com/88605079/232872247-badf6bbc-08c7-4179-89c9-00f2b7e98299.png">
5. now you are in the server.

### Install a simple Apache server
use following command to install apache server.\
(as i have choosen ubuntu so this command is only for ubuntu server)\
1. update the server via = sudo apt update\
2. install the appache server via = sudo apt install apacha2 -y\
NOTE;- you can firts take sudo previlage that is be root user, you go via that also\
3. After successfully running both the command you will get to see the screen like this...\
<img width="561" alt="Screenshot 2023-04-19 at 12 15 39 AM" src="https://user-images.githubusercontent.com/88605079/232874069-eb4d95d6-53b2-4961-b1f6-3e274f8aaf30.png">

### configure http in security group
This part i have already done while configuration of network i tik the http protocol.\

### Test the web server from a browser tab

4. Go to the console of ec2 take the public ipv4 adress and open any browaer of your choice and hit the url, you will able to see the apache home page.\
<img width="1280" alt="Screenshot 2023-04-19 at 12 18 53 AM" src="https://user-images.githubusercontent.com/88605079/232874688-aacecdaf-d7e8-41bf-8332-b2d0d97434ad.png">


### Create an AMI from Instance_1( my case it is test_server)
1. select the instance --> go to Action-->choose image and template --> select create image.\
<img width="1280" alt="Screenshot 2023-04-19 at 12 24 38 AM" src="https://user-images.githubusercontent.com/88605079/232877777-a9a69ddf-9834-4bd0-a9e9-6b2e318d5090.png">
2. fill the information likewisw as asked.\
<img width="1280" alt="Screenshot 2023-04-19 at 12 27 56 AM" src="https://user-images.githubusercontent.com/88605079/232878748-5f82627a-e9d6-4813-b641-89ae3ab5e100.png">
3. give name and tags.(rest keep as default) then scrool down and click on create image.\
4. <img width="1270" alt="Screenshot 2023-04-19 at 12 29 53 AM" src="https://user-images.githubusercontent.com/88605079/232879100-3a3feca2-9b8c-4051-ba41-f9a66514185b.png">

you will be redirected to instace page and notification in green as in pic.\
<img width="1280" alt="Screenshot 2023-04-19 at 12 34 12 AM" src="https://user-images.githubusercontent.com/88605079/232879982-3bf3bb7b-ac4d-44b5-83e2-86064b1d9c64.png">


5, now go to AMI under images option you will see that AMI of test server is created.\
<img width="1280" alt="Screenshot 2023-04-19 at 12 35 56 AM" src="https://user-images.githubusercontent.com/88605079/232879932-2c50bf16-f454-44f6-9d29-a9d870190015.png">

### Create another EC2 instance (Instance_2) from that AMI
1. select the image i.e ami from which you want to create instance ---> Launch instance from AMI.\
<img width="1259" alt="Screenshot 2023-04-19 at 12 40 50 AM" src="https://user-images.githubusercontent.com/88605079/232883770-0f289a8f-108d-4a79-a167-d986b7795061.png">

2. give the name and rest the thing as we give in launching time of ec2--> click on launch instance.\
<img width="1277" alt="Screenshot 2023-04-19 at 12 41 50 AM" src="https://user-images.githubusercontent.com/88605079/232883898-dc0d577e-167c-46c2-8fd4-dc58ec69b2e0.png">

3. after instance is launched take the public ipv4 adress and hit in browser you will get the result.\
4. Test the web server from a browser tab....\
<img width="1280" alt="Screenshot 2023-04-19 at 12 18 53 AM" src="https://user-images.githubusercontent.com/88605079/232883975-9ab29d83-9168-47b6-862a-b9c30a294b06.png">


### Cleanup
# 1.Terminate 2 EC2 instances
select the instance and go to instance state and ---> select TERMINATE.\
<img width="1276" alt="Screenshot 2023-04-19 at 12 57 27 AM" src="https://user-images.githubusercontent.com/88605079/232884773-728fa762-24d5-4716-91ad-cc8f83a163bf.png">
<img width="1271" alt="Screenshot 2023-04-19 at 12 59 14 AM" src="https://user-images.githubusercontent.com/88605079/232884970-24956b95-b32f-4766-9f46-2c5c809ab155.png">
ON terminate the instance will be terminated.\

# 2.De-register AMI
go to ami --> select ami --> go to action -->De-register AMI
<img width="1264" alt="Screenshot 2023-04-19 at 1 01 21 AM" src="https://user-images.githubusercontent.com/88605079/232887052-43fbd5b9-d8f4-45bf-b751-015d431adc83.png">

finally as this 
<img width="1271" alt="Screenshot 2023-04-19 at 1 01 42 AM" src="https://user-images.githubusercontent.com/88605079/232887118-21b447cd-b8f6-4ada-babb-1c3727142bf9.png">

# 3.Delete the snapshot
go to snapshot --> go to action --> select delete snapshot.\
<img width="1280" alt="Screenshot 2023-04-19 at 1 04 32 AM" src="https://user-images.githubusercontent.com/88605079/232886358-20a88f5c-0984-4c74-8699-d2d50b50a15d.png">
<img width="1280" alt="Screenshot 2023-04-19 at 1 06 40 AM" src="https://user-images.githubusercontent.com/88605079/232886580-febb2ca7-23f8-4874-8834-f842fcdbec20.png">

# 4.Delete Volumes (if any)
not found but if there any \
select volume --> actions --> delete volume.


### Treasure hunt: Find out where we can find ‘Launch more like this' option and describe what it is?
In the instance section --> Actions --> image and templetes --> launch more like this ,option is there which states that ....\
The Amazon EC2 console provides a "Launch more like this" wizard option that enables the user to use a current instance as a template for launching other instances. This option automatically populates the Amazon EC2 launch wizard with certain configuration details from the selected instance.\

if you would like to launch an instance with the exact same data (basically a clone of the selected EC2 instance).\
 
<img width="1276" alt="Screenshot 2023-04-19 at 1 12 36 AM" src="https://user-images.githubusercontent.com/88605079/232888033-5165f7fc-7c28-4efc-89ee-25587e69399e.png">


### Lab Challenge: Launch a windows instance using the 7 step flow and login to it.
1. go to instance --> launch instace ...\
(give name)\
<img width="1269" alt="Screenshot 2023-04-19 at 1 22 42 AM" src="https://user-images.githubusercontent.com/88605079/232890436-0c1db0ad-1461-4754-a2f8-f5aaaa493881.png">
2. select windows ami..\
<img width="1269" alt="Screenshot 2023-04-19 at 1 23 17 AM" src="https://user-images.githubusercontent.com/88605079/232890737-30ea5764-4318-4d7e-8930-d03e96c3a036.png">
3. insance type go with t2.micro as this is free tier avilable and select key pair (if you already have then just select that)\
<img width="1265" alt="Screenshot 2023-04-19 at 1 26 08 AM" src="https://user-images.githubusercontent.com/88605079/232891104-267fb38b-2098-4051-ab3f-6ee903c0a8f8.png">
4. network section make note that RDB protocol is open i.e select rdb protocol.\
<img width="1280" alt="Screenshot 2023-04-19 at 1 29 02 AM" src="https://user-images.githubusercontent.com/88605079/232891710-a171d162-8c3b-4c97-857f-c2ac735651cc.png">
5. rest keep default or configure according to your prefrence then launch the instance.\
<img width="1276" alt="Screenshot 2023-04-19 at 1 32 12 AM" src="https://user-images.githubusercontent.com/88605079/232892217-68733c23-9031-44ba-b4ea-4a071464d43f.png">
 till this point instance is launched now we have to take connection of windows instace./


### taking connection of windows instance.
1. select the windows instace ---> go to connect option --> and then select rdb client.\
<img width="1280" alt="Screenshot 2023-04-19 at 1 34 44 AM" src="https://user-images.githubusercontent.com/88605079/232892977-536eb828-4ce1-44fd-8689-b5d05361e3ed.png">
<img width="1231" alt="Screenshot 2023-04-19 at 1 35 07 AM" src="https://user-images.githubusercontent.com/88605079/232893045-851729de-2026-415a-9a9d-d0203822d43f.png">

2. click on get password --> upload the keypair i.e .pem like --->then click on decrypt password. and copy everything like username, password,dns name ,etc.\
<img width="1269" alt="Screenshot 2023-04-19 at 1 39 59 AM" src="https://user-images.githubusercontent.com/88605079/232893738-07a42838-5e88-457e-b355-a4b0ba596b83.png">

3. now open rdb client (if not then download from google, in case you are mac user then get that from app store).\
<img width="1280" alt="Screenshot 2023-04-19 at 1 42 29 AM" src="https://user-images.githubusercontent.com/88605079/232894245-836f13b6-c1a4-46f9-ae85-61283a590102.png">

4. click on add pc.\
<img width="1280" alt="Screenshot 2023-04-19 at 1 42 29 AM" src="https://user-images.githubusercontent.com/88605079/232895917-7ce32fd3-e05a-4124-9c4d-15bec4d76cbd.png">
5. give public ipv4 and click on add.\
<img width="1280" alt="Screenshot 2023-04-19 at 1 45 04 AM" src="https://user-images.githubusercontent.com/88605079/232896097-603d43a1-1e43-4de4-b751-2d6e30903ffb.png">

6.then screen will appear like this now select the ip by double clicking on it.\
<img width="1280" alt="Screenshot 2023-04-19 at 1 45 14 AM" src="https://user-images.githubusercontent.com/88605079/232896298-69eb8526-cb91-4037-969f-7a8411b2ffa4.png">

7.now give the username and passwoed that we get from rdb client and click on continue and then continue.\
<img width="637" alt="Screenshot 2023-04-19 at 1 45 48 AM" src="https://user-images.githubusercontent.com/88605079/232896594-567f556b-fcfa-47ac-be2b-57a8c41619cd.png">
8. after getting connected within few seconds you will get the screen like this with the server details on the right top.\

<img width="1280" alt="Screenshot 2023-04-19 at 1 49 27 AM" src="https://user-images.githubusercontent.com/88605079/232896890-922a202c-6876-4035-bee0-28ec78ba3bf1.png">
This ends the ASSIGnment 01.
# THANK YOU

