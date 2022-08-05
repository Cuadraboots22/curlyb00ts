# curlyb00ts
# AUTOMATED ELK STACK DEPLOYMENT


The files in this repository were used to configure the network depicted below.


<img width="364" alt="FINAL P1" src="https://user-images.githubusercontent.com/94266251/182843381-658a703e-b4f8-4787-bb87-a146ba43063e.PNG">












These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .config and .yml file may be used to install only certain pieces of it, such as Filebeat.
 
Ansible Playbook

Command: `nano my-playbook.yml`

<img width="353" alt="FINAL P2" src="https://user-images.githubusercontent.com/94266251/182843728-0cd3c0c0-3b5f-4e2c-9f6f-bd7811530af6.PNG">

Ansible hosts

 # /etc/ansible/hosts
 [webservers]
 10.1.0.5 ansible_python_interpreter=/usr/bin/python3
 10.1.0.6 ansible_python_interpreter=/usr/bin/python3
 10.1.0.9 ansible_python_interpreter=/usr/bin/python3

 [elk]
 10.1.0.4 ansible_python_interpreter=/usr/bin/python3


Ansible configuration

Command: `nano hosts`


<img width="234" alt="FINAL P3" src="https://user-images.githubusercontent.com/94266251/182843989-bfec1645-c6f5-4d9f-990e-2b52f8ed26e8.PNG">

Command: `nano ansible.cfg`

<img width="233" alt="FINAL P4" src="https://user-images.githubusercontent.com/94266251/182845679-09b3bd78-6991-4b0a-a11a-fdf8f2232fe6.PNG">

Ansible ELK Installation and VM Configuration



















Ansible Filebeat Playbook


<img width="236" alt="FINAL P5" src="https://user-images.githubusercontent.com/94266251/182845707-957782b4-16e2-4640-bf51-bffe55a80041.PNG">

Command: `nano filebeat-playbook.yml`

<img width="239" alt="FINAL P6" src="https://user-images.githubusercontent.com/94266251/182845719-92c1a09f-28c9-40b6-8f3d-afd694295f39.PNG">



Run Filebeat Playbook 

<img width="236" alt="FINAL P7" src="https://user-images.githubusercontent.com/94266251/182845740-9f6326ee-336c-4d7e-b889-0825f3c35cb0.PNG">


<img width="237" alt="FINAL P8" src="https://user-images.githubusercontent.com/94266251/182845755-189d66fe-c880-4e57-9ba6-7d9df2d6c73c.PNG">







Ansible Filebeat Config file

Command: `nano filebeat-config.yml`


<img width="236" alt="FINAL P9" src="https://user-images.githubusercontent.com/94266251/182845774-c204825d-1f8a-4acb-b1c2-275790a27406.PNG">






















Ansible Metricbeat Playbook

Command: `nano metricbeat-playbook.yml`

<img width="235" alt="FINAL P10" src="https://user-images.githubusercontent.com/94266251/182845791-5cc6512d-4eb1-4b3d-81c9-f692fdd9e1ad.PNG">




Run Metricbeat 


<img width="235" alt="FINAL P11" src="https://user-images.githubusercontent.com/94266251/182845811-74d680d3-a250-4bb1-864f-9a4a0053e299.PNG">



Ansible Metricbeat Config file


<img width="234" alt="FINAL P12" src="https://user-images.githubusercontent.com/94266251/182845833-d9ee6e6a-7470-4c05-87a1-d65d58ee49a5.PNG">

<img width="235" alt="FINAL P13" src="https://user-images.githubusercontent.com/94266251/182845851-8dcd4ac0-b06a-4950-864b-39aa0610002b.PNG">




This document contains the following details:
- Description of the Topology 

- Access Policies
-# ELK Configuration
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


<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Name</th>
    <th class="tg-0pky">Function</th>
    <th class="tg-0pky">IP Address</th>
    <th class="tg-0pky">OS</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">Jump Box</td>
    <td class="tg-0pky">Gateway</td>
    <td class="tg-0pky">10.1.0.4</td>
    <td class="tg-0pky">Linux</td>
  </tr>
  <tr>
    <td class="tg-0pky">Web-1</td>
    <td class="tg-0pky">Web Server</td>
    <td class="tg-0pky">10.1.0.5</td>
    <td class="tg-0pky">Linux</td>
  </tr>
  <tr>
    <td class="tg-0pky">Web-2</td>
    <td class="tg-0pky">Web Server</td>
    <td class="tg-0pky">10.1.0.6</td>
    <td class="tg-0pky">Linux</td>
  </tr>
  <tr>
    <td class="tg-0pky">Web-3</td>
    <td class="tg-0pky">Web Server </td>
    <td class="tg-0pky">10.1.0.9</td>
    <td class="tg-0pky">Linux</td>
  </tr>
  <tr>
    <td class="tg-0pky">Elk-VM</td>
    <td class="tg-0pky">Elk Server</td>
    <td class="tg-0pky">10.1.0.5</td>
    <td class="tg-0pky">Linux</td>
  </tr>
  <tr>
    <td class="tg-0pky">Load Balancer</td>
    <td class="tg-0pky">Load Balancer</td>
    <td class="tg-0pky">20.213.80.237</td>
    <td class="tg-0pky">Linux</td>
  </tr>
  <tr>
    <td class="tg-0pky">Workstation</td>
    <td class="tg-0pky">Access Control</td>
    <td class="tg-0pky">Public IP</td>
    <td class="tg-0pky">Linux</td>
  </tr>
