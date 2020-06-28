[![Build Status](https://travis-ci.org/a0s/ansible-role-avahi.svg?branch=master)](https://travis-ci.org/a0s/ansible-role-avahi)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-a0s.avahi-blue.svg)](https://galaxy.ansible.com/a0s/avahi)

avahi-daemon
=======

Install and setup avahi-daemon. 

Role Variables
--------------

`avahi_default_conf_path` (default _"/etc/default/avahi-daemon"_): Path to daemons's defaults 

`avahi_conf_path` (default _"/etc/avahi/avahi-daemon.conf"_): Path to [avahi-daemon.conf](https://linux.die.net/man/5/avahi-daemon.conf)

`avahi_hosts_path` (default _"/etc/avahi/hosts"_): Path to [avahi hosts](https://linux.die.net/man/5/avahi.hosts)

`avahi_default_conf` (default _[]_): Conf defaults for daemon

`avahi_conf` (default _[]_): Main conf. It supports subkeys: `server`, `wide-area`, `publish`, `reflector` and `rlimits`. See https://linux.die.net/man/5/avahi-daemon.conf

`avahi_hosts` (default _[]_): Hosts conf. See https://linux.die.net/man/5/avahi.hosts

Example Playbook
----------------

Avahi-daemon default (Ubuntu's) configuration:

```yaml
- hosts: servers
  roles:
     - a0s.avahi
  vars:
    avahi_default_conf:
      - |
        AVAHI_DAEMON_DETECT_LOCAL=1
    avahi_conf:
      server:
        - |
          use-ipv4=yes
          use-ipv6=yes
          ratelimit-interval-usec=1000000
          ratelimit-burst=1000
      wide-area:
        - |
          enable-wide-area=yes
      publish:
        - |
          publish-hinfo=no
          publish-workstation=no      
```

License
-------

MIT
