Role Name
=========

Install the s3cmd command on Debian and RedHat family.

s3cmd is used to put/get/ls from s3 storage.

Requirements
------------

RHEL servers should have a valid subscription in order to user yum/dnf.

Role Variables
--------------

* `s3_access_key`: required
* `s3_secret_key`: required
* `s3_host_bucket`: default bucket (required)
* `s3_human_readable_sizes`: true/false to display file size in k/M/G instead of bites
* `s3_host_base`: The URI of your s3 server
* `s3_website_endpoint`: The API URI
* `s3cmd_user`: The user you wish to create a *.s3cfg* file for. Doesn't accept a list.
* `s3_global_env_var`: true/false if you want a variable, called $S3, that contain the default bucket. This will create the file */etc/profiles.d/s3.sh*. This enables the user to do: `s3cmd ls $S3`.

Dependencies
------------

None


Example Inventory
-----------------

group_vars/main.yml:

```yaml
---
s3_host_base: "s3.example.com"
s3_website_endpoint: "https://s3.example.com/_/s3browser/"
s3_access_key: "{{ vault_s3_access_key }}"
s3_secret_key: "{{ vault_s3_secret_key }}"
s3_host_bucket: "svc0000-12345678912345678912345678912345"
s3_human_readable_sizes: true
s3_global_env_var: true
```

group_vars/vault.yml:

```
---
vault_s3_access_key: ***
vault_s3_secret_key: ***
```


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: s3cmd
           vars:
             s3cmd_user: appadm
         - role: s3cmd
           vars:
             s3cmd_user: root
License
-------

MIT

Author Information
------------------

This role was created by [Laurent Indermühle](https://github.com/Honiix)
