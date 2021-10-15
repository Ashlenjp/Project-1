## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: filebeat-playbook.yml

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
- _TODO: What aspect of security do load balancers protect? Load balancers protectr from DDos attacks. What is the advantage of a jump box?_To give access to the user from a single node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
- _TODO: What does Filebeat watch for?_Filebeat watches for any information in the file system which has been changed and when it has.
- _TODO: What does Metricbeat record?_ Compiles the metrics and statistics that collects and ships them to the specified output.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |  Server  | 10.0.0.5   | Linux            |
| Web-2    |  Server  | 10.0.0.6   | Linux            |
| Elkserver|  Server  | 10.1.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Local IP Address

Machines within the network can only be accessed by DVWA container whithin Jump Box VM.
- _TODO: My personal machine was allowed accress as well as the Jump Box VM via peering connection.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
| Web-1    | No                  |   10.0.0.1           |
| Web-2    | No                  |   10.0.0.1           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
Answer: It allowed us to avoid configuring it manually, thus minimizing the chance for errors.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker
- Download Image
- Configure container
- create the playbook to install the container with docker and filebeart and metricbeat
- run the playbook to launch the container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
Web-Server 1: 10.0.0.5
Web-Server 2: 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Filebeat and MetricBeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filbeat collets logs for each of the virtual machines such as visitor information and error reports
Metricbeat provides information such as CPU Usage and Memory Usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml and metricbeat-playbook.yml file to ansible directory.
- Update the hosts file to include...Private ip addresses for the machines.
- Run the playbook, and navigate to public ip address of the elk VM on port 5601 to check that the installation worked as expected.

_