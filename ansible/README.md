# Ansible

Basic Ansible project scaffold. Run commands from this directory so Ansible
loads `ansible.cfg` automatically.

```sh
ansible-inventory --list
ansible-playbook -i inventories/dev/hosts.yml playbooks/site.yml --check
```

## Layout

- `inventories/dev/hosts.yml`: development inventory (currently empty).
- `group_vars/all.yml`: variables shared by all hosts.
- `playbooks/site.yml`: starting playbook for host configuration.
- `roles/`: reusable roles as the project grows.

Add hosts to the inventory before running against real infrastructure.
