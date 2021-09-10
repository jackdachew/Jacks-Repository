# Jacks-Repository [README.txt]

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

! Images/Jack Berkowitz Unit 11 Week 12 homework

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the /etc/ansible/roles file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be stable, in addition to authenticating access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.

| Name                 | Function | IP Address | Operating System |
|----------------------|----------|------------|------------------|
| Jump-Box-Provisioner | Gateway  | 10.0.0.5   | Linux            |
| Vmelk                | Kibana   | 10.1.0.4   | Linux            |
| Web-1                | DVMA     | 10.0.0.6   | Linux            |
| Web-2                | DVMA     | 10.0.0.7   | Linux            |
| Web-3                | DVMA     | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 72.208.29.47

Machines within the network can only be accessed by Jump-Box-Provisioner (10.0.0.5)

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes                 | 72.208.29.47         |
| Vmelk                | No                  | 10.0.0.5             |
| Web-1                | No                  | 10.0.0.5             |
| Web-2                | No                  | 10.0.0.5             |
| Web-3                | No                  | 10.0.0.5             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it made sure all devices had the same programs and versions.

The playbook implements the following tasks:

- The first 3 steps in this play book installs docker.io, adds python3 and installs the python docker program.

- The next steps first increase the amount of memory used by the system so it can properly run the docker elk container which has the published ports 5601,9200, and 5044 running.

- The final step is enabling the docker service on boot so docker starts every time the machine is booted up.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/docker_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

10.0.0.6
10.0.0.7
10.0.0.8

We have installed the following Beats on these machines:
Metricbeat and Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat is collecting log events and files that we specify for it to watch. While we have that running, Metricbeat collects requests and services that are run on the server. 


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install_elk.yml file to /etc/ansible.
- Update the host file to include your IP address
- Run the playbook and navigate to (your ip address)/app/kibana to check that the installation worked as expected.

