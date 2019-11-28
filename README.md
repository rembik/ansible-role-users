Ansible Role: Users
===================

[![Build Status](https://img.shields.io/travis/rembik/ansible-role-users/master.svg?logo=travis-ci&logoColor=EEE)][travis_ci]
[![GitHub release](https://img.shields.io/github/release/rembik/ansible-role-users.svg?&colorB=56b4b6&logo=github&logoColor=EEE)](https://github.com/rembik/ansible-role-users/releases)
[![Ansible Role](https://img.shields.io/ansible/role/36409.svg?colorB=56b4b6&logo=ansible&logoColor=EEE)][ansible_galaxy]
[![Ansible Role downloads](https://img.shields.io/ansible/role/d/36409.svg?label=downloads&logo=ansible&logoColor=EEE)][ansible_galaxy]

This role manages users and their groups on your system.

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent Ansible version (tested last 3 major versions).

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- rembik.bootstrap

```

Role Variables
--------------

These defaults are set in `defaults/main.yml`:
```yaml
---
# defaults file for users

# The default value, whether to create a group for every user
# and make that their primary group
users_group_per_user: yes
# If no group per user is created, then this is the default primary
# group all users belong to
users_group: users
# The default value, whether to create home directory for the user
# when the account is created or if the home directory does not exist
users_create_home: yes
# The default sudo options for the user when sudo is set to yes,
# but none are specified
users_sudo_options: "ALL=(ALL) NOPASSWD: ALL"
# The default shell for the user when none is specified
users_shell: /bin/bash
# The local directory to find/store generated ssh keys
users_ssh_key_dir: ssh_keys

# Lists of users to create, remove or modify
users: []

# List of user groups to create or delete
users_groups: []

```
A good place to put replacements for these variables is in `group_vars/all` or `group_vars/group_name`,
if you only want defined users and groups to be on certain machines.

The `users` variable containing the list of users to create, remove or modify.
Each user in this list is defined as an dictionary.
The following parameters are available for each user dictionary:

| User Parameter | Choices / **Defaults** | Comments |
|---|---|---|
| `name` *required* || Name of the user to create, remove or modify. |
| `state` | Choices:<ul><li>**present**</li><li>absent</li></ul> | Whether the account should exist or not, taking action if the state is different from what is stated. |
| `comment` || Optionally sets the description (aka GECOS) of user account. |
| `uid` || Optionally sets the UID of the user. |
| `group` | Default: **`user.name`** | Optionally overrides the user's primary group taken from `users_group_per_user=yes` or `users_group` (takes a group name). |
| `gid` || This only affects `users_group_per_user=yes`. Optionally sets different GID of user's primary group. Otherwise the UID will be used. |
| `groups` || List of groups user will be added to. When set to an empty string the user is removed from all groups except the primary group. |
| `append` | Choices:<ul><li>**no**</li><li>yes</li></ul> | If *yes*, add the user to the groups specified in `groups`. If *no*, user will only be added to the groups specified in `groups`, removing them from all other groups. |
| `password` | Default: **!**| Optionally set the user's password to this crypted value. Otherwise the user account will be locked. |
| `update_password` | Choices:<ul><li>**always**</li><li>on_create</li></ul> | *always* will update passwords if they differ. *on_create* will only set the password for newly created users. |
| `create_home` | Choices:<ul><li>**yes**</li><li>no</li></ul> | Optionally overrides this value taken from `users_create_home`. Unless set to *no*, a home directory will be made for the user when the account is created or if the home directory does not exist. |
| `home` | Default: **/home/`user.name`** | Optionally set the user's home directory. |
| `shell` | Default: **/bin/bash** | Optionally overrides the user's shell taken from `users_shell`. |
| `profile` || Optionally sets custom block into user's profile. *Requires `user.create_home=yes`!* |
| `cron` | Choices:<ul><li>**no**</li><li>yes</li></ul> | If *yes*, allow the user to create, edit, display, or remove crontab files. Otherwise, disallow to modify crontab files. |
| `sudo` | Choices:<ul><li>**no**</li><li>yes</li></ul> | If *yes*, set the user's sudo options taken from `user.sudo_options`. Otherwise, remove the user's sudo options. |
| `sudo_options` | Default: **ALL=(ALL) NOPASSWD: ALL**| Optionally overrides the user's sudo options taken from `users_sudo_options`. |
| `ssh_key` || List of the users's authorized SSH keys (takes public SSH keys; included directly and without newlines). When set to an empty list or string all the users's authorized SSH keys are removed. *Requires `user.create_home=yes`!* |
| `generate_ssh_key` | Choices:<ul><li>**no**</li><li>yes</li></ul> | Unless set to *no*, generate the user's SSH key pair, if the SSH key does not exists in the local directory `users_ssh_key_dir`. After that, add it to the users's authorized SSH keys and deploy the SSH key pair to the user. *Requires `user.create_home=yes`!* |
| `remove` | Choices:<ul><li>**no**</li><li>yes</li></ul> | This only affects `user.state=absent`, it attempts to remove directories associated with the user. The behavior is the same as *userdel --remove*, check the man page for details and support. |
|`force` | Choices:<ul><li>**no**</li><li>yes</li></ul> | This only affects `user.state=absent`, it forces removal of the user and associated directories on supported platforms. The behavior is the same as *userdel --force*, check the man page for details and support. |

The `users_groups` variable containing the list of user groups to create or delete. Each group in this list is defined as an dictionary.
The following parameters are available for each group dictionary:

| Group Parameter | Choices / **Defaults** | Comments |
|---|---|---|
| `name` *required* || Name of the group to manage. |
| `state` | Choices:<ul><li>**present**</li><li>absent</li></ul> | Whether the group should be present or not on the remote host. |
| `gid` || Optional GID to set for the group. |

Dependencies
------------

In general this role has no dependencies. In combination with the recommended role [`rembik.bootstrap`](https://github.com/rembik/ansible-role-bootstrap), this role uses the defined `bootstrap_user` (if necessary) to connect to the remote host and executing this role tasks.

Example Playbook
----------------

This example is taken from `molecule/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: rembik.bootstrap
    - role: rembik.users
      vars:
        users_ssh_key_dir: "{{ lookup('env', 'MOLECULE_EPHEMERAL_DIRECTORY') }}/ssh_key"
        users_groups:
          - name: users
          - name: bin
        users:
          - name: nouser
            comment: No User
            create_home: no
          - name: molecule
            comment: Ansible Test User
            uid: 2001
            cron: yes
            sudo: yes
            generate_ssh_key: yes
          - name: admin
            comment: Administrator
            uid: 2002
            groups: [users]
            cron: yes
            sudo: yes
            profile: |
              alias ll='ls -lah'
              alias cp='cp -iv'
            ssh_key:
              - "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABWBILQeRSYYmGea/WIf6kd... admin@example.com"
          - name: user
            comment: User
            uid: 2003
            groups: [users]
            home: /custom/user
            shell: /bin/sh
            generate_ssh_key: yes
```

Role Tests
-----

[![Python](https://img.shields.io/badge/python-3.7-1488C6.svg)](https://www.python.org/)
[![Ansible](https://img.shields.io/badge/Ansible-2.7%20%7C%202.8%20%7C%202.9%20%7C%20devel%2A-56b4b6.svg)](https://ansible.com/)

This role is tested periodically against the following Linux distributions:

|| [![Ansible](https://img.shields.io/badge/2.7-56b4b6.svg)](https://docs.ansible.com/ansible/2.7/) | [![Ansible](https://img.shields.io/badge/2.8-56b4b6.svg)](https://docs.ansible.com/ansible/2.8/) | [![Ansible](https://img.shields.io/badge/2.9-56b4b6.svg)](https://docs.ansible.com/ansible/2.9/)| [![Ansible](https://img.shields.io/badge/devel%2A-56b4b6.svg)](https://docs.ansible.com/ansible/devel/) |
|---|---|---|---|---|
| [![DockerDistro](https://img.shields.io/badge/Alpine-latest%20%7C%20edge%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/alpine) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/AmazonLinux-latest-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/amazonlinux) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/ArchLinux-latest-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/r/archlinux/base) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/CentOS-latest-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/centos) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![EC2Distro](https://img.shields.io/badge/CentOS-7-232F3E.svg?logo=amazon-aws&logoColor=EEE)](https://aws.amazon.com/marketplace/seller-profile?id=16cb8b03-256e-4dde-8f34-1b0f377efe89) ||| [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] ||
| [![DockerDistro](https://img.shields.io/badge/Debian-latest%20%7C%20unstable%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/debian) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![EC2Distro](https://img.shields.io/badge/Debian-9-232F3E.svg?logo=amazon-aws&logoColor=EEE)](https://aws.amazon.com/marketplace/seller-profile?id=890be55d-32d8-4bc8-9042-2b4fd83064d5) ||| [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] ||
| [![DockerDistro](https://img.shields.io/badge/Fedora-latest%20%7C%20rawhide%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/fedora) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![EC2Distro](https://img.shields.io/badge/Fedora-31-232F3E.svg?logo=amazon-aws&logoColor=EEE)](https://alt.fedoraproject.org/cloud/) ||| [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] ||
| [![DockerDistro](https://img.shields.io/badge/openSUSE-Leap%20%7C%20Tumbleweed-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/opensuse) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/RedHat-latest-1488C6.svg?logo=docker&logoColor=EEE)](https://access.redhat.com/containers/#/registry.access.redhat.com/ubi8/ubi) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![DockerDistro](https://img.shields.io/badge/Ubuntu-latest%20%7C%20devel%2A-1488C6.svg?logo=docker&logoColor=EEE)](https://hub.docker.com/_/ubuntu) | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] | [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] |
| [![EC2Distro](https://img.shields.io/badge/Ubuntu-18.04-232F3E.svg?logo=amazon-aws&logoColor=EEE)](https://aws.amazon.com/marketplace/seller-profile?id=565feec9-3d43-413e-9760-c651546613f2) ||| [![Check](https://img.shields.io/badge/X-grey.svg)][travis_ci] ||

> Asteriks means the build is allowed to fail, it's marked as an experimental build.

Contributing
------------

If you find issues, please register them at this [GitHub project issue page](https://github.com/rembik/ansible-role-users/issues/new/choose) or consider contributing code by following this [guideline](http://github.com/rembik/ansible-role-users/tree/master/.github/CONTRIBUTING.md).

License
-------

Apache-2.0

Author Information
------------------

- [Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
- [Brian Rimek](https://github.com/rembik)

[travis_ci]: https://travis-ci.org/rembik/ansible-role-users
[ansible_galaxy]: https://galaxy.ansible.com/rembik/users
