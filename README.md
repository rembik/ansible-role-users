Ansible Role: Users
===================

[![Build Status](https://img.shields.io/travis/rembik/ansible-role-users/master.svg?logo=travis&logoColor=EEE)](https://travis-ci.org/rembik/ansible-role-users)
[![GitHub release](https://img.shields.io/github/release/rembik/ansible-role-users.svg?&colorB=56b4b6&logo=github&logoColor=EEE)](https://github.com/rembik/ansible-role-users/releases)
[![Ansible Role](https://img.shields.io/ansible/role/36409.svg?colorB=56b4b6&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAEdUlEQVRYR61Xa4iUVRh+n8PMCjXOzHlPmZUlZlgpoVBBUdBlUyExTRJsyUrqdxcw6EKhBEUX6fKvG5l0IUvZUKSr1I8uZpCUCVLE0lZo6znn29mVcpv53jjTzDLOzux3Vvv+fs/znOf7zvO+7zmgE3hE5NQkSU4HcBoAJSJHSqXSEICRqcohllCpVObVarVb0jTtAzCvE09EDgPYLSKfAniPmYez9DMNeO+vTdP0QQCLs8Ta3h8hoke01i8BSLtxuxpwzpVEZDuA66a4cDv8u56enhsKhcKhTjodDXjvZ6dp+iGAC05y8TpdRH4noqXGmB/b9SYYsNbOIqJvAZzxfyze1BCRChFdYYw50Kp7nIGQbufcXgAXRS5eI6JfiWhOJH4wn89fMn369KEm/jgD1tqtAFZHihGAdeVyeYtz7msAl0XyvmDmqyYYSJLk0jRN90aKhH09xMxnh4Rba1cD2BrLJaJbmfnNgB//A9bajwFcHysC4FGt9WONkOWcc4MAZsbwReQPZj4PwLG6Ae/9QhHZF0NuYKq5XG5msVi03vs7tNabrbUbg6kpaNT/Qt2Ac+4JInpgCuS3mbnPe3+NiLzGzHNGR0dnjo2NhXJTkTrvMPOapoGQ5HMiiWH/rzTGfGmt3QzgdgA3aa37rbXbAKyK1BnWWht478si4iNJYfEDxpgFbbz3mXllkiS9aZp+EquVy+UuhLV2AYD9sSQRucsY86r3/l4ReXa8nIA5WusB59xPRHR+jJ5SqhdJkixO0/SjGELoZsw8I6TXe79SRDYTUalRCRuNMRu89/eIyHMxekS0NhhYEvp+DAHAJq31+ibWe7+oYWIhEQ2EMFpriwD+JKJpWZr1/DjnLiai77PA/80UmW2MGXTOvaCU6i+Xy7sbWQh/YkUzjN77l8NWZWkqpZaiUqmYarUaZnfWs4uZlzXwodzyYd4z8+OBaK3dAGBRCGNsrgK+WYa/RAyUZcy8yzl3PxE91eJ2p9Z6DYCjoS8Q0T6tdWKt/QrA5ZN81ZjWmusGrLXPA7h7EvCg1np2o2sOENG5rVgROZjP51cUi8WDLflYKyJbJtHcwcw31g1kVYKIrDfGbLLWLgXwQSdRETmqlLpNa729URXTvPdhq0wnPIDQwl+vGxCREMb9AOZ3AB8TkRnGmIpzrj+ELSMsT2qtH2pMyVcA3NkBb7XWswD8PT4NvfdXi8hnHcA/i0gYnQrAw5G9fgeA7SKyiYi4XRPAfVrreq9oP5C8C+DmrHI4mfci8hszzwUwNsGAiBScc3u6bMXJrFvnishfoTKYebzvdDqUhqn4TezhYoquljPzzlZO12N5uN0Q0dwpLtAN/g8RrWsewzINBMDw8DDXarVtRBSaywk/IjKilFqutf68YzlmKTvn+kTkGQBnZmFb34vIqFLqxXw+/3ShUDjcjZt5N2yE5xTv/SoR6SWiJQDO6iYoInuUUm8ppd4olUouy3SUgXaRkZGRGdVqdb6IhAtMGL9DIhKu5z+EQ0nWoq3v/wWf4hm52dSUyAAAAABJRU5ErkJggg==)](https://galaxy.ansible.com/rembik/users)
[![Ansible Role downloads](https://img.shields.io/ansible/role/d/36409.svg?label=downloads&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAEdUlEQVRYR61Xa4iUVRh+n8PMCjXOzHlPmZUlZlgpoVBBUdBlUyExTRJsyUrqdxcw6EKhBEUX6fKvG5l0IUvZUKSr1I8uZpCUCVLE0lZo6znn29mVcpv53jjTzDLOzux3Vvv+fs/znOf7zvO+7zmgE3hE5NQkSU4HcBoAJSJHSqXSEICRqcohllCpVObVarVb0jTtAzCvE09EDgPYLSKfAniPmYez9DMNeO+vTdP0QQCLs8Ta3h8hoke01i8BSLtxuxpwzpVEZDuA66a4cDv8u56enhsKhcKhTjodDXjvZ6dp+iGAC05y8TpdRH4noqXGmB/b9SYYsNbOIqJvAZzxfyze1BCRChFdYYw50Kp7nIGQbufcXgAXRS5eI6JfiWhOJH4wn89fMn369KEm/jgD1tqtAFZHihGAdeVyeYtz7msAl0XyvmDmqyYYSJLk0jRN90aKhH09xMxnh4Rba1cD2BrLJaJbmfnNgB//A9bajwFcHysC4FGt9WONkOWcc4MAZsbwReQPZj4PwLG6Ae/9QhHZF0NuYKq5XG5msVi03vs7tNabrbUbg6kpaNT/Qt2Ac+4JInpgCuS3mbnPe3+NiLzGzHNGR0dnjo2NhXJTkTrvMPOapoGQ5HMiiWH/rzTGfGmt3QzgdgA3aa37rbXbAKyK1BnWWht478si4iNJYfEDxpgFbbz3mXllkiS9aZp+EquVy+UuhLV2AYD9sSQRucsY86r3/l4ReXa8nIA5WusB59xPRHR+jJ5SqhdJkixO0/SjGELoZsw8I6TXe79SRDYTUalRCRuNMRu89/eIyHMxekS0NhhYEvp+DAHAJq31+ibWe7+oYWIhEQ2EMFpriwD+JKJpWZr1/DjnLiai77PA/80UmW2MGXTOvaCU6i+Xy7sbWQh/YkUzjN77l8NWZWkqpZaiUqmYarUaZnfWs4uZlzXwodzyYd4z8+OBaK3dAGBRCGNsrgK+WYa/RAyUZcy8yzl3PxE91eJ2p9Z6DYCjoS8Q0T6tdWKt/QrA5ZN81ZjWmusGrLXPA7h7EvCg1np2o2sOENG5rVgROZjP51cUi8WDLflYKyJbJtHcwcw31g1kVYKIrDfGbLLWLgXwQSdRETmqlLpNa729URXTvPdhq0wnPIDQwl+vGxCREMb9AOZ3AB8TkRnGmIpzrj+ELSMsT2qtH2pMyVcA3NkBb7XWswD8PT4NvfdXi8hnHcA/i0gYnQrAw5G9fgeA7SKyiYi4XRPAfVrreq9oP5C8C+DmrHI4mfci8hszzwUwNsGAiBScc3u6bMXJrFvnishfoTKYebzvdDqUhqn4TezhYoquljPzzlZO12N5uN0Q0dwpLtAN/g8RrWsewzINBMDw8DDXarVtRBSaywk/IjKilFqutf68YzlmKTvn+kTkGQBnZmFb34vIqFLqxXw+/3ShUDjcjZt5N2yE5xTv/SoR6SWiJQDO6iYoInuUUm8ppd4olUouy3SUgXaRkZGRGdVqdb6IhAtMGL9DIhKu5z+EQ0nWoq3v/wWf4hm52dSUyAAAAABJRU5ErkJggg==)](https://galaxy.ansible.com/rembik/users)

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

In general this role has no dependencies. In combination with the recommended role [`rembik.bootstrap`](https://github.com/rembik/ansible-role-bootstrap), this role uses the temporary registered `bootstrap_remote_user` to connect to the remote host and executing this role tasks.

Example Playbook
----------------

This example is taken from `molecule/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  gather_facts: false
  become: true

  roles:
    - role: rembik.bootstrap
    - role: rembik.users
      vars:
        users_groups:
          - name: users
          - name: bin
        users:
          - name: nouser
            comment: No User
            create_home: no
          - name: admin
            comment: Ansible Management User
            uid: 2001
            groups: [users, bin]
            cron: yes
            sudo: yes
            shell: /bin/sh
            profile: |
              alias ll='ls -lah'
              alias cp='cp -iv'
            ssh_key:
              - "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDVpUJQCOaPg3p5xro9e+1fkGRWNOGrrExiKMqTE91Fwu349bxfMnMzRS0PAERouR9EEL+Ee4Yzhav/uNc35eCtXzACtluXnAncMrQj6pM3IqASynhvXTygHljmcMbBSDQtLrTZeW+YzIcOgk5UM1yBi26WoUYva2aCr9IRvKdYreAK08OiMdZedpOye0ZdvIYJGcyITwc6YMmrAhP7jZlrk/mDEkf2a4eBp+475o7MJtaC9npqYkToM8vqvx5AGEKqXt7/f1/paOY7KsR+VGPQy6k2RkXjWBsXPesZ3d3XLZHE60wAk0EsuJO8A25+uWSB6ILQeRSYYmGea/WIf6kd noone@throwaway.example.com"
            generate_ssh_key: yes
          - name: test
            comment: Ansible Test User
            uid: 2002
            groups: [users]
            home: /test
            cron: yes
            generate_ssh_key: yes
          - name: user
            comment: User
            uid: 2003
            groups: [users]

```

Role Tests
-----

This role has been tested against the following Linux distributions and Ansible versions:

| Distribution ||
|---|---|
| [![Distro](https://img.shields.io/badge/Alpine-latest%20%7C%20edge%2A-brightgreen.svg)](https://travis-ci.org/rembik/ansible-role-users) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)]() |
| [![Distro](https://img.shields.io/badge/ArchLinux-latest-brightgreen.svg)](https://travis-ci.org/rembik/ansible-role-users) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)]() |
| [![Distro](https://img.shields.io/badge/CentOS-latest-brightgreen.svg)](https://travis-ci.org/rembik/ansible-role-users) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)]() |
| [![Distro](https://img.shields.io/badge/Debian-latest%20%7C%20unstable%2A-brightgreen.svg)](https://travis-ci.org/rembik/ansible-role-users) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)]() |
| [![Distro](https://img.shields.io/badge/Fedora-latest%20%7C%20rawhide%2A-brightgreen.svg)](https://travis-ci.org/rembik/ansible-role-users) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)]() |
| [![Distro](https://img.shields.io/badge/openSUSE-Leap%20%7C%20Tumbleweed-brightgreen.svg)](https://travis-ci.org/rembik/ansible-role-users) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)]() |
| [![Distro](https://img.shields.io/badge/Ubuntu-latest%20%7C%20devel%2A-brightgreen.svg)](https://travis-ci.org/rembik/ansible-role-users) | [![Ansible](https://img.shields.io/badge/Ansible-2.5%20%7C%202.6%20%7C%202.7%20%7C%20devel%2A-56b4b6.svg)]() |

> Asteriks means the build is allowed to fail, it's marked as an experimental build.

Contributing
------------

If you find issues, please register them in [GitHub](https://github.com/rembik/ansible-role-users/issues) or consider contributing by opening a pull request and following the [contributing](CONTRIBUTING.md) guideline.

License
-------

Apache-2.0

Author Information
------------------

- [Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
- [Brian Rimek](https://github.com/rembik)
