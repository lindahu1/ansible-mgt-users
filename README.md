user_accounts
=========

![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)&nbsp;&nbsp;&nbsp;&nbsp;[![Build Status](https://travis-ci.org/lindahu1/ansible-mgt-users.svg?branch=master)](https://travis-ci.org/lindahu1/ansible-mgt-users#)

![Platform](http://img.shields.io/badge/platform-centos-932279.svg?style=flat) ![Platform](http://img.shields.io/badge/platform-redhat-cc0000.svg?style=flat) ![Platform](http://img.shields.io/badge/platform-ubuntu-dd4814.svg?style=flat) ![Platform](http://img.shields.io/badge/platform-Amazon-3c6eb4.svg?style=flat) ![Platform](http://img.shields.io/badge/platform-opensuse-73ba25.svg?style=flat)

- manage user account and group
- manage ssh authorized_keys
- manage sudo permission
- manage enable_user (for special purpose)
  &nbsp;&nbsp;This function is for lazy administrators:
  &nbsp;&nbsp;`/etc/init.d/enable_{{userid}}` `[start/stop/status]`
   - Change shell: from /sbin/nologin to /bin/bash
   - Set crontab: to change back shell everyday


## Requirements

- [ansible](https://ansible.com) >= 2.2


## Role Variables

- **debug**: flag to run debug tasks. (True or False, default: false)
- **nolog**: flag for no_log. (True or False, default: True - won't print stdout)
- **user_list**: list of users' setting.
- **sbin_nologin**: nologin shell path. (default: /sbin/nologin)
- **stop_cron_hour**: the hour to stop enable_user daily. (default: 23)
- **stop_cron_min**: the minute to stop enable_user daily. (default: 57)


## Dependencies

None


## Example Playbook
```yaml
---
 - hosts: localhost
   become: yes
   roles:
     - { role: lindahu1.user_accounts }
```

## Example user_list
configure user_list in group_vars/all
```yaml
---
user_list:
  test:
    userid: 'test'
    uid: '1001'
    gid: '1001'
    homefolder: /home/test
    shell: /bin/bash
    permit: ALL=(ALL)       ALL
    ensure: present
    sshkey: AAAABxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx=
    sshkeytype: ssh-rsa
    sshkey_ensure: present
    sshkey_exclusive: True
  devops:
    userid: devops
    password: $6$nCkb0HCW$1HLCb8rbT9WOdrFAOK3vbbnGOUK4T7.49qJUHxcTMOmALicKQBOWt7c3EqLQZMNQ9deIBmUJsxcbtbv3hAMRp0
    ensure: present
    permit: ALL=(root)       NOPASSWD:/bin/ping, /bin/ls, /bin/more, /bin/gzip, /bin/tar, /usr/bin/zip, /usr/bin/unzip, /usr/bin/less, /usr/bin/tail, /usr/bin/head, /bin/zcat
    enable_user: true
  testuser:
    ensure: absent
```


## Tags

- **debug**: print out user list.
- **user**: manage all of tasks.
- **authorized_keys**: setup ssh authorized_keys tasks.
- **sudo**: setup sudo tasks.
- **enable_user**: setup enable_user service tasks.

