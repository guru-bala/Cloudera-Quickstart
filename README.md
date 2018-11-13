# Cloudera-Quickstart - 
# Steps to create a Cloudera quickstart VM with docker container on Azure 
# A very easy and simplified way to get started with cloudera quickstart VM, as opposed to installing on a local machine
Create/Provision a simple Ubuntu Linux VM on Azure - D4S-V3 machine, as Cloudera VM needs 16GB (costs ~$220/month). 
Steps to create a Linux Azure VM - https://docs.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-manage-vm
SSH through putty into the VM (ensure that you have provided inbound access to ports 22 and to port 7180 for access to Cloudera console)
  In the VM console page, look for "Settings => Networking" to create new inbound port rules for the above mentioned ports
Install docker on the VM through the below commands
  sudo apt-get update
  sudo apt-get install docker.io
  sudo docker pull cloudera/quickstart
Run the docker within the VM
  sudo docker run --hostname=quickstart.cloudera --privileged=true -t -i -p 8888:8888 -p 7180:7180 cloudera/quickstart /usr/bin/docker-quickstart
The above command will take you inside the container.  Run the following inside the container 
If the container is already running, get into the container thru - 
  sudo docker exec -it <container id> /bin/bash # you can start executing commands after this line
  sudo docker ps #to get the container id, for the above line
Export the env variable inside the docker so that you have all available permissions
  export HADOOP_USER_NAME=hdfs - to overcome any permission problems/errors
Everytime you login to the VM, ensure you repeat steps 15,16 and 18 to get into the docker and have all required permissions
With this you should be good to go and execute your assignments on the course
Connect to cloudera manager from browser http://<ip of vm>:7180
