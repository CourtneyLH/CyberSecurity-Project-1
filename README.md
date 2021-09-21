# CyberSecurity-Project-1
CC_Cybersecurity_Bootcamp_Project_1


## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Elk_Network_Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible.cfg file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml
  - hosts.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- A Jump box allows a secure way to access a network, via SSH. The load balancers protect from unauthenticated access, increase relizbility, prevent applications from vulnerable threats like traffic caching. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- Filebeat watches for changes in log files.
- Metricbeat records metrics from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name    | Function  | IP Address | Operating System |
|---------|-----------|------------|------------------|
| Jumpbox | Gateway   | 10.0.0.4   | Linux            |
| Elk-VM  | Server VM | 10.1.0.5   | Linux            |
| Web-1   | DVWA      | 10.0.0.5   | Linux            |
| Web-1   | DVWA      | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 98.202.65.128

Machines within the network can only be accessed by RedAdmin.
- ELK only accessible from 98.202.65.128

A summary of the access policies in place can be found in the table below.

| Name    | Publicly Accessible | Allowed IP Addresses |
|---------|---------------------|----------------------|
| Jumpbox | Yes                 | 98.202.65.128        |
| Elk-VM  | Yes                 | 98.202.65.128        |
| Web-1   | No                  | 10.0.0.4             |
| Web-1   | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Easy to use and easy to configure and deploy services.

The playbook implements the following tasks:
- Install docker.io
- Install apt module python
- Install Docker Module
- Download and launch a docker elk container
- Enable docker service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!/Images/Success_docker_ps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat watches for changes in log files.
- Metricbeat records metrics from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/roles directory.
- Update the hosts file to include the private IP of the specific machine you want to run. Put the IP under the category [Webservers] for the filebeat install vs [Elk] for the elk server install.
- Run the playbook, and navigate to http:// 20.110.62.193/app/kibana to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ansible-playbook filebeat-playbook.yml