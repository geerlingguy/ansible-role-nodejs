# Ansible Role: Node.js

Installs Node.js on RHEL/CentOS.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `vars/main.yml`):

    nodejs_forever: true

Whether to install Forever, a simple process manager for Node.js. With forever installed, you can start a Node.js app with the command `forever start /path/to/app.js`, and manage the app via `forever` much the same as you would manage other services on your server with `service`.

## Dependencies

  - geerlingguy.repo-epel

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
