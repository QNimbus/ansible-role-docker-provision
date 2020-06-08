# Ansible Role docker_provision

[![GitHub last commit (branch)](https://img.shields.io/github/last-commit/qnimbus/ansible-role-docker-provision/master?style=for-the-badge)](https://github.com/QNimbus/ansible-role-docker-provision) [![Travis (.org) branch](https://img.shields.io/travis/qnimbus/ansible-role-docker-provision/master?style=for-the-badge)](https://travis-ci.org/github/QNimbus/ansible-role-docker-provision)
## Role Variables

TODO

## Example Playbook

Inventory example

```ini
[containers]
apollo image="qnimbus/ansible-ubuntu:20.04"
ares image="qnimbus/ansible-ubuntu:20.04"
```

Playbook example

```yaml
---
- name: Bring up docker containers using Docker connection
  hosts: localhost
  roles:
    - role: docker_provision
      docker_provision_privileged: true,
      docker_provision_inventory_group: "{{ groups['containers'] }}"
      docker_provision_use_docker_connection: true

- hosts: containers
  tasks:
    - name: Ensure containers are online
      ping:
```

Or using a dynamic inventory

```yaml
---
- name: Bring up docker containers using Docker connection
  hosts: localhost
  vars:
    inventory:
      - name: apollo
      - name: ares
        image: 'qnimbus/ansible-ubuntu:20.04'
      - name: hera
        image: 'qnimbus/ansible-ubuntu:20.04'
  roles:
    - { role: docker_provision, docker_provision_privileged: true, docker_provision_inventory: '{{ inventory }}' }
```

## TODO

## License

[MIT](LICENSE)