## OCI-RSA-Ansible-Wazuh
This project contains the Wazuh cluster Ansible playbook. This stands up the Wazuh cluster which consists of a Wazuh 
Master node and two Wazuh Worker nodes. The cluster is used for security monitoring, threat detection, integrity monitoring, 
and more.

## Ansible Role: Wazuh Ansible
We are using <b>Galaxy</b> which provides pre-packaged units of work known to Ansible as roles and collections. Content from 
roles and collections of the <b>wazuh-ansible</b> is referenced in Ansible PlayBooks. This playbook installs and 
configures Wazuh agent and manager.

## Ansible Role: OCI-RSA-Ansible-Base


## Ansible Role: Wazuh-Cluster

## Code style


[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://github.com/oracle-quickstart)
 

## Branches
* `main` branch contains the latest code.


## Usage
Launching the playbook:
```
ansible-playbook -i localhost, $OCI_RSA_BASE/${playbook_name}/main.yml --connection=local 
```
This is used to stand up the Wazuh cluster which consists of a Wazuh Master node and two Wazuh Worker nodes, which is 
used for security monitoring, threat detection, integrity monitoring, and more.

## Requirements

This project is built with:
- [Ansible](https://documentation.wazuh.com/current/deploying-with-ansible/index.html) 

## Documentation

* [Wazuh Ansible documentation](https://documentation.wazuh.com/current/deploying-with-ansible/index.html)
* [Full documentation](http://documentation.wazuh.com)

## How to Contribute
Interested in contributing?  See our contribution [guidelines](CONTRIBUTE.md) for details.

## License
This repository and its contents are licensed under [UPL 1.0](https://opensource.org/licenses/UPL).