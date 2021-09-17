Role: Wazuh-Cluster
=========

Installs the Wazuh master and Wazuh worker on the cluster nodes


Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------
```
wazuh_manager_version: "4.1.5-1"
```
Overrides the Wazuh manager version

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
Overrides the filebeat version
```
wazuh_template_branch: 4.1
```

```
filebeat_output_elasticsearch_hosts:
  - "elasticnode0.{{ domain_name }}"
  - "elasticnode1.{{ domain_name }}"
  - "elasticnode2.{{ domain_name }}"
```
```
filebeat_module_package_url: https://packages.wazuh.com/4.x/filebeat
filebeat_module_package_name: wazuh-filebeat-0.1.tar.gz
filebeat_module_package_path: /tmp/
filebeat_module_destination: /usr/share/filebeat/module
filebeat_module_folder: /usr/share/filebeat/module/wazuh
```

```
local_certs_path: "/etc/ssl/local"
```
The local path to store the generated certificates (OpenDistro security plugin)

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
