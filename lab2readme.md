# Working with EC2 and EBS

### 1. Create an EC2 instance (Ubuntu 16.04 LTS) using the 7 step
workflow in 2 different availability zones(1a and 1b)\
2. Create an ‘EBS Volume 1’ and attach to instance which is in 1a\
3. Create a snapshot from the above ‘EBS volume 1’\
4. Create another ‘EBS volume 2’ in 1b from the snapshot\
5. Attach ‘EBS volume 2’ to instance which is in 1b\
6. Cleanup\
 Terminate 2 EC2 instances\
 Delete the snapshot\
 Delete Volumes

### Assignment srarts....
1.Create an EC2 instance (Ubuntu 16.04 LTS) using the 7 step\
workflow in 2 different availability zones(1a and 1b)\

--> To create a instance login into the aws console and choose ec2 service from search bar or from your left side service section.\
--> then choose LAUNCH INSTANCE
<img width="1274" alt="Screenshot 2023-04-19 at 10 55 56 PM" src="https://user-images.githubusercontent.com/88605079/233153319-8c3b43de-47a2-43a4-b1a4-7aed973354fb.png">

--> THen give Name and tags\
<img width="1270" alt="Screenshot 2023-04-19 at 11 01 46 PM" src="https://user-images.githubusercontent.com/88605079/233155601-7883ec4d-a19b-424c-b981-8ca09a6bf2d5.png">

--> choose Application and OS Images (Amazon Machine Image)\
<img width="1280" alt="Screenshot 2023-04-19 at 11 02 55 PM" src="https://user-images.githubusercontent.com/88605079/233155790-057700ea-8239-49c5-9a81-6b9c74a3f37d.png">

--> choose Instance type and select Key pair (login) (if you already have or crate new one)\
<img width="1257" alt="Screenshot 2023-04-19 at 11 04 07 PM" src="https://user-images.githubusercontent.com/88605079/233155961-8df69758-f5e4-4608-8cea-af6c4053b8ec.png">

--> edit network settings\
<img width="1271" alt="Screenshot 2023-04-19 at 11 04 52 PM" src="https://user-images.githubusercontent.com/88605079/233156154-ba0e5d9d-21a4-4c52-a253-155dc42f79a9.png">
 >>>> for different availability zone choose from subnet section after selecting edit option\
 <img width="1275" alt="Screenshot 2023-04-19 at 11 05 23 PM" src="https://user-images.githubusercontent.com/88605079/233156425-2ffb30a4-6f76-47c8-97f6-80b094dcb58c.png">

--> Configure storage according to your prefrence\
<img width="1279" alt="Screenshot 2023-04-19 at 11 06 09 PM" src="https://user-images.githubusercontent.com/88605079/233156667-12b7cbfd-2939-44b9-9701-6b90623aa937.png">
 --> then click on launch instance\
 <img width="1276" alt="Screenshot 2023-04-19 at 11 13 11 PM" src="https://user-images.githubusercontent.com/88605079/233157172-bf420c13-4d6e-4033-99b4-a8706c35bae4.png">
--> finally your instance is ready\
<img width="1280" alt="Screenshot 2023-04-19 at 11 13 42 PM" src="https://user-images.githubusercontent.com/88605079/233157324-65045acb-19ae-4590-be56-cb0858494234.png">

---->> we have to create two instance in two different availability zone, one is ready in 1a zone for launching the instance in othe A. zone like in 1b,\
just go to NETWORK SETTINGS AND choose EDIT option and in the subnet option choose 1b.\
<img width="1277" alt="Screenshot 2023-04-19 at 11 20 06 PM" src="https://user-images.githubusercontent.com/88605079/233159043-14b0e64e-7856-4784-bb07-73abfb0b91f7.png">
after selection of A.zone screen will looks like this\
<img width="1280" alt="Screenshot 2023-04-19 at 11 20 41 PM" src="https://user-images.githubusercontent.com/88605079/233159113-4cb22821-d6df-46e4-8a09-92dc7a9df9b7.png">

--> keep rest start same as first one and then launch the instance you will get your 2nd instance in 1b is ready.\
<img width="1275" alt="Screenshot 2023-04-19 at 11 21 29 PM" src="https://user-images.githubusercontent.com/88605079/233159534-68e2ff54-c73e-413d-bb6f-d7343a760fa9.png">

### 2. Create an ‘EBS Volume 1’ and attach to instance which is in 1a.
--->> scroll down and from Elastic Block Store choose volume and click on CREATE VOLUME\
<img width="1280" alt="Screenshot 2023-04-19 at 11 27 44 PM" src="https://user-images.githubusercontent.com/88605079/233160821-f073fd56-e55b-4ea7-910b-6603ba26e1e6.png">

