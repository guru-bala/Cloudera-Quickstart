# Cloudera-Quickstart - 
## Steps to create a Cloudera quickstart VM with docker container on Azure

1. Create/Provision a simple Ubuntu Linux VM on Azure - D4S-V3 machine, as Cloudera VM needs 16GB. 

Steps to create a Linux Azure VM can be found [here](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-manage-vm)

2. SSH through putty into the VM (ensure that you have provided inbound access to ports 22 and to port 7180 for access to Cloudera console)

3. In the VM console page, look for "Settings => Networking" to create new inbound port rules for the above mentioned ports

4. Install docker on the VM through the below commands 
- **sudo apt-get update**
- **sudo apt-get install docker.io** 
- **sudo docker pull cloudera/quickstart**
- Run the docker within the VM with the command **sudo docker run --hostname=quickstart.cloudera --privileged=true -t -i -p 8888:8888 -p 7180:7180 cloudera/quickstart /usr/bin/docker-quickstart** 

The above command will take you inside the container.  

 If the container is already running, get into the container thru  
 - **sudo docker exec -it /bin/bash *containerId***. 
 You can get the *containerId* (for the above step) with the command 
 - **sudo docker ps**. 

- Export the env variable inside the docker so that you have all available permissions by running the command **export HADOOP_USER_NAME=hdfs**  to overcome any permission problems/errors. Everytime you login to the VM, ensure you repeat the steps required to be run inside the container and have all required permissions.
5. With this you should be good to go and execute your assignments on the course. 
6. One last tip - you can connect to cloudera manager from browser [http://`<ip of vm>`:7180]()

