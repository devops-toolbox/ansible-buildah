Role Name
=========

ansible-buildah: Ansible-buildah

[![Build Status](https://travis-ci.org/cmihai-ansible/ansible-buildah.svg?branch=master)](https://travis-ci.org/cmihai-ansible/ansible-buildah)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.ansible-buildah](https://galaxy.ansible.com/devopstoolbox.ansible-buildah)

```bash
ansible-galaxy install devopstoolbox.ansible-buildah
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
ansible-buildah_packages_state: present
ansible-buildah_remove_packages: true
ansible-buildah_enable_service: true
ansible-buildah_enable_selinux: true
ansible-buildah_copy_templates: true
ansible-buildah_firewall_configure: true
ansible-buildah_firewall_rules:
  - service: ssh
  - port: 3389
ansible-buildah_users:
  - user: devops
    group: docker
ansible-buildah_selinux_booleans:
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
- name: Install ansible-buildah on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: ansible-buildah is configured
      import_role:
        name: devopstoolbox.ansible-buildah
      vars:
        ansible-buildah_packages_state: present
        ansible-buildah_remove_packages: true
        ansible-buildah_enable_service: true
        ansible-buildah_enable_selinux: true
        ansible-buildah_copy_templates: true
        ansible-buildah_firewall_configure: true
        ansible-buildah_firewall_rules:
          - service: ssh
          - port: 3389
        ansible-buildah_users:
          - user: devops
            group: docker
        ansible-buildah_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: ansible-buildah
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
