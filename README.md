## OCI-RSA-ANSIBLE-WAZUH
This stack contains the [Wazuh](https://wazuh.com/) cluster Ansible playbook. The cluster consists of a Wazuh master node 
and two worker nodes. The Wazuh cluster is used for security monitoring, threat detection, integrity monitoring, and more.

## Ansible Role: Wazuh Ansible
We are using <b>Galaxy</b> which provides pre-packaged units of work known to Ansible as roles and collections. Content from 
roles and collections of the <b>wazuh-ansible</b> is referenced in Ansible PlayBooks. This playbook installs and 
configures Wazuh agent and manager.

## Ansible Role: Wazuh Cluster

## Code style


[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://github.com/oracle-quickstart)
 

## Branches
* `main` branch contains the latest code.

## Documentation

* [Wazuh Ansible documentation](https://documentation.wazuh.com/current/deploying-with-ansible/index.html)
* [Full documentation](http://documentation.wazuh.com)

## Launching the playbook
```
ansible-playbook -i localhost, $OCI_RSA_BASE/${playbook_name}/main.yml --connection=local 
```

## Tech/framework used

<b>Built with</b>
- [Ansible](https://documentation.wazuh.com/current/deploying-with-ansible/index.html) core 2.11.0 

## Features
What makes your project stand out?

## Code Example
Show what the library does as concisely as possible, developers should be able to figure out **how** your project solves their problem by looking at the code example. Make sure the API you are showing off is obvious, and that your code is short and concise.

## Installation
Provide step by step series of examples and explanations about how to get a development env running.

## API Reference

Depending on the size of the project, if it is small and simple enough the reference docs can be added to the README. For medium size to larger projects it is important to at least provide a link to where the API reference docs live.

## Tests
Describe and show how to run the tests with code examples.

## How to use?
If people like your project they’ll want to learn how they can use it. To do so include step by step guide to use your project.

## How to Contribute
Interested in contributing?  See our contribution [guidelines](CONTRIBUTE.md) for details.

## License
This repository and its contents are licensed under [UPL 1.0](https://opensource.org/licenses/UPL).