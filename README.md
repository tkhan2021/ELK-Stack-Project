# ELK-Stack-Project

Tanveer Khan 04/03/2021 SMU Cybersecurity Boot Camp

This is a collection of Linux scripts and Ansible scripts from my Cybersecurity Bootcamp class.

The scripts are used to configure cloud servers with different docker containers.

The final setup was 4 servers running vulnerable DVWA containers along with a JumpBox and a server running an ELK Stack container.

![image](https://user-images.githubusercontent.com/74847116/127726650-730e7627-7b1e-4340-b4b7-44b6b8a1a9ea.png)

These files have been tested and are now being used to create a live ELK deployment on Azure. They may be used to re-create the whole deployment seen in the image above. Select components of the playbook (.yml) file, such as Filebeat, can also be used to install only certain parts of it.

The following ansible-playbooks are needed to create and install DVWA and the ELK-server:

Please use the .yml links above to view playbook codes.

This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build

Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. Load Balancing ensures availability to the web-servers which is the availability aspect of security in regards to the CIA Triad.

What is the advantage of a jump box? The main advantage of using a JumpBox is having one origination point for administrative tasks. This ultimately sets the JumpBox as a Secure Admin Workstation (SAW). In order to conduct administrative tasks administrators are required to access the JumpBox before accessing the other servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

Filebeat watches for log files/locations and collect log events. (Filebeat: Lightweight Log Analysis & Elasticsearch)
Metricbeat records metrics and statistical data from the operating system and from services running on the server (Metricbeat: Lightweight Shipper for Metrics)

The configuration details of each machine may be found below.



Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Personal IP Address

Machines within the network can only be accessed by SSH.

The ELK-Server is only accessible by SSH from the JumpBox and via web access from Personal IP Address.
A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Address
Jump-Box	No	Personal IP Address
Web-1	Yes Thru Load Ballancer	13.66.204.159 LB Public IP 10.0.0.4 - JumpBox
Web-2	Yes Thru Load Ballancer	13.66.204.159 LB Public IP 10.0.0.4 JumpBox
ELK-Server	No	SSH 10.0.0.4 - JumpBox HTTP Port 5601 Personal IP

Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

The main advantage of automating the installation process is that we could deploy multiple servers easily and quickly without having to physically touch each server.
The playbook implements the following tasks:

Install Docker.io and pip3
Increases VM memory
Download and Configure elk docker container
Sets Published Ports

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

![docker-ps](https://user-images.githubusercontent.com/74847116/127727841-acccfd8a-2995-46ae-9236-05bc7078788b.png)

Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web-1 10.1.5
Web-2 10.1.6
We have installed the following Beats on these machines:

Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat watches for log files/locations and collect log events. (Filebeat: Lightweight Log Analysis & Elasticsearch)
Metricbeat records metrics and statistical data from the operating system and from services running on the server (Metricbeat: Lightweight Shipper for Metrics)
Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the filebeat-config.yml and metricbeat-config.yml file to /etc/ansible/files.
Update the configuration files to include the Private IP of the ELK-Server to the ElasticSearch and Kibana Sections of the Configuration File
Run the playbook, and navigate to ELK-Server-PublicIP:5601/app/kibana to check that the installation worked as expected.
Which file is the playbook? The playbook files are:
