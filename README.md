# Project-13
The files in this repository were used to configure the network depicted below.

![](Diagrams/elk%20stack.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting overloading to the network.
 What aspect of security do load balancers protect? What is the advantage of a jump box? 
Load balancers defend against denial-of-service (DDoS) attacks.  The advantage of a jump box is to be used as an origination point to connect to servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the applications and system logs.
What does Filebeat watch for?  Filebeat monitors the log files and locations you specifically need.
 What does Metricbeat record? Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify.
The configuration details of each machine may be found below.
|     Name           |     Function              |     Private IP   address    |     Operating   System    |
|--------------------|---------------------------|-----------------------------|---------------------------|
|     Jump Box       |     Point of Access       |     10.0.0.4                |     Linux                 |
|     Elk-Stack      |     Log Server            |     10.1.0.4                |     Linux                 |
|     Webserver 1    |     Server                |     10.0.0.5                |     Linux                 |
|     Webserver 2    |     Server                |     10.0.0.6                |     Linux                 |


Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
Any IP address that has permission from the Jump Box inbound rules.

Machines within the network can only be accessed by The Jump-Box-Provisioner.
 Which machine did you allow to access your ELK VM? The Jump-Box-Provisioner.
What was its IP address? 10.0.0.4

A summary of the access policies in place can be found in the table below.
| Name          | Publicly Accessible | Allowed IP Addresses |
|---------------|---------------------|----------------------|
| Jump Box      | YES                 | 10.0.0.4             |
| Elk-Stack     | YES                 | 10.1.0.4             |
| Webserver 1   | NO                  | 10.0.0.5             |
| Webserver 2   | NO                  | 10.0.0.6             |
| Load Balancer | YES                 | STATIC               |


Elk Configuration
[install-ELK](Ansible/Install-elk.yml)




Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because... makes easier to install.
 What is the main advantage of automating configuration with Ansible? Very simple to set up and use also it lets you model even highly complex IT workflows.

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
1 collection of data
2 data aggregation and processing
3 indexing and storage
4 analysis and visualization


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
 



 Target Machines & Beats
This ELK server is configured to monitor the following machines: Webserver 1 and Webserver 2
List the IP addresses of the machines you are monitoring. Webserver 1 IP 10.0.0.5  Webserver IP 10.0.0.6

We have installed the following Beats on these machines: Jump-Box-Provisioner and Elk-Stack
 Specify which Beats you successfully installed. 

These Beats allow us to collect the following information from each machine:
In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server.
Filebeat  uses a backpressure-sensitive protocol when sending data to Logstash or Elasticsearch to account for higher volumes of data.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible configuration file to Elk-Stack container.
- Update the Host file to include IP addresses of Webservers and Elk-Stack.
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.

 Answer the following questions to fill in the blanks.
-Which file is the playbook? Ansible
 Where do you copy it? To Elk-Stack Container
Which file do you update to make Ansible run the playbook on a specific machine? Ansible Configuration file.
 How do I specify which machine to install the ELK server on versus which to install Filebeat on? Using Elk-Stack IP address
Which URL do you navigate to in order to check that the ELK server is running? Kibana


