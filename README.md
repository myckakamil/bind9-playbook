Bind9 Playbook
===
Playbook ansible for automated [Bind9](https://www.isc.org/bind/) deployment. 

Quick start
---
- Clone repository
- Customize your inventory file
- Set your variables
- Run playbook
```
ansible-playbook -i inventory.ini main.yaml
```

Requirements
---
- RHEL 9
- Python3 installed
- Root or sudo access

Inventory setup
---
Create `inventory.ini` file with your server details:
```ini
[dns]
10.20.30.10
```

Configuration
---
All DNS records are stored in `vars/config.yaml`
```yaml
---
ansible_user: admin
bind_domains:
  - name: example.net
    network: "10.20"
    serial: 2025010101
    nameserver_ip: 10.20.30.10
    hosts:
      - name: dns
        type: A
        ip: 10.20.30.10
      - name: router
        type: A
        ip: 10.20.30.1
```


Todo
---
- [ ] - make this playbook compatible with Debian systems
- [ ] - improve configuration file
- [ ] - add block list
