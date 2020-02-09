Role Name
=========

nvidia: Nvidia

[![Build Status](https://travis-ci.org/cmihai-ansible/nvidia.svg?branch=master)](https://travis-ci.org/cmihai-ansible/nvidia)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.nvidia](https://galaxy.ansible.com/devopstoolbox.nvidia)

```bash
ansible-galaxy install devopstoolbox.nvidia
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
nvidia_packages_state: present
nvidia_remove_packages: true
nvidia_enable_service: true
nvidia_enable_selinux: true
nvidia_copy_templates: true
nvidia_firewall_configure: true
nvidia_firewall_rules:
  - service: ssh
  - port: 3389
nvidia_users:
  - user: devops
    group: docker
nvidia_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install nvidia on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: nvidia is configured
      import_role:
        name: devopstoolbox.nvidia
      vars:
        nvidia_packages_state: present
        nvidia_remove_packages: true
        nvidia_enable_service: true
        nvidia_enable_selinux: true
        nvidia_copy_templates: true
        nvidia_firewall_configure: true
        nvidia_firewall_rules:
          - service: ssh
          - port: 3389
        nvidia_users:
          - user: devops
            group: docker
        nvidia_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: nvidia
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
