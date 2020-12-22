## Automated ELK Stack Deployment
 
The files in this repository were used to configure the network depicted below.
 
https://github.com/TurbineDriver/Cybersecurity/blob/main/Diagrams/ELK_Network.png
 
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the pentest.yml (ansible playbook) file may be used to install only certain pieces of it, such as Filebeat.
 
  https://github.com/TurbineDriver/Cybersecurity/blob/main/Ansible/Yaml%20Playbook%20Install%20and%20Launch%20Filebeat.txt


 
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
 
 
### Description of the Topology
 
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
 
Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box? Load balancers help protect the Availability of network servers.  A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments.
 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system data.
- What does Filebeat watch for? Filebeat monitors the log files or locations that you specify.
- What does Metricbeat record? Metricbeat collects metrics from the system and services running on the server.
 
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
 
| Name         | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.15  | Linux            |
| Web-1        |  VM      | 10.0.0.12  | Linux            |
| Web-2         |  VM       |  10.0.0.13 | Linux            |
| Web-3         |  VM       |  10.0.0.17 | Linux            |
 
### Access Policies
 
The machines on the internal network are not exposed to the public Internet.
 
Only the ELK machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Whitelisted IP addresses: (my host machine)
 
Machines within the network can only be accessed by jump box.
- Which machine did you allow to access your ELK VM? What was its IP address? Jump box 104.209.43.53
 
A summary of the access policies in place can be found in the table below.
 
| Name         | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                     | My Host Machine IP   |
|   ELK           | Yes                    |jump box,http port 80, port 5601|                     
|              |                |                          |
 
### Elk Configuration
 
Ansible was used to automate the configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? All functions (ie. starting, updating, and installing) are performed autonomously.
 
The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- After the VM was created for the ELK server it was added to the ansible hosts file 
- Created a new ansible-playbook to configure our new ELK VM
- The playbook installed docker.io, python3-pip, and docker.
- After Docker is installed, download and run the sebp/elk:761    container.
- After the ELK container is installed, SSH to your container and double-check that your elk-docker container is running.
 
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
 
https://drive.google.com/file/d/1X1sa4Qdf89Lty1zhS2fSBLCW-l5LQXD8/view?usp=sharing


 
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.12
- Web-2 10.0.0.13
- Web-3 10.0.0.17
 
We have installed the following Beats on these machines:
- Filebeat
- Metricbeat
 
These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files or locations that you specify.
- Metricbeat collects metrics from the system and services running on the server.


 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
 
SSH into the control node and follow the steps below:
- Copy the ansible configuration file to the container.
- Update the hosts file to include the three VM’s IP addresses.
- Run the playbook, and navigate to Kibana http://[your.VM.IP]:5601/app/kibana.
 to check that the installation worked as expected.


 _As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
This is the command to run the playbook:
 ansible-playbook /etc/ansible/pentest.yml