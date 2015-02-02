# Ansible Role: Node.js

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-nodejs.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-nodejs)

Installs Node.js on RHEL/CentOS or Debian/Ubuntu.

## Requirements

Requires the EPEL repository on RedHat/CentOS (you can install it by simply adding the `geerlingguy.repo-epel` role to your playbook).

## Role Variables

Available variables are listed below, along with default values (see `vars/main.yml`):

    nodejs_forever: true

Whether to install Forever, a simple process manager for Node.js. With forever installed, you can start a Node.js app with the command `forever start /path/to/app.js`, and manage the app via `forever` much the same as you would manage other services on your server with `service`.

## Dependencies

None.

## Example Playbook

    - hosts: utility
      vars_files:
        - vars/main.yml
      roles:
        - { role: geerlingguy.nodejs }

*Inside `vars/main.yml`*:

    nodejs_forever: true

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/).