--->> ACCOrding to your need choose Volume type, Size (GiB), Availability Zone, Tags - optional, etc and then click on create volume.\
<img width="1272" alt="Screenshot 2023-04-19 at 11 33 49 PM" src="https://user-images.githubusercontent.com/88605079/233162017-11a7de61-33d4-48f2-bd0f-71ed2e577227.png">
<img width="1280" alt="Screenshot 2023-04-19 at 11 34 42 PM" src="https://user-images.githubusercontent.com/88605079/233162054-5c8df799-4ec6-4286-88f7-1da790a1f0bb.png">
--->> you get your volume is created\
<img width="1280" alt="Screenshot 2023-04-19 at 11 36 57 PM" src="https://user-images.githubusercontent.com/88605079/233162517-9c2f1ee4-d83b-44e1-b3ca-5ec100721cac.png">
--->> now select the created ebs volume and go to action and choose ATTACH volume\
<img width="1274" alt="Screenshot 2023-04-19 at 11 39 35 PM" src="https://user-images.githubusercontent.com/88605079/233163055-6b7387e9-c45d-417f-a50b-1e870ff94955.png">
--->> choose Instance to attached and click on attach volume\
<img width="1270" alt="Screenshot 2023-04-19 at 11 40 42 PM" src="https://user-images.githubusercontent.com/88605079/233163413-1177782a-d8e1-483e-84c5-abaa805d8f13.png">
--->> now you will see that your volume is attached and in-use (earlier it was showing available only in blue color)\
<img width="1280" alt="Screenshot 2023-04-19 at 11 43 05 PM" src="https://user-images.githubusercontent.com/88605079/233163893-3c4d3960-baf1-4529-8b29-26e87309a255.png">

### 3. Create a snapshot from the above ‘EBS volume 1’

---->>> scroll down and from Elastic Block Store choose snapshot and click on create snapshot\
<img width="1280" alt="Screenshot 2023-04-19 at 11 47 22 PM" src="https://user-images.githubusercontent.com/88605079/233164644-91e1646c-14c0-4d75-8146-12c84ac0a59d.png">
---->>> choose Resource type, Volume ID, give some Description, give Tags and click of create snapshot.\
<img width="1280" alt="Screenshot 2023-04-19 at 11 51 59 PM" src="https://user-images.githubusercontent.com/88605079/233165930-1dd37e2c-5ea6-480c-b8a1-b96fe07263a9.png">
<img width="1264" alt="Screenshot 2023-04-19 at 11 52 24 PM" src="https://user-images.githubusercontent.com/88605079/233165969-f855bb5c-0c87-4ebd-90af-795556b8a792.png">
---->>> finaaly snapshot is created\
<img width="1280" alt="Screenshot 2023-04-19 at 11 53 03 PM" src="https://user-images.githubusercontent.com/88605079/233166094-0c4cbe28-58db-418e-b70c-b35b508127b4.png">

### 4. Create another ‘EBS volume 2’ in 1b from the snapshot

----->>>> select the snapshot from which you want to create volume and then go to action and choose create volume from snapshot.\
<img width="1262" alt="Screenshot 2023-04-19 at 11 55 45 PM" src="https://user-images.githubusercontent.com/88605079/233166819-c8c3273b-bad2-459d-963c-44fe4df084a7.png">
----->>>> now according to your need select Volume type, Size (GiB), Availability Zone, Tags - optional,etc and then click on create volume.\
<img width="1268" alt="Screenshot 2023-04-20 at 12 00 53 AM" src="https://user-images.githubusercontent.com/88605079/233167948-7507ba09-e7ba-489d-9d4b-f1ffa518e468.png">
<img width="1260" alt="Screenshot 2023-04-20 at 12 01 31 AM" src="https://user-images.githubusercontent.com/88605079/233168040-dc6e9d0e-b125-4c2d-b6a0-7e48ea7a5dca.png">
<img width="1238" alt="Screenshot 2023-04-20 at 12 01 49 AM" src="https://user-images.githubusercontent.com/88605079/233168079-3870de1f-e785-4a40-a4f4-bd34e761f906.png">
----->>>> see volume is created from snapshot and is inavailable state\
<img width="1246" alt="Screenshot 2023-04-20 at 12 04 04 AM" src="https://user-images.githubusercontent.com/88605079/233168498-def19f59-cf79-44bb-b856-8fda3764178f.png">

