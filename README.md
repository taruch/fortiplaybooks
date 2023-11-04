# fortiplaybooks

Repo to hold my Fortigate Anisble playbooks. Use at your own risk.


I set up an inventory file like below with the variables configured for my environment:

```ini
[fortiweb]
fortiweb1    ansible_host=<insert host here>

[fortigates]
fortigate1 ansible_host=<insert host here>

[fortiweb:vars]
ansible_user=<insert user here>
ansible_password=<insert password here>

[fortigates:vars]
ansible_user=<insert user here>
ansible_password=<insert password here>
```

```sh
cat group_vars/fortigates.yml 
```
```yaml
ansible_network_os: fortinet.fortios.fortios
ansible_connection: httpapi
ansible_httpapi_use_ssl: yes
ansible_httpapi_validate_certs: no
ansible_httpapi_port: 443
```
```sh
[fortiplaybooks]$ cat group_vars/fortiweb.yml 
```
```yaml
---
ansible_network_os: fortinet.fortiweb.fwebos
ansible_connection: httpapi
ansible_httpapi_use_ssl: yes
ansible_httpapi_validate_certs: no
ansible_httpapi_port: 8443
```

Make sure that the ansible_connection: httpapi is specified in the group_vars or inventory.

Had my first successful run of any fortiweb module, to create a virtual server:
ansible-navigator run -mstdout fwebos_virtual_server.yml 


fwebos_virtual_server.yml is working now