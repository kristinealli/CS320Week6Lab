# wordpress

Creates the WordPress database and database user, downloads WP-CLI and
WordPress core, writes `wp-config.php`, installs WordPress, and installs and
activates configured plugins.

## Requirements and variables

- Install the `community.mysql` collection from the project's
  `requirements.yml` on the Ansible control node.
- The target needs WP-CLI prerequisites and a running local MariaDB server.
- `group_vars/common.yml` supplies `wordpress`, `wp_database`, `wp_cli`, and
  `wordpress_plugins` settings.
- The encrypted, local-only `group_vars/vault.yml` supplies `vault_email`,
  `vault_wp_admin_password`, and `vault_wp_db_password`.
- `wordpress_system.user`, `.group`, and `.home` come from
  `stack_config/defaults/main.yml`.

