## OCI-RSA-ANSIBLE-WAZUH
This stack contains the [Wazuh](https://documentation.wazuh.com/current/index.html) cluster Ansible playbook. This stands 
up the Wazuh cluster which consists of a Wazuh manager node and two Wazuh worker nodes. The cluster is used for security 
monitoring, threat detection, integrity monitoring, and more.

## Ansible Role: wazuh-cluster
We developed this role to stand up the Wazuh cluster based on the configurations and requirements. Installs the Wazuh manager 
and Wazuh worker on the target instances. More information on the wazuh-cluster role and role variables can be found 
[here](/wazuh-cluster/README.md).

## Ansible Role: wazuh-logs
Enables the logging for the Wazuh Cluster.

## Ansible Role: wazuh-ansible
We are using <b>Galaxy</b> which provides pre-packaged units of work known to Ansible as roles and collections. Content from 
roles and collections of the <b>wazuh-ansible</b> are referenced in oci-rsa-ansible-wazuh. This playbook installs and 
configures Wazuh agent and manager.

## Ansible Role: oci-rsa-ansible-base
Installs base packages and sets configuration for general security, monitoring, and auditing purposes. More information 
on the oci-rsa-ansible-base can be found [here](PLACEHOLDER).

## Requirements

- [Ansible core](https://docs.ansible.com/ansible-core/devel/index.html) >= 2.11.0
- [Oracle Autonomous Linux](https://www.oracle.com/linux/autonomous-linux/) >= 7.9

Dependencies
------------

A list of other roles hosted on Galaxy:
* [geerlingguy.clamav](https://github.com/geerlingguy/ansible-role-clamav): Installs ClamAV on Linux server.
* [wazuh-ansible](https://github.com/wazuh/wazuh-ansible): These playbooks install and configure Wazuh Agent, Manager and 
  Elastic Stack
  - [ansible-wazuh-manager](https://github.com/wazuh/wazuh-ansible/tree/master/roles/wazuh/ansible-wazuh-manager): This role 
    installs and configures Wazuh Manager and Wazuh API
  - [ansible-filebeat-oss](https://github.com/wazuh/wazuh-ansible/tree/master/roles/wazuh/ansible-filebeat-oss): This role 
    installs Filebeat which is used with Wazuh Manager to send events and alerts to Elasticsearch.

A list of other roles hosted on Github:
* [oci-rsa-ansible-base](PLACEHOLDER): Installs base 
  packages and sets configuration for general security, monitoring, and auditing purposes.

## Branches
* `main` branch contains the latest code.

## Usage

There are multiple ways to run Ansible playbook, but for our project we choose to pull down the bundled playbook from 
the OCI Object Storage bucket and then run the following command to configure each of the hosts locally.

```
ansible-playbook -i localhost, $OCI_RSA_BASE/${playbook_name}/main.yml --connection=local
```

An `extra_variables.yml` file is required to set the variables below. Here the Wazuh password, Open Distro Elasticsearch 
security password, Wazuh bucket name, and the node type can be set by the user.
```
wazuh_api_users:
  - username: "wazuh"
    password: "${}"
elasticsearch_security_password: "${}"
wazuh_backup_bucket_name: "${}"
wazuh_node_type: "${}"
```
This is a wrapper which configures the Wazuh cluster. To deploy the infrastructure and configure the cluster on instance nodes,
our team recommends a specific workflow. Detailed explanation of the recommended workflow can be found [here](WORKFLOW.md). 

## Documentation

* [Wazuh Ansible documentation](https://documentation.wazuh.com/current/deploying-with-ansible/index.html)
* [Full documentation](http://documentation.wazuh.com)

## The Team
This repository was developed by the Oracle OCI Regulatory Solutions and Automation (RSA) team.

## How to Contribute
Interested in contributing?  See our contribution [guidelines](CONTRIBUTE.md) for details.

## License
This repository and its contents are licensed under [UPL 1.0](https://opensource.org/licenses/UPL).