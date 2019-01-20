users
=========

[![Build Status](https://travis-ci.org/rembik/ansible-role-users.svg?branch=master)](https://travis-ci.org/rembik/ansible-role-users)

The purpose of this role is to manage users and their groups on your system.

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
    - rembik.bootstrap
    - rembik.users

```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for users

# Create a group for every user and make that their primary group
users_group_per_user: true
# If no group per user is created, then this is the primary group all users belong to
users_group: users
# Create home dirs for new users (needed for ssh key setup)
users_create_home: true
# The default sudo options for a user if sudo is enabled and none are specified
users_default_sudo_options: "ALL=(ALL) NOPASSWD: ALL"
# The default shell for a user if none is specified
users_default_shell: /bin/bash
# The local directory to find/store generated ssh keys
users_ssh_key_dir: ssh_keys

# Lists of users to create or delete
users: []

# List of user groups to create or delete
users_groups: []

```

### Users

Add a users variable containing the list of users to create or delete. A good place to put
this is in `group_vars/all` or `group_vars/groupname` if you only want the
users to be on certain machines.

The following attributes are *required* for each user:

* name - The user's name.
* state - This can be either 'present' or 'absent'
  - 'present' will create the user (default).
  - 'absent' will delete the user.

In case, the user should be *created* the following *optional* attributes will take effects:

* comment - The full name of the user (gecos field).
* home - The home directory of the user to create (defaults to '/home/<user.name>').
* uid - The numeric user id for the user. This is required for uid consistency
  across systems.
* gid - The numeric group id for the group. Otherwise, the
  uid will be used.
* password - If a hash is provided then that will be used, but otherwise the
  account will be locked.
* update_password - This can be either 'always' or 'on_create'
  - 'always' will update passwords if they differ (default).
  - 'on_create' will only set the password for newly created users.
* group - The overridden primary group for the user (defaults to 'users').
* groups - The list of supplementary groups for the user.
* append - If yes, will only add groups, not set them to just the list in groups.
* cron - Whether to create cron permission for the user.
* sudo - Whether to create sudo options for the user.
* sudo_options - The overridden sudo options for the user (default to
  'ALL=(ALL) NOPASSWD: ALL').
* shell - The user's shell (defaults to '/bin/bash').
* profile - The block settings for the custom user shell profile.
* ssh_key - The list of authorized SSH keys for the user. Each public SSH key
  should be included directly and should have no newlines.
* generate_ssh_key - Whether to generate and authorize SSH key for the user.

In case, the user should be *deleted* the following *optional* attributes will take effects:

* uid - The numeric user id for the user. This is required for uid consistency
  across systems.
* remove - Whether to remove user's home directory and mail spool.
* force - Whether to removal user's files.

### User groups

Add a users_groups variable containing the list of user's groups to create or delete. A good place to put
this is in `group_vars/all` or `group_vars/groupname` if you only want the
users to be on certain machines.

The following attributes are *required* for each group:

* name - The group's name.
* state - This can be either 'present' or 'absent'
  - 'present' will create the group (default).
  - 'absent' will delete the group.

The following *optional* attributes will take effects:

* gid - The numeric group id for the group. This is required for gid consistency
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
