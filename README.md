# Ansible Role: Drupal

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-drupal.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-drupal)

Builds and installs [Drupal](https://drupal.org/), an open source content management platform.

## Requirements

Drupal is a PHP-based application that is meant to run behind a typical LAMP/LEMP/LEPP/etc. stack, so you'll need at least the following:

  - Apache or Nginx (Recommended: `geerlingguy.apache` or `geerlingguy.nginx`)
  - MySQL or similar Database server (Recommended: `geerlingguy.mysql` or `geerlingguy.postgresql`)
  - PHP (Recommended: `geerlingguy.php` along with other PHP-related roles like `php-mysql`).

Drush is not an absolute requirement, but it's handy to have, and also required if you use this role to Install a Drupal site (`drupal_install_site: true`). You can use `geerlingguy.drush` to install Drush.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    TODO.

## Dependencies

N/A

## Example Playbook

See the example playbook used for Travis CI tests (in `tests/test.yml`) for a simple example. See also: [Drupal VM](https://www.drupalvm.com), which uses this role to set up Drupal.

Currently, this role assumes you've either already cloned an existing Drupal codebase into the `drupal_core_path`, you have a Drush make file or `composer.json` already configured to build your site, or you are building a brand new Drupal site (this is the default) using the [Composer template for Drupal projects](https://github.com/drupal-composer/drupal-project).

    - hosts: webserver
      vars_files:
        - vars/main.yml
      roles:
        - geerlingguy.apache
        - geerlingguy.mysql
        - geerlingguy.php
        - geerlingguy.php-mysql
        - geerlingguy.composer
        - geerlingguy.drush
        - geerlingguy.drupal

*Inside `vars/main.yml`*:

    TODO.

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
