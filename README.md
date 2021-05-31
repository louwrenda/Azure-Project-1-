# Azure-Project-1-
Week 13 
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Azure Network

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.
¬
  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable and available, in addition to restricting access to the network.

•	Load balancers can defend an organization against denial-of-service (DDos) attacks by shifting attack traffic. 
•	A jumpbox serves as a gateway to gain entry into a remote network. Many times the primary mode of access is ssh and without the key access is forbidden. The advantage of a jump box is to give access to the user from a single node that can be secured and monitored. 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system traffic. .
What does Filebeat watch for?
Filebeat monitors the system logs and watches for any information that has changed and forward it to the Elasticsearch Host/ 
What does Metricbeat record?
Metricbeat records the metrics and statistics from the operation system and from services running on the server.

The configuration details of each machine may be found below.

| Name     	| Function             	| IP Address 	| Operating System 
| Jump Box 	| Gateway              	| 10.0.0.4   	| Linux (ubuntu 18.04)
| Web-1    	| Web Server           	| 10.0.0.5   	| Linux (ubuntu 18.04)     
| Web-2    	| Web Server           	| 10.0.0.6   	| Linux (ubuntu 18.04)
| Web-3    	| Web Server           	| 10.0.0.7   	| Linux (ubuntu 18.04)
| ELK      	| Elastic-Search Stack 	| 10.1.0.4   	| Linux (ubuntu 18.04)

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
•	149.167.249.205
Machines within the network can only be accessed by the Jump Box virtual machine
•	The Jump Box VM has access to the ELK machine. 
Public IP – 23.101.113.48
Private IP – 10.0.0.4


A summary of the access policies in place can be found in the table below.

| Name     	| Publicly Accessible 	| Allowed IP Addresses 	
|----------	|---------------------	|----------------------	
| Jump Box 	| Yes                 	| 149.167.249.205      	|
| Web-1    	| No                  	| 10.0.0.4             	|
| Web-2    	| No                  	| 10.0.0.4             	|
| Web-3    	| No                  	| 10.0.0.4             	|
| ELK      	| No                  	| 10.0.0.4             	|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
•	It allows for full automation of a specific server and reduces configuration errors

The playbook implements the following tasks:
•	Install Docker: Installs the core docker code to the remote server
•	Install Python3_pip: Pip is an installation module that allows for additional docker modules to be installed easier
•	Install Docker python Module: Tells the previous PIP module to install the necessary docker component modules
•	Increase Memory/Use More Memory: A common issue with the ELK Docker image is to little memory. Allows server to launch properly 
•	Download and Launch ELK Container: This downloads the ELK docker container and initializes it with the specified ports being published

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
README/Images/docker_ps_output_png



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
•	Web-1, 10.0.0.5 
•	Web-2, 10.0.0.6
•	Web-3, 10.0.0.7

We have installed the following Beats on these machines:
•	Filebeat
•	Metricbeat
These Beats allow us to collect the following information from each machine:
•	Filebeat monitors the log files or locations that you specify, which we use to see what changes or messages the log files have received such as kill commands or SSH login attempts.  
•	Metricbeat records the metrics and statistics from the operation system and from services running on the server, which we could use to look at how much RAM or CPU usage was being used on the webservers at certain time. This is useful in determining if there are any aberant programs or behaviours taking system resources. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
•	Copy the install-elk.yml and filebeat-playbook.yml file to /etc/ansible.
•	Update the install-elk.yml and filebeat-playbook.yml file to include the virtual machine you want to run the playbooks on by adding the webserver and elkserver IP address. You are then able to specify in the playbook.yml file which host you want to install what on. 
•	Run the playbook, and navigate to http://[10.1.0.4]:5601/app/kibana to check that the installation worked as expected.
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
nano ansible.cfg
add the machine, its IP, and ansible_python_interpreter=/usr/bin/python3 to the hosts
Ctrl + x to exit file
in the folder that install-elk.yml is in, run: cp install-elk.yml /etc/ansible
nano install-elk.yml /etc/ansible
name: installing elk hosts: 
Ctrl + x to exit file
ansible-playbook install-elk.yml
