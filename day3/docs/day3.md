## Ansible-playbook

#### Command run

```
ansible-playbook -i inventory main.yml
```

E.g:
```
ansible-playbook -i hosts main-playbook.yml -v -e hostname="demo[1]"
ansible-playbook -i hosts main-playbook.yml -v -e hostname="demo"
ansible-playbook -i hosts main-playbook.yml -v -e hostname=demo -l "192.168.33.11"
```

#### Writing a playbook

```
- hosts: ...
  tasks: ...
- hosts: ...
  tasks: ...
- hosts: ...
  tasks: ...
```

Content:
```
- hosts:
    - all
  tasks:
    - action: ping
```

#### Check and diff

--check will tell you which changes would be made, without actually making them. (Not all modules support this)
--diff shows you the differences between the old and new files

```
ansible-playbook -i hosts main-playbook.yml -v -e hostname=demo -l "192.168.33.11" --check --diff
```

#### Tags

```
- hosts: "{{hostname}}"
  gather_facts: yes
  become: yes
  pre_tasks:
  - name: 'install python'
    raw: sudo apt-get update && sudo apt-get -y install python3
    tags: ['always']
  tasks:
  - name: ping
    action: ping
    tags: check
  - name: ensure package cache is up to date
    apt: update_cache=yes cache_valid_time=3600
    tags: install
```
Run command

```
ansible-playbook -i hosts main-playbook.yml -v -e hostname=demo -l "192.168.33.11" -t check
ansible-playbook -i hosts main-playbook.yml -v -e hostname=demo -l "192.168.33.11" -t install
```

#### Limit to specific hosts

```
ansible-playbook -i hosts main-playbook.yml -v -e hostname="demo[1]"
ansible-playbook -i hosts main-playbook.yml -v -e hostname=demo -l "192.168.33.11"
```
