# stack_install

Installs the packages listed in `defaults/main.yml` using Ansible's `dnf`
module. The package list includes NGINX, MariaDB, PHP-FPM, the PyMySQL driver,
and supporting utilities.

## Requirements and variables

- The target must be a compatible RPM-family Linux distribution with `dnf`.
- Package names in `defaults/main.yml` must exist in the target's enabled
  repositories.
- `system_packages`, `extra_packages`, and `stack_packages` can be overridden
  to adjust package selection.

This role does not configure or start the services; that is handled by
`stack_config`.