</tbody>
</table>







#Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:   20.211.160.59. 
 Add whitelisted IP addresses 10.0.0.5 (ELK-VM),  10.1.0.4 (Jumpbox)   

Machines within the network can only be accessed by the Workstation and the Jump Box . Which machine did you allow to access your ELK VM?  What was its IP address?Jumpbox; ssh Red_Team_Admin@10.0.0.5 via ssh port 22 and the Workstation 20.211.160.59 via port TCP 5601



<img width="236" alt="FINAL P14" src="https://user-images.githubusercontent.com/94266251/182845862-c4769c61-66e0-4fa8-a411-c1ae6208efdb.PNG">

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
What is the main advantage of automating configuration with Ansible? The main advantage of automating configuration with Ansible is that it has full access to our virtual network and connects with our new VM without using the command `apt-get`.

The playbook implements the following tasks:
Install Docker.io and pip3
Increase VM memory
Download and configure ELK docker container
Set published ports 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


<img width="237" alt="FINAL P15" src="https://user-images.githubusercontent.com/94266251/182845877-ec95a455-9984-49e2-9d0d-64c58f7cf6c6.PNG">











Update the path with the name of your screenshot of docker ps output.

<img width="233" alt="FINAL P16" src="https://user-images.githubusercontent.com/94266251/182850387-18ac2fa5-3eec-4b24-8ea6-b1daa12fb171.PNG">



Target Machines & Beats
This ELK server is configured to monitor the following machines: 

List the IP addresses of the machines you are monitoring: Web-1: 10.1.0.5; Web-2: 10.1.0.6, and Web-3: 10.1.0.9

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
Command: `ansible-playbook install-elk.yml`

For Filebeat download the playbook using this command:
`curl -L -O https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/files/filebeat-config.yml`
Copy the `/etc/ansible/files/filebeat-config.yml` file to `/etc/filebeat/filebeat-playbook.yml`
Update the filebeat-playbook.yml file to include installer: `curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.1-amd64.deb`
Update the filebeat-config.yml file when you’re in root @49d0faf9204b:/etc/ansible/files# then `nano filebeat-config.yml` (to make the update and save)
Run the playbook using: ansible-playbook filebeat-playbook.yml and navigate to Kibana > Logs: add log data> system logs>5:Module Status>Check data to make sure that the installation worked.

For Metricbeat:

Download Metricbat playbook with command: `curl -L -0 https://gist.githubusercontent.com/slape/58541585x1886d2e26cd8be557ce04c/raw/0ce2c7e744c54513616966affb5e9d96f5e12f73/metricbeat>/etc/ansible/files/metricbeat-config.yml`

Copy the `/etc/ansible/files/files/metricbeat` file to `/etc/metricbeat/metricbeat-playbook.yml` file to include installer: `curl -L -0 https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.6.1-amb64.deb`

Update the metricbeat file rename to metricbeat-config.yml you must be at root: root @49d0faf9204b:/etc/ansible/files# then nano metricbeat-config.yml
Run the playbook, (ansible-playbook metricbeat-playbook.yml) and navigate to Kibana > Add Metric Data > Docker Metrics > Module Status to check that the installation worked. Which URL do you navigate to in order to check that the ELK server is running?  http://20.210.88.153:5601/app/kibana


Additional Commands:

`ssh Red_Team_Admin@20.211.160.59` (to get into the Jumpbox)

`ssh Red_Team_Admin@10.1.0.5`  (to get into the ELK-VM)

`ssh Red_Team_Admin@10.1.0.6` (to access VM-2)

`ssh Red_Team_Admin@10.1.0.9` (to access VM-9)

`sudo docker` start elk (to start elk)

`sudo docker ps` (to look for container)

`sudo docker start quirky_payne` (to start the container)

`sudo docker attach quirky_payne` (to attach the container)

`cd /etc/ansible/` then `ls` and you see the files (.yml and .config) and directories)

`cd ansible-playbook install_elk_playbook.yml`   (to install playbook)

`cd /etc/ansible/roles` 

`cd ansible-playbook install_filebeat-playbook.yml` (to install playbook filebeat playbook)

`cd ansible-playbook install_metricbeat-playblook.yml` (to install playbook metricbeat playbook)

`ssh-keygen` (to create ssh key)

`sudo apt-get update` (to update all packages)

`ansible -m ping` (all to check the connection of ansible containers)

`sudo apt install docker.io` (to install docker application)

`sudo service docker start` (to start the docker application)

`systemctl status docker` (to check the status of the docker application)

`sudo docker pull cybersecurity/ansible` (to download the docker file)

`sudo docker run -ti cybersecurity/bash` (to run and create a docker image)










	
