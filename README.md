# Bootcamp-Projects
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://github.com/erwesteen/Bootcamp-Projects/blob/main/Diagrams/ELK%20Diagram.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive, in addition to restricting access to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.




|  Name    |  Function  |  IP Address |  Operating System  |
|----------|------------|-------------|--------------------|
| Jump Box | Gateway    | 10.3.0.4    | Linux              |
| Web 1    | Server     | 10.2.0.4    | Linux              |
| Web 2    | Server     | 10.2.0.5    | Linux              |
| ELK      | Log Server | 10.2.0.6    | Linux              |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 76.17.137.141

Machines within the network can only be accessed by Jump Box.
- The ELK server can also accept connections from external IP 76.17.137.141

A summary of the access policies in place can be found in the table below.

|  Name    |  Publicly Accessible |  Allowed IP Addresses |
|----------|----------------------|-----------------------|
| Jump Box | Yes                  | 76.17.137.141         |
| Web 1    | No                   | 10.3.0.4              |
| Web 2    | No                   | 10.3.0.4              |
| ELK      | Yes                  | 76.17.137.141         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it automates the process which saves time and creates a repeatable action for future configs.


The playbook implements the following tasks:
- Download and Install docker.io, pip3, and Docker python module
- Download and launch the ELK container docker
- Get more memory to ensure the containers run smooth

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](https://github.com/erwesteen/Bootcamp-Projects/blob/main/Ansible/Elk.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.2.0.4 and 10.2.0.5

We have installed the following Beats on these machines:
- FileBeat and MetricBeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log files and saves the log data to Elasticsearch. Metricbeat monitors servers and collects metrics that are running. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to your Web VMs.
- Update the hosts file to include the the IP address' of your Web VMs and ELK VM
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.


Which file is the playbook? Where do you copy it?
- Config files that you copy to etc/ansible/filebeat-config.yml and etc/ansible/Metricbeat-config.yml

Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
- The config file and specify the IP address for the machine.

Which URL do you navigate to in order to check that the ELK server is running? 
- http://[your.VM.IP]:5601/app/kibana


