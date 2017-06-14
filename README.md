mgt-users
=========

[![License](https://img.shields.io/badge/license-BSD-blue.svg?style=flat)]

[![Platform](http://img.shields.io/badge/platform-centos-932279.svg?style=flat)](#)
[![Platform](http://img.shields.io/badge/platform-redhat-cc0000.svg?style=flat)](#)
[![Platform](http://img.shields.io/badge/platform-ubuntu-dd4814.svg?style=flat)](#)


- manage user account and group
- manage ssh authorized_keys
- manage sudo permission
- manage enable_user (for special purpose)


## Requirements

- [ansible][ansible] >= 2.2


## Role Variables

- **debug**: flag to run debug tasks. (True or False, default: false)
- **nolog**: flag for no_log. (True or False, default: True - won't print stdout)
- **user_list**: list of users' setting.
- **sbin_nologin**: nologin shell path. (default: /sbin/nologin)


## Dependencies

None


## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }


## License

BSD


## Author Information

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
