# Ansible

Run Ansible commands from this directory so `ansible.cfg` is loaded.

```sh
ansible-galaxy collection install -r requirements.yaml
ansible-inventory -i inventories/dev/hosts.ini --list
ansible-playbook -i inventories/dev/hosts.ini site.yml --syntax-check
```

## Layout

- `site.yml`: main infrastructure playbook.
- `inventories/dev/hosts.ini`: development inventory.
- `inventories/ci/hosts.ini`: local inventory used by the CI integration job.
- `group_vars/all.yml`: variables shared by all hosts.
- `roles/`: host preparation, Xray, K3s, Helm CLI, Sealed Secrets, and Argo CD bootstrap roles.
- `requirements.yaml`: Ansible collections used by the roles.

See [`../helm/app/SECRETS.md`](../helm/app/SECRETS.md) for generating and
deploying encrypted PostgreSQL and Redis credentials with Sealed Secrets.

Add hosts to the inventory before running the playbook against infrastructure.
