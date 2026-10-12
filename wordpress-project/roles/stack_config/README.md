# stack_config

Creates the WordPress system group, user, and document root; deploys the
NGINX site and PHP-FPM pool templates; adjusts PHP settings; and enables and
starts NGINX, MariaDB, and PHP-FPM. It also runs `nginx -t` to validate the
NGINX configuration.

## Requirements and variables

This role expects the packages to have been installed by `stack_install`.
Its defaults in `defaults/main.yml` define `wordpress_system` (user, group,
home directory, comment, and state). Shared settings are loaded from
`group_vars/common.yml` by the main playbook:

- `php_fpm_service`, `php_fpm_pool_path`, and `php_fpm_socket`
- `php_ini_path`
- `nginx_user` and `nginx_service`
- `wordpress.domain`