### 5. Attach ‘EBS volume 2’ to instance which is in 1b
------>>>>> select the volume go to action and select attach volume\
<img width="1280" alt="Screenshot 2023-04-20 at 12 06 03 AM" src="https://user-images.githubusercontent.com/88605079/233169028-4eda7506-0f1f-4341-a0f7-adf3925a443c.png">
------>>>>> select the instance to which you want to attached the volume and click on the attached volume\
<img width="1275" alt="Screenshot 2023-04-20 at 12 08 02 AM" src="https://user-images.githubusercontent.com/88605079/233169470-93d8e659-aa89-4552-867e-e64e25ca3f84.png">
------>>>> finaly you will see the volume is attached and in-use state.\
<img width="1277" alt="Screenshot 2023-04-20 at 12 09 43 AM" src="https://user-images.githubusercontent.com/88605079/233169764-b05f1aa3-cc3f-47bf-be23-da6f1750afa5.png">

### 6. Cleanup
 Terminate 2 EC2 instances\
 Delete the snapshot\
 Delete Volumes\

1.Terminate 2 EC2 instances\

===> select the instance that you want to terminate and go to instance state and choose terminate instance.\
<img width="1275" alt="Screenshot 2023-04-20 at 12 12 23 AM" src="https://user-images.githubusercontent.com/88605079/233170415-814a29bd-72d8-4b59-921f-16208bfefd67.png">

2. Delete the snapshot
===>> In the elastic block volume select snapshot, select the snapshot and go to action there select delete volume\
<img width="1272" alt="Screenshot 2023-04-20 at 12 15 08 AM" src="https://user-images.githubusercontent.com/88605079/233171132-bf90017e-3d2c-4111-8db1-4997c1067461.png">
===>>then delete the snapshot by clicking on delete\
<img width="1280" alt="Screenshot 2023-04-20 at 12 16 59 AM" src="https://user-images.githubusercontent.com/88605079/233171388-7eb563c2-f6ca-4c04-a6a7-a194aaa34edb.png">
 
3. Delete Volumes
===>> In the volume slect all the volume that you want to delete and then go to action select delete volume\
<img width="1278" alt="Screenshot 2023-04-20 at 12 18 25 AM" src="https://user-images.githubusercontent.com/88605079/233171715-5c64c037-73ec-4079-9cd2-0f88be5bcf9d.png">

===>> by writing and selecting and clicking on delete you will able to delte the volume.\
<img width="1271" alt="Screenshot 2023-04-20 at 12 19 40 AM" src="https://user-images.githubusercontent.com/88605079/233172021-c3800935-0e73-4416-911a-d1244ff63c6e.png">

### Treasure hunt: Is it possible to detach the root volume from EC2 instance? If Yes or No (with screenshots)
===>> create a instance and in the configure storage section there is a build in storage that is like same as c: drive in windows and\
there is a option of add volume also that is ebs volume.\
<img width="1276" alt="Screenshot 2023-04-20 at 12 25 39 AM" src="https://user-images.githubusercontent.com/88605079/233174403-ef66e1ba-82e4-400b-9d5a-ca04762c7d0d.png">
 add the ebs volume and launch the instance\
 <img width="1279" alt="Screenshot 2023-04-20 at 12 32 49 AM" src="https://user-images.githubusercontent.com/88605079/233176940-8db66f1a-ea03-4acb-98e4-ba0443598784.png">

 ===>> now go to volume under elastic block volume option and select volume, there you will see both the volume root as well as ebs\

selct ebs volume and go to action and then select force detach option and type detach and click detach and detach the ebs volume\ 
<img width="1274" alt="Screenshot 2023-04-20 at 12 28 02 AM" src="https://user-images.githubusercontent.com/88605079/233175350-9df1cc7c-85ca-4156-82ad-05f47f7fdf5d.png">
==>> after that again selct ebs volume and go to action there you will see the delete volume option is activated from there follow the step and delete the volume\
<img width="1276" alt="Screenshot 2023-04-20 at 12 28 47 AM" src="https://user-images.githubusercontent.com/88605079/233175603-415c7202-a4ce-4034-91a2-40c3c99ca478.png">
<img width="1280" alt="Screenshot 2023-04-20 at 12 29 10 AM" src="https://user-images.githubusercontent.com/88605079/233175649-92429539-3240-4286-b769-778b69dd9c4a.png">
==>> you will see only root volume is there.\
<img width="1279" alt="Screenshot 2023-04-20 at 12 29 31 AM" src="https://user-images.githubusercontent.com/88605079/233175866-359b1aa2-cd18-4cf6-922d-d0b233a8b7de.png">

===>> select root volume and go to action there you will see that neither detach option is activated nor delete option.\
<img width="1280" alt="Screenshot 2023-04-20 at 12 27 01 AM" src="https://user-images.githubusercontent.com/88605079/233176091-6369e4d5-37d2-4da8-96af-a15f352b1a4a.png">

===>> now it's clear that root volume is undetachable and undeletable.

### Lab Challenge: Try to login into the instance and create a file (test.txt) in EBS volume





