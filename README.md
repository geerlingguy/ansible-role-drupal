# Ansible Role: Drupal

Installs [Drupal](https://drupal.org/), an open source content management platform, on Linux hosts running the generic LAMP stack.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    # The core version you want to use (e.g. 6.x, 7.x, 8.x).
    drupal_core_version: "8.x"

The version of Drupal you would like to use (can be any git branch, tag, or commit ref). Examples: "6.x", "7.x", "8.x", "5a3ef30".

    drupal_core_path: "/var/www/drupal-{{ drupal_core_version }}-dev"

The path where Drupal will be downloaded and installed (needs to be readable by the webserver).

    drupal_domain: "drupaltest.dev"

The domain/DNS name of the drupal site. If using for local testing/development, you can use whatever you want (or keep the default), and add an entry to your `/etc/hosts` file like `127.0.0.1 mytestdrupalsite.com`.

    drupal_site_name: "Drupal Example"

The site name (will be used as the home page title and anywhere else the site name is displayed).

    drupal_webserver_daemon: apache2

The daemon name for the webserver you're running (could be `apache2`, `httpd`, `nginx`, etc.). Used to restart the appropriate service after Drupal is configured and installed.

    drupal_mysql_user: drupal
    drupal_mysql_password: password
    drupal_mysql_database: drupal

MySQL database username, password, and database name for Drupal to use.

## Dependencies

  - geerlingguy.apache
  - geerlingguy.mysql
  - geerlingguy.php
  - geerlingguy.drush

## Example Playbook

    - hosts: servers
      vars_files:
        - vars/main.yml
      roles:
        - { role: geerlingguy.drupal }

*Inside `vars/main.yml`*:

    drupal_core_version: "7.x"
    drupal_domain: "drupaltest.dev"
    ... etc ...

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/).
