edi_installer
=============

Ansible role that installs edi and its prerequisites on Ubuntu or Debian.

Requirements
------------

The role can be applied to a basic Debian or Ubuntu installation. It might not work in a container as edi makes use of LXD (it would then lead to a nested container scenario).

Role Variables
--------------

The role can be tweaked by changing `edi_user`. By default `edi_user` is set to `gitops`. `edi_user` is the user that will be able to make use of edi.

Dependencies
------------

The role is not based upon any other roles. This role can be combined with another role in order to create a Gitlab or Github runner that is able to build OS images.

Example Playbook
----------------

A basic playbook that makes use of this role could look like this:

```
---
- hosts: all

  vars:
    edi_user: johndoe

  roles:
    - role: edi_installer
      become: true
```

Testing
-------

The following command can be used to apply the role to the local machine for the current user (the user will be added to the group lxd):

```
sudo ansible-playbook --connection=local -i edi_installer/tests/inventory edi_installer/tests/test.yml --extra-vars "edi_user=${USER}"
```

License
-------

MIT

Author Information
------------------

https://www.get-edi.io
