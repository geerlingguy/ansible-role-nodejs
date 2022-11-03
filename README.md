# Ansible Role: Node.js

[![CI](https://github.com/geerlingguy/ansible-role-nodejs/workflows/CI/badge.svg?event=push)](https://github.com/geerlingguy/ansible-role-nodejs/actions?query=workflow%3ACI)

Installs Node.js on RHEL/CentOS or Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
nodejs_version: "16.x"
```

The Node.js version to install. "14.x" is the default and works on most supported OSes. Other versions such as "10.x", "14.x", "18.x", etc. should work on the latest versions of Debian/Ubuntu and RHEL/CentOS.

```yaml
nodejs_repourl: "https://deb.nodesource.com"
```

The Node.js repository to use for installation.

```yaml
nodejs_install_npm_user: "{{ ansible_ssh_user }}"
```

The user for whom the npm packages will be installed can be set here, this defaults to `ansible_user`.

```yaml
npm_config_prefix: "/usr/local/lib/npm"
```

The global installation directory. This should be writeable by the `nodejs_install_npm_user`.

```yaml
npm_config_unsafe_perm: "false"
```

Set to true to suppress the UID/GID switching when running package scripts. If set explicitly to false, then installing as a non-root user will fail.

```yaml
nodejs_npm_global_packages: []
```

A list of npm packages with a `name` and (optional) `version` to be installed globally. For example:

```yaml
nodejs_npm_global_packages:
  # Install a specific version of a package.
  - name: jslint
    version: 0.9.3
  # Install the latest stable release of a package.
  - name: node-sass
  # This shorthand syntax also works (same as previous example).
  - node-sass
  # Remove a package by setting state to 'absent'.
  - name: node-sass
    state: absent
```

```yaml
nodejs_package_json_path: ""
```

Set a path pointing to a particular `package.json` (e.g. `"/var/www/app/package.json"`). This will install all of the defined packages globally using Ansible's `npm` module.

```yaml
nodejs_generate_etc_profile: "true"
```
    
By default the role will create `/etc/profile.d/npm.sh` with exported variables (`PATH`, `NPM_CONFIG_PREFIX`, `NODE_PATH`). If you prefer to avoid generating that file (e.g. you want to set the variables yourself for a non-global install), set it to "false".

## Dependencies

None.

## Example Playbook

```yaml
- hosts: utility
  vars_files:
    - vars/main.yml
  roles:
    - geerlingguy.nodejs
```

*Inside `vars/main.yml`*:

```yaml
nodejs_npm_global_packages:
  - name: jslint
  - name: node-sass
```

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
