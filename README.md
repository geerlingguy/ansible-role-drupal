# Ansible Role: Drupal

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-drupal.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-drupal)

Installs [Drupal](https://drupal.org/), an open source content management platform, on Linux hosts running the generic LAMP stack.

Currently the role is only guaranteed to work on a LAMP stack on Debian/Ubuntu, though only minimal changes will need to be made to make the role with other platforms (notably RedHat/CentOS), and with other webservers besides Apache (thus enabling Drupal on a LEMP stack fairly easily).

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    # The core version you want to use (e.g. 6.x, 7.x, 8.0.x).
    drupal_core_version: "8.0.x"

The version of Drupal you would like to use (can be any git branch, tag, or commit ref). Examples: "6.x", "7.x", "8.0.x", "5a3ef30".

    drupal_core_path: "/var/www/drupal-{{ drupal_core_version }}-dev"

The path where Drupal will be downloaded and installed (needs to be readable by the webserver).

    drupal_domain: "drupaltest.dev"

The domain/DNS name of the drupal site. If using for local testing/development, you can use whatever you want (or keep the default), and add an entry to your `/etc/hosts` file like `127.0.0.1 mytestdrupalsite.com`.

    drupal_site_name: "Drupal Example"

The site name (will be used as the home page title and anywhere else the site name is displayed).

    drupal_admin_name: admin
    drupal_admin_password: admin

The username and password for the admin account (user 1).

    drupal_webserver_daemon: apache2

The daemon name for the webserver you're running (could be `apache2`, `httpd`, `nginx`, etc.). Used to restart the appropriate service after Drupal is configured and installed.

    drupal_mysql_user: drupal
    drupal_mysql_password: password
    drupal_mysql_database: drupal

MySQL database username, password, and database name for Drupal to use.

    drupal_repo_url: "http://git.drupal.org/project/drupal.git"

The public url of the git repository you want to clone. Use `drupal_core_version` to clone a particular branch. (*Note: Usually you shouldn't change this from the default, unless you need to use a private fork of Drupal.*).

    drupal_keep_updated: no

Whether to update the repo above to the latest commit in the branch identified by `drupal_core_version` (the git tag or branch) whenever this playbook runs. (*Warning: Setting this to `yes` can cause your Drupal codebase to change over time, requiring other deployment steps and update scripts to be run. Use with caution!).

    drupal_install_profile: standard

The install profile to use. If you're installing Drupal 6.x, you should update this from 'standard' to 'default'.

## Dependencies

  - geerlingguy.git
  - geerlingguy.apache
  - geerlingguy.mysql
  - geerlingguy.php
  - geerlingguy.php-mysql
  - geerlingguy.composer
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
