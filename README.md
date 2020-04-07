Ansible OpenDKIM Role
=========

This is simple ansible role to configure opendkim on ubuntu xenial.

Requirements
------------

#### Ubuntu:
**The below requirements are needed on the host that executes this module.**
* python
* python-apt

Role Variables
--------------


|  name | default | description | acceptable values |
|---|---|---|---|
| opendkim_enable |  true | enable role |  |
| opendkim_config_file |  /etc/opendkim.conf | opendkim config file path |  |
| opendkim_pid_file |  /var/run/opendkim/opendkim_pid | opendkim pid file path |  |
| opendkim_socket |  inet:12301@localhost | opendkim socket |  |
| opendkim_user |  opendkim | opendkim user | directory path |
| opendkim_keypath |  /etc/opendkim/keys | path where key saved  |  |
| opendkim_keyTable |  /etc/opendkim/keytable | path to opendkim key table | file path |
| opendkim_signingTable |  /etc/opendkim/signingtable | path to opendkim signing table | file path |
| opendkim_fetch_path |  ./opendkim_keys | destination path on managing node to download keys to | path |
| opendkim_default_key_selector |  default | opendkim default selector | string |
| opendkim_domains | [ { name: "{{ ansible_fqdn }}", selector: "default"} ] | list of domains along with selector name. if selector not mentioned opendkim_default_key_selector used |  |

Example Playbook
----------------

#### example 1:

```yaml
---
# single domain with hostname properly set
- hosts: servers
  roles:
    - role: ghobadimhd.opendkim
```
#### example 2:

```yaml
---
- hosts: servers
  roles:
    - role: ghobadimhd.opendkim
      opendkim_domains:
        - name: example.com
          selector: mta1
        - name: foobar.com
```

License
-------

MIT

Author Information
------------------

Author: Mohammad Ghobadi

Email: ghobadimhd@gmail.com
