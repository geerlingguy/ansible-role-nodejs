# Ansible Role: Node.js

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-nodejs.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-nodejs)

Installs Node.js on RHEL/CentOS or Debian/Ubuntu.

## Requirements

Requires the EPEL repository on RedHat/CentOS (you can install it by simply adding the `geerlingguy.repo-epel` role to your playbook).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    nodejs_version: "0.10"

The Node.js version to install. "0.10" is the default and works on all supported OSes. Other versions such as "0.12", "4.x", and "5.x" should work on the latest versions of Debian/Ubuntu and RHEL/CentOS, but may be less stable on older operating systems (like CentOS 6).

    nodejs_forever: true

Whether to install Forever, a simple process manager for Node.js. With forever installed, you can start a Node.js app with the command `forever start /path/to/app.js`, and manage the app via `forever` much the same as you would manage other services on your server with `service`.

    nodejs_npm_global_packages: []

Add a list of npm packages with a `name` and (optional) `version` to be installed globally. For example:

    nodejs_npm_global_packages:
      # Install a specific version of a package.
      - name: jslint
        version: 0.9.3
      # Install the latest stable release of a package.
      - name: node-sass

## Dependencies

None.

## Example Playbook

    - hosts: utility
      vars_files:
        - vars/main.yml
      roles:
        - geerlingguy.nodejs

*Inside `vars/main.yml`*:

    nodejs_forever: true
    nodejs_npm_global_packages:
      - name: jslint
      - name: node-sass

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/).
