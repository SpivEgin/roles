```
- hosts: buildser
  vars:
    db_admin: purpleteelpitz
    db_groups: cockroach_db
    db_passwd: $6$T9b111Kl.d$FQVBjfi7IVkcuhcth.VVhQzwirea4EB3.mSUiU/2ULjnD6hKXPplpJ92I5P6rWekITsEA8Saf1qjOogMZQ75n0
    db_description: CockroachDB Install, golang
    cockroach_masterNode_ip: '192.168.1.80'
    cockroachDBversion: '1.0.1a'
    insecure: "--insecure"
    node_db: "0"
    ip_address: "{{buildser}}"
  roles:
    -  cockroachdb

```

## Create a var file in your playbook
```

## Database vars
# Cockroach service user
db_admin: purpleteelpitz
db_groups: cockroach
db_passwd: $6$T9b111Kl.d$FQVBjfi7IVkcuhcth.VVhQzwirea4EB3.mSUiU/2ULjnD6hKXPplpJ92I5P6rWekITsEA8Saf1qjOogMZQ75n0
# Database name
# Vars for database
db_usr:
  - tlm_django
db_pwd:
  - tlmReady-2-Go
db_name:
  - tlm_django
domain_name:
  - tpnfc.net
  - tpnfc.us
salt_cookie: A7rmz9sisra7o3daFCkd
# Service Description
db_description: CockroachDB Install, golang

#Ip address for master node
cockroach_masterNode_ip: '192.168.1.80'
cockroachDBversion: "1.0.1a"
insecure: "--insecure"
# Node id 0 == master
node_db: "0"
# host main ip address public if on internet
ip_address: "{{hosts}}"

```
Then include in by pointing to your file in your playbook.  This will then be imported into the tasks/main.yml as "vars_file".  Note rinse and repeat for each node
```
  roles:
    - {role: cockroachdb, vars_file: your/var/file.yml }


```