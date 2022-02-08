# Yaml-Bash-Scripts
Cloud networking / Elk Stack scripts from GW Cybersecurity Bootcamp
# Cloud Network
This is a collection of Linux Scripts and Ansible Scripts from my CyberClass.

Most of the scripts are used to configure cloud servers with differnt docker containers.

The final setup was 4 servers running vulnerable DVWA containers along with a jump box and a server running an ELK stack container.

![](https://github.com/jhess7/Yaml-Bash-Scripts/blob/9e8012bbbd9bb25a76d452855847c4e881efc874/diagrams/AzureCloud.drawio.png)
![](https://github.com/jhess7/Yaml-Bash-Scripts/blob/9e8012bbbd9bb25a76d452855847c4e881efc874/diagrams/ELK-Stack.drawio.png)

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://github.com/jhess7/Yaml-Bash-Scripts/blob/9e8012bbbd9bb25a76d452855847c4e881efc874/diagrams/ELK-Stack.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _yaml_ file may be used to install only certain pieces of it, such as Filebeat.

  - [Elk playbook](https://github.com/jhess7/Yaml-Bash-Scripts/blob/9e8012bbbd9bb25a76d452855847c4e881efc874/ansible/install-elk.yml)
  - [Filebeat-Metricbeat playbook](https://github.com/jhess7/Yaml-Bash-Scripts/blob/9e8012bbbd9bb25a76d452855847c4e881efc874/ansible/roles/filebeat-metricbeat-playbook.yml)
  - [DVWA playbook](https://github.com/jhess7/Yaml-Bash-Scripts/blob/9e8012bbbd9bb25a76d452855847c4e881efc874/ansible/pentest.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting access to the network.
- What aspect of security do load balancers protect? Load balancers protects reliability and increases capacity What is the advantage of a jump box? it provides a secure computer that all admins must first connect to

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the sever and system logs.
- What does Filebeat watch for? log files
- What does Metricbeat record? metrics from the operating system and services

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function | IP Address | Operating System |
|---------- |----------|------------|------------------|
| Jump Box  | Gateway  | 10.0.0.1   | Linux            |
| Web-1     |          | 10.0.0.4   |   Linux          |
| Web-2     |          | 10.0.0.5   |  Linux           |
| Web-3     |          |  10.0.0.6  | Linux               
| Elk       | Elk Stack| 10.0.0.7   | Linux

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk Stack machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 73.172.244.86 

Machines within the network can only be accessed by SSH.
- My local machine 73.172.244.86 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4 73.172.244.86  |
|  Web-1   | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Web-3    | No                  |  10.0.0.4            |              
| Elk      | Yes                 |   73.172.244.86      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? it's simple to use and setup; it's powerful, and agentless

The playbook implements the following tasks:
- install docker
- install python3 pip
- increse memory
- download and install elk container
- enable service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](https://github.com/jhess7/Yaml-Bash-Scripts/blob/9e8012bbbd9bb25a76d452855847c4e881efc874/yaml_docker_check.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5, 10.0.0.6, 10.0.0.4

We have installed the following Beats on these machines:
- filebeats and metricbeats

These Beats allow us to collect the following information from each machine:
- They collect system log files

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Edit the inventory file under /etc/ansible/hosts
- Add a group [elk]
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? elk-playbook.yaml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Ansible runs a playbook on the hosts in the inventory file; you specify which machine to run by using groups
- _Which URL do you navigate to in order to check that the ELK server is running? http://localipaddress:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
