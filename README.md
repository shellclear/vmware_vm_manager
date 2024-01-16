vmware_vm_manager 
=========

Manage VMs on vsphere

Requirements
------------

Python requirements on the control node runnig the automation
- pyVmomi>=6.7
- git+https://github.com/vmware/vsphere-automation-sdk-python.git
- python_version >= '2.7'  # Python 2.6 is not supported

Role Variables
--------------

| Name                                           | Default value                                           |                                                               |
|------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------|
| vmware_vm_manager_hostname                     | UNDEF                                                   | Specify vsphere url                                           |
| vmware_vm_manager_port                         | 443                                                     | Specify vsphere port                                          |
| vmware_vm_manager_validate_certs               | true                                                    | Check ssl certificates                                        |
| vmware_vm_manager_username                     | UNDEF                                                   | Specify vmware username                                       |
| vmware_vm_manager_password                     | UNDEF                                                   | Specify vmware password                                       |
| vmware_vm_manager_datacenter                   | UNDEF                                                   | Specify vmware datacenter                                     |
| vmware_vm_manager_cluster                      | UNDEF                                                   | Specify vmware cluster                                        |
| vmware_vm_manager_esxi_hostname                | UNDEF                                                   | vm host where deploy vm, this conflict with cluster name var  |
| vmware_vm_manager_datastore                    | UNDEF                                                   | Datastore to use, check datastore precedence on disk var      |
| vmware_vm_manager_folder                       | UNDEF                                                   | Datastore folder                                              |
| vmware_vm_manager_proxy_host                   | UNDEF                                                   | Specify proxy for vmware                                      |
| vmware_vm_manager_proxy_port                   | UNDEF                                                   | Specify proxy port for vmware                                 |
| vmware_vm_manager_name                         | UNDEF                                                   | vm name                                                       |
| vmware_vm_manager_annotation                   | "Created by Ansible"                                    | Annotation to apply on vm                                     |
| vmware_vm_manager_state                        | present                                                 | vm state                                                      |
| vmware_vm_manager_template                     | UNDEF                                                   | vm template name                                              |
| vmware_vm_manager_disk                         | []                                                      | vm disk list to create                                        |
| vmware_vm_manager_hardware                     | []                                                      | vm hardware definition list                                   |
| vmware_vm_manager_networks                     | []                                                      | vm network list                                               |
| vmware_vm_manager_vm_tag_names                 | []                                                      | List of tags to apply to vm                                   |
| vmware_vm_manager_tag_category_name            | UNDEF                                                   | Tag category name                                             |
| vmware_vm_manager_tag_category_description     | UNDEF                                                   | Tag category description                                      |
| vmware_vm_manager_create_tag_name              | UNDEF                                                   | Name of the tag to create                                     |   
| vmware_vm_manager_create_tag_description       | UNDEF                                                   | Description of the tag                                        |

Dependencies
------------

None

Example Playbook
----------------

```yaml
---
- name: "Create VM on VMware hypervisor"
  hosts: "localhost"
  gather_facts: false
  vars:
    vmware_vm_manager_hostname: "vmware.portal.local.domain"
    vmware_vm_manager_username: "vmware_username"
    vmware_vm_manager_datacenter: "datacenter_name"
    vmware_vm_manager_datastore: "datastore_name"
    vmware_vm_manager_folder: "folder/dir"
    vmware_vm_manager_name: "vmname"
    vmware_vm_manager_template: "template_name"
    vmware_vm_manager_disk:
      - size_gb: 10
        type: "thin"
    vmware_vm_manager_hardware:
      memory_mb: 2048
      num_cpus: 4
      num_cpu_cores_per_socket: 2
    vmware_vm_manager_networks:
      - name: "network_name"
        vlan: 0
  roles:
    - "vmware_vm_manager"
...
```

License
-------

MIT License

Author Information
------------------

shellclear@gmail.com