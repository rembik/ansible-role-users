Ansible Role: Users
===================

[![Build Status](https://img.shields.io/travis/rembik/ansible-role-users/master.svg?logo=travis&logoColor=EEE)](https://travis-ci.org/rembik/ansible-role-users)
[![GitHub release](https://img.shields.io/github/release/rembik/ansible-role-users.svg?&logo=github&logoColor=EEE)](https://github.com/rembik/ansible-role-users/releases)
[![Ansible Role](https://img.shields.io/ansible/role/36409.svg?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAEdUlEQVRYR61Xa4iUVRh+n8PMCjXOzHlPmZUlZlgpoVBBUdBlUyExTRJsyUrqdxcw6EKhBEUX6fKvG5l0IUvZUKSr1I8uZpCUCVLE0lZo6znn29mVcpv53jjTzDLOzux3Vvv+fs/znOf7zvO+7zmgE3hE5NQkSU4HcBoAJSJHSqXSEICRqcohllCpVObVarVb0jTtAzCvE09EDgPYLSKfAniPmYez9DMNeO+vTdP0QQCLs8Ta3h8hoke01i8BSLtxuxpwzpVEZDuA66a4cDv8u56enhsKhcKhTjodDXjvZ6dp+iGAC05y8TpdRH4noqXGmB/b9SYYsNbOIqJvAZzxfyze1BCRChFdYYw50Kp7nIGQbufcXgAXRS5eI6JfiWhOJH4wn89fMn369KEm/jgD1tqtAFZHihGAdeVyeYtz7msAl0XyvmDmqyYYSJLk0jRN90aKhH09xMxnh4Rba1cD2BrLJaJbmfnNgB//A9bajwFcHysC4FGt9WONkOWcc4MAZsbwReQPZj4PwLG6Ae/9QhHZF0NuYKq5XG5msVi03vs7tNabrbUbg6kpaNT/Qt2Ac+4JInpgCuS3mbnPe3+NiLzGzHNGR0dnjo2NhXJTkTrvMPOapoGQ5HMiiWH/rzTGfGmt3QzgdgA3aa37rbXbAKyK1BnWWht478si4iNJYfEDxpgFbbz3mXllkiS9aZp+EquVy+UuhLV2AYD9sSQRucsY86r3/l4ReXa8nIA5WusB59xPRHR+jJ5SqhdJkixO0/SjGELoZsw8I6TXe79SRDYTUalRCRuNMRu89/eIyHMxekS0NhhYEvp+DAHAJq31+ibWe7+oYWIhEQ2EMFpriwD+JKJpWZr1/DjnLiai77PA/80UmW2MGXTOvaCU6i+Xy7sbWQh/YkUzjN77l8NWZWkqpZaiUqmYarUaZnfWs4uZlzXwodzyYd4z8+OBaK3dAGBRCGNsrgK+WYa/RAyUZcy8yzl3PxE91eJ2p9Z6DYCjoS8Q0T6tdWKt/QrA5ZN81ZjWmusGrLXPA7h7EvCg1np2o2sOENG5rVgROZjP51cUi8WDLflYKyJbJtHcwcw31g1kVYKIrDfGbLLWLgXwQSdRETmqlLpNa729URXTvPdhq0wnPIDQwl+vGxCREMb9AOZ3AB8TkRnGmIpzrj+ELSMsT2qtH2pMyVcA3NkBb7XWswD8PT4NvfdXi8hnHcA/i0gYnQrAw5G9fgeA7SKyiYi4XRPAfVrreq9oP5C8C+DmrHI4mfci8hszzwUwNsGAiBScc3u6bMXJrFvnishfoTKYebzvdDqUhqn4TezhYoquljPzzlZO12N5uN0Q0dwpLtAN/g8RrWsewzINBMDw8DDXarVtRBSaywk/IjKilFqutf68YzlmKTvn+kTkGQBnZmFb34vIqFLqxXw+/3ShUDjcjZt5N2yE5xTv/SoR6SWiJQDO6iYoInuUUm8ppd4olUouy3SUgXaRkZGRGdVqdb6IhAtMGL9DIhKu5z+EQ0nWoq3v/wWf4hm52dSUyAAAAABJRU5ErkJggg==)](https://galaxy.ansible.com/rembik/users)
[![Ansible Role downloads](https://img.shields.io/ansible/role/d/36409.svg?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAEdUlEQVRYR61Xa4iUVRh+n8PMCjXOzHlPmZUlZlgpoVBBUdBlUyExTRJsyUrqdxcw6EKhBEUX6fKvG5l0IUvZUKSr1I8uZpCUCVLE0lZo6znn29mVcpv53jjTzDLOzux3Vvv+fs/znOf7zvO+7zmgE3hE5NQkSU4HcBoAJSJHSqXSEICRqcohllCpVObVarVb0jTtAzCvE09EDgPYLSKfAniPmYez9DMNeO+vTdP0QQCLs8Ta3h8hoke01i8BSLtxuxpwzpVEZDuA66a4cDv8u56enhsKhcKhTjodDXjvZ6dp+iGAC05y8TpdRH4noqXGmB/b9SYYsNbOIqJvAZzxfyze1BCRChFdYYw50Kp7nIGQbufcXgAXRS5eI6JfiWhOJH4wn89fMn369KEm/jgD1tqtAFZHihGAdeVyeYtz7msAl0XyvmDmqyYYSJLk0jRN90aKhH09xMxnh4Rba1cD2BrLJaJbmfnNgB//A9bajwFcHysC4FGt9WONkOWcc4MAZsbwReQPZj4PwLG6Ae/9QhHZF0NuYKq5XG5msVi03vs7tNabrbUbg6kpaNT/Qt2Ac+4JInpgCuS3mbnPe3+NiLzGzHNGR0dnjo2NhXJTkTrvMPOapoGQ5HMiiWH/rzTGfGmt3QzgdgA3aa37rbXbAKyK1BnWWht478si4iNJYfEDxpgFbbz3mXllkiS9aZp+EquVy+UuhLV2AYD9sSQRucsY86r3/l4ReXa8nIA5WusB59xPRHR+jJ5SqhdJkixO0/SjGELoZsw8I6TXe79SRDYTUalRCRuNMRu89/eIyHMxekS0NhhYEvp+DAHAJq31+ibWe7+oYWIhEQ2EMFpriwD+JKJpWZr1/DjnLiai77PA/80UmW2MGXTOvaCU6i+Xy7sbWQh/YkUzjN77l8NWZWkqpZaiUqmYarUaZnfWs4uZlzXwodzyYd4z8+OBaK3dAGBRCGNsrgK+WYa/RAyUZcy8yzl3PxE91eJ2p9Z6DYCjoS8Q0T6tdWKt/QrA5ZN81ZjWmusGrLXPA7h7EvCg1np2o2sOENG5rVgROZjP51cUi8WDLflYKyJbJtHcwcw31g1kVYKIrDfGbLLWLgXwQSdRETmqlLpNa729URXTvPdhq0wnPIDQwl+vGxCREMb9AOZ3AB8TkRnGmIpzrj+ELSMsT2qtH2pMyVcA3NkBb7XWswD8PT4NvfdXi8hnHcA/i0gYnQrAw5G9fgeA7SKyiYi4XRPAfVrreq9oP5C8C+DmrHI4mfci8hszzwUwNsGAiBScc3u6bMXJrFvnishfoTKYebzvdDqUhqn4TezhYoquljPzzlZO12N5uN0Q0dwpLtAN/g8RrWsewzINBMDw8DDXarVtRBSaywk/IjKilFqutf68YzlmKTvn+kTkGQBnZmFb34vIqFLqxXw+/3ShUDjcjZt5N2yE5xTv/SoR6SWiJQDO6iYoInuUUm8ppd4olUouy3SUgXaRkZGRGdVqdb6IhAtMGL9DIhKu5z+EQ0nWoq3v/wWf4hm52dSUyAAAAABJRU5ErkJggg==)](https://galaxy.ansible.com/rembik/users)

This role manages users and their groups on your system.

Example Playbook
----------------

This example is taken from `molecule/default/playbook.yml`:
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

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

Role Variables
--------------

These variables are set in `defaults/main.yml`:
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
# (needed for ssh key setup)
users_create_home: yes
# The default sudo options for the user when sudo is enabled,
# but none are specified
users_sudo_options: "ALL=(ALL) NOPASSWD: ALL"
# The default shell for the user when none is specified
users_shell: /bin/bash
# The local directory to find/store generated ssh keys
users_ssh_key_dir: ssh_keys

# Lists of users to create or delete
users: []

# List of user groups to create or delete
users_groups: []

```

Add `users` variable containing the list of users to create or delete.
A good place to put this is in `group_vars/all` or `group_vars/groupname`,
if you only want the users to be on certain machines.

The following attributes are **required** for each user:

* `name` - The user name.
* `state` - This can be either *present* or *absent*
  - *present* will create the user (default).
  - *absent* will delete the user.

In case, the user should be **created** the following **optional** attributes will take effects:

* `uid` - The numeric user id for the user. This is required for uid consistency
  across systems.
* `gid` - The numeric group id for the group per user. Otherwise, the
  uid will be used.
* `comment` - The full name of the user (gecos field).
* `group` - The overridden primary group for the user (default: *<user.name>*).
* `groups` - The list of supplementary groups for the user.
* `append` - If yes, will only add groups, not set them to just the list in groups.
* `password` - If a hash is provided then that will be used, but otherwise the
  account will be locked.
* `update_password` - This can be either *always* or *on_create*
  - *always* will update passwords if they differ (default).
  - *on_create* will only set the password for newly created users.
* `create_home` - The overridden value, whether to create home directory for the user when the account is created or if the home directory does not exist (default: *yes*).
* `home` - The home directory of the user (default: */home/<user.name>*).
* `shell` - The overridden shell for the user (default: */bin/bash*).
* `profile` - The block to expand settings for the user profile.
* `cron` - If *yes*, set cron permission for the user (default: *no*).
* `sudo` - If *yes*, set sudo options for the user (default: *no*).
* `sudo_options` - The overridden sudo options for the user (default:
  *ALL=(ALL) NOPASSWD: ALL*).
* `ssh_key` - The list of authorized SSH keys for the user. Each public SSH key
  should be included directly and should have no newlines.
* `generate_ssh_key` - If *yes*, generate and authorize SSH key for the user (default: *no*).

In case, the user should be **deleted** the following **optional** attributes will take effects:

* `uid` - The numeric user id for the user. This is required for uid consistency
  across systems.
* `remove` - If *yes*, remove user's home directory and mail spool (default: *no*).
* `force` - If *yes*, removal user's directories (default: *no*).

Add `users_groups` variable containing the list of user groups to create or delete.
A good place to put this is in `group_vars/all` or `group_vars/groupname`,
if you only want the user groups to be on certain machines.

The following attributes are **required** for each user group:

* `name` - The group name.
* `state` - This can be either *present* or *absent*
  - *present* will create the group (default).
  - *absent* will delete the group.

The following **optional** attributes will take effects:

* `gid` - The numeric group id for the group. This is required for gid consistency
  across systems.

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the last 3 release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- rembik.bootstrap

```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/users.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.6|ansible 2.7|ansible devel|
|------------|-----------|-----------|-------------|
|alpine-edge*|yes|yes|yes*|
|alpine-latest|yes|yes|yes*|
|archlinux|yes|yes|yes*|
|centos-6|yes|yes|yes*|
|centos-latest|yes|yes|yes*|
|debian-latest|yes|yes|yes*|
|debian-stable|yes|yes|yes*|
|debian-unstable*|yes|yes|yes*|
|fedora-latest|yes|yes|yes*|
|fedora-rawhide*|yes|yes|yes*|
|opensuse-leap|yes|yes|yes*|
|opensuse-tumbleweed|yes|yes|yes*|
|ubuntu-artful|yes|yes|yes*|
|ubuntu-devel*|yes|yes|yes*|
|ubuntu-latest|yes|yes|yes*|

A single star means the build may fail, it's marked as an experimental build.

Testing
-------

[Unit tests](https://travis-ci.org/rembik/ansible-role-users) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/rembik/ansible-role-users/issues)

To test this role locally please use [Molecule](https://github.com/metacloud/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

Run the [ansible-galaxy](https://github.com/ansible/galaxy-lint-rules) and [my](https://github.com/robertdebock/ansible-lint-rules) lint rules if you want your change to be merges:

```shell
git clone https://github.com/ansible/ansible-lint.git /tmp/ansible-lint
ansible-lint -r /tmp/ansible-lint/lib/ansiblelint/rules .

git clone https://github.com/robertdebock/ansible-lint /tmp/my-ansible-lint
ansible-lint -r /tmp/my-ansible-lint/rules .
```

License
-------

Apache-2.0


Author Information
------------------

[Brian Rimek](https://github.com/rembik)
