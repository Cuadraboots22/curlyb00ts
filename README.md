# curlyb00ts
##AUTOMATED ELK STACK DEPLOYMENT


The files in this repository were used to configure the network depicted below.
Project#1_Cloud_Computing.PNG

<img width="364" alt="FINAL P1" src="https://user-images.githubusercontent.com/94266251/182843381-658a703e-b4f8-4787-bb87-a146ba43063e.PNG">












These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .config and .yml file may be used to install only certain pieces of it, such as Filebeat.
 
Ansible Playbook
Command: nano my-playbook.yml

 Ansible hosts
Command: nano hostsAnsible configuration
Command: nano ansible.cfg


Ansible ELK Installation and VM Configuration



















Ansible Filebeat Playbook

Command: nano filebeat-playbook.yml



Run filebeat playbook 


















Ansible Filebeat Config file
Command: nano filebeat-config.yml























Ansible Metricbeat Playbook
Command: nano metricbeat-playbook.yml

Run metricbeat 


Ansible Metricbeat Config file


























This document contains the following details:
- Description of the Topology 

- Access Policies
- ELK Configuration
  - Beats in Use: Filebeat and Metricbeat
  - Machines Being Monitored: ELK-VM, Web-1, Web-2, Web-3
- How to Use the Ansible Build:

Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA.

Load balancing ensures that the application will be highly secured, in addition to restricting web traffic to the network.
 What aspect of security do load balancers protect? Load balancers help defend against distributed denial of service attacks (DDoS) (Web security) by protecting the availability,  web traffic and web security of the system. 
What is the advantage of a jump box? The advantages of having a jump box is having automation, security, network segmentation and access control.  The jump box acts as a gateway to limit potential attacks by SSH’ng from the jumpbox to connect to other servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system _logs.
-  What does Filebeat watch for? Filebeat collects data about the file systems by monitoring  the log files, collecting log events  and forwarding the data to either Logstash or Elasticsearch for indexing.
-  What does Metricbeat record?Metricbeat  collects metric data from your target servers or it can be used to monitor other beats and ELK stack. This metrics and statistical data collected is then shipped to either Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
| Name          	| Function       	| IP Address    	| Operating System 	|   	
|---------------	|----------------	|---------------	|------------------	|---	|
| Jumpbox       	| Gateway        	| 10.1.0.4      	| Linux            	|   	
| Web-1         	| Web Server     	| 10.1.0.5      	| Linux            	|   	
| Web-2         	| Web Server     	| 10.1.0.6      	| Linux            	|   	
| Web-3         	| Web Server     	| 10.1.0.9      	| Linux            	|   	
| ELK-VM        	| Elk Server     	| 10.0.0.5      	| Linux            	|   	|
| Load Balancer 	| Load Balancer  	| 20.213.80.237 	| Linux            	|   	
| Workstation   	| Access Control 	| Public IP     	| Linux            	|   	


Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:   20.211.160.59. 
 Add whitelisted IP addresses 10.0.0.5 (ELK-VM),  10.1.0.4 (Jumpbox)   

Machines within the network can only be accessed by the Workstation and the Jump Box . Which machine did you allow to access your ELK VM?  What was its IP address?Jumpbox; ssh Red_Team_Admin@10.0.0.5 via ssh port 22 and the Workstation 20.211.160.59 via port TCP 5601


A summary of the access policies in place can be found in the table below.

| Name           	| Publicly Accessible 	| Allowed IP Address                    	|   	  	
|----------------	|---------------------	|---------------------------------------	|		
| Jump  Box      	|Yes                  	| Workstation Public  IP on SSH Port 22 	 	|   	|
| Web-1          	| No                  	| 10.1.0.5 on SSH Port 22               	|  
| Web-2          	| No                  	| 10.1.0.6 on SSH Port 22               	|   	
| Web-3         	| No                  	| 10.1.0.9 on SSH Port 22               	|   	
| Elk-VM         	| Yes                 	| Workstation Public IP using TCP 5601  	|  	   	|
| Load  Balancer 	| No                  	| Workstation Public IP on HTTP 80      	|   	                	                     	                                       	   	  	

Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible? The main advantage of automating configuration with Ansible is that it has full access to our virtual network and connects with our new VM without using the command apt-get.

