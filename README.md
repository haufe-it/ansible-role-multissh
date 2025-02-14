multissh
========

Configure multiple instances of SSHd to listen on separate IPs and/or ports using a separate host key.

Requirements
------------

- Debian

Role Variables
--------------

| Name                         | Description                                         |
|-                             |-                                                    |
| instance                     | (arbitrary) name of the SSH instance                |
| kbdinteractiveauthentication | sshd\_config KbdInteractiveAuthentication           |
| passwordauthentication       | sshd\_config PasswordAuthentication                 |
| listenaddresses              | List of IP addresses this instance should listen on |
| hostkey                      | SSH private key for the instance                    |

Example Playbook
----------------

```yaml
- hosts: myserver
  roles:
    - role: haufe_it.multissh
      instance: instance1.example.org
      listenaddresses:
        - 2001:db8::1
      hostkey: "{{ vault.instance1_hostkey }}"
    - role: haufe_it.multissh
      instance: instance2.example.org
      listenaddresses:
        - 2001:db8::2
      hostkey: "{{ vault.instance2_hostkey }}"
```

License
-------

GPL-3.0-only

Author Information
------------------

Jakob Haufe <jakob@haufe.it>
