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
6. Cleanup\
 Terminate 2 EC2 instances\
 Delete EFS
