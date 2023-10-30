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
