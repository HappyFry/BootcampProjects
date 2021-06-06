# BootcampProjects
Location for all cybersecurity bootcamp projects and files.
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(https://github.com/HappyFry/BootcampProjects/blob/main/Images/JumpboxProvisioner.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml
  - filebeatinstall.yml
  - metricbeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available and reliable, in addition to restricting access to the network.
- Load balancers can help deter a DDos attack as the traffic will be diverted. Jump boxes let admins carry out tasks without risk of credentials being stolen.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the machine and system logs.
- Filebeat monitors and watches the logs that you specify.
- Metricbeat records and collects metrics fromt the OS and the services running on the machine.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jumpbox  | Gateway   | 10.0.0.4   | Linux            |
| Web1     | WebServer | 10.0.0.5   | Linux            |
| Web2     | WebServer | 10.0.0.6   | Linux            |
| Web3     | WebServer | 10.0.0.7   | Linux            |
| ElkStack | Monitor   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the DVWA machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 13.83.47.87

Machines within the network can only be accessed by the Jump Box.
- The Jump Box is allowed to access the Elk machine. The IP is 168.62.198.248.

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | No                  | 24.5.14.128          |
| Elk Server | No                  | 168.62.198.248       |
| DVWA       | Yes                 | Any                  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Anytime you want to spin up a new machine you will not need to manually configure it, you would only need to run the playbook and it is all automated.

The playbook implements the following tasks:
- Install docker
- Install python3-pip
- Install docker module
- Increase virtual memory for container
- Download elk image container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!(Images/dockerps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5, 10.0.0.6, 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat and Metricbeat.

These Beats allow us to collect the following information from each machine:
- Filebeat allows us to collect log data and gather it all in a centralized dashboard. It gathers log events and logs that you specify and forwards them for indexing.
- Metricbeat allows us to collect metrics from the operating system and services running on the server. You can use it to check CPU usage, memory, and load on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to /etc/ansible/files.
- Update the config file to include the IP of your elk machine.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

- The playbook is the .yml file and it is located in /etc/ansible/.
- You need to update the playbook file to specify which machine it runs on.
- http://20.98.73.224:5601/app/kibana.
