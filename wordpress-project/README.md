# WordPress Ansible Lab

This lab uses Ansible to set up a WordPress server. The playbook runs three
roles in order: `stack_install` installs the packages, `stack_config`
configures the services, and `wordpress` installs WordPress and its plugins.

## Before running

The inventory in `hosts.ini` targets `tp_cs320_al10` at `10.2.37.105` and
connects as `kjohnson`. Make sure the SSH key path in that file works from
your Ansible control machine.

The tasks use `dnf` and RPM-style PHP paths, so the target is expected to be
an RPM-based Linux system (like Alma Linux). Confirm the target OS and adjust package or service names if needed.

Install the required MySQL collection from this directory:

```sh
ansible-galaxy collection install -r requirements.yml
```

The local, encrypted `group_vars/vault.yml` file is ignored by Git. Create it with:

```sh
ansible-vault create group_vars/vault.yml
```

It needs `vault_email`, `vault_wp_admin_password`, and `vault_wp_db_password`.
Keep the vault password and any private keys out of the repository.

## Run and check the playbook

Run these commands from the `wordpress-project` directory. Ansible will
prompt for the vault password when needed.

```sh
ansible -i hosts.ini wordpress_servers -m ping
ansible-playbook -i hosts.ini site.yml --syntax-check --ask-vault-pass
ansible-playbook -i hosts.ini site.yml --ask-vault-pass
ansible-playbook -i hosts.ini site.yml --ask-vault-pass
```

The last command runs the playbook a second time so you can check for
unexpected changes. After deployment, check that NGINX, MariaDB, and PHP-FPM
are running and that the WordPress site loads.

