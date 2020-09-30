# Cybersecurity_Bootcamp
Collection of scripting and other exercises performed during class.
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/Elk-Network.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML files may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.  The load balancer maintains access by distributing traffic between the three vulnerable web servers.  Access controls prevent unauthorized users from accessing these servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the VMs on this network and system metrics like usage, login attempts etc.
- Filebeat monitors log files and their locations.
- Metricbeat monitors all sorts of VM system parameters including CPU, Disk and Network usage.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| DVWA 1   |Web Server| 10.0.0.5   | Linux            |
| DVWA 2   |Web Server| 10.0.0.6   | Linux            |
| DVWA 3   |Web Server| 10.0.0.7   | Linux            |
| ELK      |Monitoring| 10.1.0.4   | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 67.164.184.14

Machines within the network can only be accessed by eachother.
- The ELK machine can be accessed by all three DVWA and the jumpbox machines on the private network.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 67.164.184.14        |
| DVWA 1   | No                  | 10.0.0.0/8           |
| DVWA 2   | No                  | 10.0.0.0/8           |
| DVWA 3   | NO                  | 10.0.0.0/8           |
| ELK      | NO                  | 10.0.0.0/8
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It saves time and resources when deploying virtual machines and networks.
- It ensures consistancy and repeatable results.
- It provides a standardized method for the desired application.

The playbook implements the following tasks:
- Install Docker.io
- Install pip3
- Install Docker Python Module
- Increase and use more virtual memory
- Download and launch docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker-ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- DVWA 1, DVWA 2 and DWVA 3 at 10.0.0.5 through 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat tracks the creation and movement of logs.
- Metricbeat tracks the usage of various system resources including CPU, storage and networking.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk.yml file to /etc/ansible.
- Update the hosts file to include your specifc IP adresses of your VMs
- Run the playbook, and navigate to  Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ the elk.yml file is the playbook you copy it to /etc/ansible.
- _Which file do you update to make Ansible run the playbook on a specific machine? You must update the hosts file. How do I specify which machine to install the ELK server on versus which to install Filebeat on? In the hosts file you define which VMs are web servers and which are elk servers.
- _Which URL do you navigate to in order to check that the ELK server is running?
- http://168.61.18.249:5601/app/kibana (note that your IP will be different)

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
