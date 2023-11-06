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

Working playbooks:
- fwebos_virtual_server.yml
- fwebos_virtual_ip.yml
- fwebos_virtual_server_vip.yml

mostly working playbooks:
- fwebos_certificate_ca.yml
Will continue to add the same ca cert - not idempotent.

- fwebos_certificate_local_csr.yml 
You can create the csr, but no way to download it automatically. Once you have downloaded 
it manually, you need to create the certificate manually, and store it somewhere.
- fwebos_certificate_local_import_certificate.yml
You can't upload a certificate where the CSR was not generated on the Fortiweb.
Supposedly you can upload the certificate and the key, but this hasn't worked yet for me.

