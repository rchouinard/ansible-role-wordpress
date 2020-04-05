# WordPress Ansible Role

This role manages the WordPress platform and WP-CLI tool.

The installation of a webserver and PHP runtime are expected to be otherwise managed.

## Requirements

* Ansible 2.6+

## Role Variables

``` yaml
# Filesystem config
wp_path: /var/www/html
wp_owner: wordpress
wp_group: "{{ wp_owner }}"

# WordPress download configuration
wp_version: latest
wp_skip_content: false  # set true to skip default plugins and themes

# WordPress configuration
wp_skip_config: false   # set true to skip config creation
wp_db_name: wordpress
wp_db_user: wordpress
wp_db_pass: ~
wp_db_host: localhost:3306
wp_db_prefix: wp_
wp_db_charset: utf8
wp_db_skip_check: false

# WordPress installation
wp_skip_install: false  # set true to skip installation
wp_url: ~               # required for installation
wp_title: My Blog!
wp_admin_user: admin
wp_admin_password: ~    # defaults to random string
wp_admin_email: ~       # required for installation
wp_skip_email: false

# WP-CLI configuration
wp_cli_path: /usr/local/bin/wp
```

## Dependencies

None.

## Example Playbook

``` yaml
- hosts: localhost
  tasks:
  - import_role:
      name: rchouinard.wordpress
    vars:
      wp_url: https://www.mycompany.com
      wp_admin_email: wpadmin@mycompany.com
      wp_db_host: my-db-host
      wp_db_pass: my-db-password
```

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