The playbook implements the following tasks:
Install Docker.io and pip3
Increase VM memory
Download and configure ELK docker container
Set published ports 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.












Update the path with the name of your screenshot of docker ps output.



Target Machines & Beats
This ELK server is configured to monitor the following machines: 

 List the IP addresses of the machines you are monitoring:Web-1: 10.1.0.5; Web-2: 10.1.0.6, and Web-3: 10.1.0.9

We have installed the following Beats on these machines:Elk Server, Web-1, Web-2 and Web-3
Specify which Beats you successfully installed Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat collects data about a file system such as log files.  Metricbeat collects machine metrics such as graphs for analysis.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
Creating the Filebeat Installation Play:
Copy the filebeat-config.yml and metricbeat-config.yml files
Update the config files to include the private IP addresses of the ELK Server to the elastic search and kibana sections of the configuration file
Run the playbook, and on a browser navigate to the ELK Server http://20.210.88.153:5601/app/kibana to check if the installation worked.

 Answer the following questions to fill in the blanks
Which file is the playbook?

For ELK VM Configuration:
Copy the ansible ELK installation and VM Configuration
Command: ansible-playbook install-elk.yml

For Filebeat download the playbook using this command:
curl -L -O https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/files/filebeat-config.yml
Copy the /etc/ansible/files/filebeat-config.yml file to /etc/filebeat/filebeat-playbook.yml
Update the filebeat-playbook.yml file to include installer: curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.1-amd64.deb
Update the filebeat-config.yml file when you’re in root @49d0faf9204b:/etc/ansible/files# then nano filebeat-config.yml (to make the update and save)
Run the playbook using: ansible-playbook filebeat-playbook.yml and navigate to Kibana > Logs: add log data> system logs>5:Module Status>Check data to make sure that the installation worked.

For Metricbeat:

Download Metricbat playbook with command: curl -L -0 https://gist.githubusercontent.com/slape/58541585x1886d2e26cd8be557ce04c/raw/0ce2c7e744c54513616966affb5e9d96f5e12f73/metricbeat>/etc/ansible/files/metricbeat-config.yml
Copy the /etc/ansible/files/files/metricbeat file to /etc/metricbeat/metricbeat-playbook.yml file to include installer: curl -L -0 https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.6.1-amb64.deb
Update the metricbeat file rename to metricbeat-config.yml you must be at root: root @49d0faf9204b:/etc/ansible/files# then nano metricbeat-config.yml
Run the playbook, (ansible-playbook metricbeat-playbook.yml) and navigate to Kibana > Add Metric Data > Docker Metrics > Module Status to check that the installation worked.
 
               Which URL do you navigate to in order to check that the ELK server is running? 
                http://20.210.88.153:5601/app/kibana

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files:


Commands:
ssh Red_Team_Admin@20.211.160.59 (to get into the Jumpbox)
ssh Red_Team_Admin@10.1.0.5  (to get into the ELK-VM)
ssh Red_Team_Admin@10.1.0.6 (to access VM-2)
ssh Red_Team_Admin@10.1.0.9 (to access VM-9)
sudo docker start elk (to start elk)
sudo docker ps (to look for container)
sudo docker start quirky_payne (to start the container)
sudo docker attach quirky_payne (to attach the container)
cd /etc/ansible/ then ls and you see the files (.yml and .config) and directories
cd ansible-playbook install_elk_playbook.yml   (to install playbook)
cd /etc/ansible/roles 
cd ansible-playbook install_filebeat-playbook.yml (to install playbook filebeat playbook)
cd ansible-playbook install_metricbeat-playblook.yml (to install playbook metricbeat playbook)
ssh-keygen to create ssh key
sudo apt-get update (to update all packages)
ansible -m ping all to check the connection of ansible containers
sudo apt install docker.io (to install docker application)
sudo service docker start (to start the docker application)
systemctl status docker (to check the status of the docker application)
sudo docker pull cybersecurity/ansible (to download the docker file)
sudo docker run -ti cybersecurity/bash (to run and create a docker image)


	
