## OCI-RSA-ANSIBLE-WAZUH
This project contains the Wazuh cluster Ansible playbook. This stands up the Wazuh cluster which consists of a Wazuh 
Master node and two Wazuh Worker nodes. The cluster is used for security monitoring, threat detection, integrity monitoring, 
and more.

## Ansible Role: Wazuh-Cluster
More information on the Wazuh-Cluster can be found [here](/wazuh-cluster/README.md).

## Ansible Role: Wazuh-Logs
This enables the logging for the Wazuh cluster.

## Ansible Role: Wazuh Ansible
We are using <b>Galaxy</b> which provides pre-packaged units of work known to Ansible as roles and collections. Content from 
roles and collections of the <b>wazuh-ansible</b> is referenced in Ansible PlayBooks. This playbook installs and 
configures Wazuh agent and manager.

## Ansible Role: OCI-RSA-ANSIBLE-BASE
More information on the oci-rsa-ansible-base can be found [here](https://bitbucket.oci.oraclecorp.com/projects/RSA/repos/oci-rsa-ansible-base).



## Code style


[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://github.com/oracle-quickstart)
 

## Branches
* `main` branch contains the latest code.


## Usage
* Launching the playbook:
    ```
    ansible-playbook -i localhost, $OCI_RSA_BASE/${playbook_name}/main.yml --connection=local 
    ```
* General usage
This is used to stand up the Wazuh cluster which consists of a Wazuh Master node and two Wazuh Worker nodes, which is 
used for security monitoring, threat detection, integrity monitoring, and more.

## Requirements

This project is built with:
- [Ansible](https://documentation.wazuh.com/current/deploying-with-ansible/index.html) 

Dependencies
------------

A list of other roles hosted on Galaxy:
* [geerlingguy.clamav](https://github.com/geerlingguy/ansible-role-clamav): Installs ClamAV on RedHat Linux server.
* [wazuh-ansible](https://github.com/wazuh/wazuh-ansible): These playbooks install and configure Wazuh agent, manager and 
  Elastic Stack
  - [ansible-wazuh-manager](https://github.com/wazuh/wazuh-ansible/tree/master/roles/wazuh/ansible-wazuh-manager): Wazuh
    Manager role installs and configures Wazuh Manager and Wazuh API
  - [ansible-filebeat-oss](https://github.com/wazuh/wazuh-ansible/tree/master/roles/wazuh/ansible-filebeat-oss): This role 
    installs Filebeat which is used with Wazuh Manager to send events and alerts to Elasticsearch.

A list of other roles hosted on Github:
* [oci-rsa-ansible-base](https://bitbucket.oci.oraclecorp.com/projects/RSA/repos/oci-rsa-ansible-base): Installs base 
  packages and sets configuration for general security, montoring, and auditing purposes.
    


Example Playbook
----------------

An example of how to use the roles:

    ---
    - hosts: all
      vars_files:
        - ../extra-variables.yml
      roles: 
        - role: oci-rsa-ansible-base
          become: true
        - role: wazuh-cluster
          become: true
        - role: geerlingguy.clamav
          become: true
        - role: wazuh-ansible/wazuh-ansible/roles/wazuh/ansible-wazuh-manager
          become: true
        - role: wazuh-ansible/wazuh-ansible/roles/wazuh/ansible-filebeat-oss
          become: true
        - role: wazuh-logs
          become: true

## Documentation

* [Wazuh Ansible documentation](https://documentation.wazuh.com/current/deploying-with-ansible/index.html)
* [Full documentation](http://documentation.wazuh.com)

## How to Contribute
Interested in contributing?  See our contribution [guidelines](CONTRIBUTE.md) for details.

## License
This repository and its contents are licensed under [UPL 1.0](https://opensource.org/licenses/UPL).