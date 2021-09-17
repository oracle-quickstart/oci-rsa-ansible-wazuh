Role: Wazuh-Cluster
=========

Installs the Wazuh master and Wazuh worker on the cluster nodes which is used for security monitoring, threat detection, 
integrity monitoring, and more.


Requirements
------------


Role Variables
--------------
```
wazuh_manager_version: "4.1.5-1"
```
Overrides the Wazuh manager version to 4.1.5-1

``` 
wazuh_manager_cluster:
  disable: 'no'
  name: 'wazuh'
  node_name: "{{ ansible_facts['nodename'] }}"
  node_type: '{{ wazuh_node_type }}'
  key: 'ugdtAnd7Pi9myP7CVts4qZaZQEQcRYZa'
  port: '1516'
  bind_addr: '0.0.0.0'
  nodes:
    - 'wazuhmasterinstance.wazuhsubnet.primaryvcn.oraclevcn.com'
  hidden: 'no'
```
Overrides the default configurations of the wazuh manager cluster

```
filebeat_node_name: '{{ ansible_fqdn }}'
```
Overrides the default filebeat node name
```
domain_name: 'wazuhsubnet.primaryvcn.oraclevcn.com'
```
Domain refers to the Wazuh subnet inside the primary VCN
```
filebeat_version: 7.10.2
```
Overrides the filebeat version to 7.10.2
```
wazuh_template_branch: 4.1
```
Overrides the Wazuh template branch to 4.1
```
filebeat_output_elasticsearch_hosts:
  - "elasticnode0.{{ domain_name }}"
  - "elasticnode1.{{ domain_name }}"
  - "elasticnode2.{{ domain_name }}"
```
Sets the output hosts as the ElasticSearch Open Distro nodes
```
filebeat_module_package_url: https://packages.wazuh.com/4.x/filebeat
filebeat_module_package_name: wazuh-filebeat-0.1.tar.gz
filebeat_module_package_path: /tmp/
filebeat_module_destination: /usr/share/filebeat/module
filebeat_module_folder: /usr/share/filebeat/module/wazuh
```
Contains the details of the filebeat package example the url, name of the package etc.
```
local_certs_path: "/etc/ssl/local"
```
The local path to store the generated certificates (OpenDistro security plugin)

Dependencies
------------

A list of other roles hosted on Galaxy:
* geerlingguy.clamav: Installs ClamAV on RedHat Linux server.
* wazuh-ansible: These playbooks install and configure Wazuh agent, manager and Elastic Stack
  - ansible-wazuh-manager: Wazuh Manager role installs and configures Wazuh Manager and Wazuh API
  - ansible-filebeat-oss: This role installs Filebeat which is used with Wazuh Manager to send events and alerts to Elasticsearch.
* oci-rsa-ansible-base: Installs base packages and sets configuration for general security, montoring, and auditing purposes.
    - wazuh-logs: This enables the logging for the Wazuh cluster


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

## How to Contribute
Interested in contributing?  See our contribution [guidelines](CONTRIBUTE.md) for details.

## License
This repository and its contents are licensed under [UPL 1.0](https://opensource.org/licenses/UPL).