ROLE: WAZUH-CLUSTER
=========

Installs the Wazuh Manager and Wazuh Worker on the cluster nodes which is used for security monitoring, threat detection, 
integrity monitoring, and more.


Requirements
------------
This role will work on:

- [Ansible core](https://docs.ansible.com/ansible-core/devel/index.html) >= 2.11.0
- [Oracle Autonomous Linux](https://www.oracle.com/linux/autonomous-linux/) >= 7.9


Role Variables
--------------
Overrides the Wazuh manager version to 4.1.5-1
```
wazuh_manager_version: "4.1.5-1"
```

The wazuh_manager_cluster variable overrides the default configurations of the wazuh manager cluster.  The node type
variable in Wazuh Manager cluster is by default set to `worker`. The `extra-variables.yml` file can be used to override 
this variable to either use `manager` or `worker`.
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

Overrides the default filebeat node name.
```
filebeat_node_name: '{{ ansible_fqdn }}'
```

Domain refers to the Wazuh subnet inside the primary VCN.
```
domain_name: 'wazuhsubnet.primaryvcn.oraclevcn.com'
```

Overrides the filebeat version to 7.10.2
```
filebeat_version: 7.10.2
```

Overrides the Wazuh template branch to 4.1
```
wazuh_template_branch: 4.1
```

Sets the output hosts as the ElasticSearch Open Distro nodes.
```
filebeat_output_elasticsearch_hosts:
  - "elasticnode0.{{ domain_name }}"
  - "elasticnode1.{{ domain_name }}"
  - "elasticnode2.{{ domain_name }}"
```

Sets the details of the filebeat package example the url, name of the package etc.
```
filebeat_module_package_url: https://packages.wazuh.com/4.x/filebeat
filebeat_module_package_name: wazuh-filebeat-0.1.tar.gz
filebeat_module_package_path: /tmp/
filebeat_module_destination: /usr/share/filebeat/module
filebeat_module_folder: /usr/share/filebeat/module/wazuh
```

The local path to store the generated certificates (OpenDistro security plugin).
```
local_certs_path: "/etc/ssl/local"
```


Dependencies
------------
None

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