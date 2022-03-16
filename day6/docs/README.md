ansible -i hosts demo -e ansible_python_interpreter=/usr/bin/python3 -m ping

```
192.168.33.12 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
192.168.33.11 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

```
ansible -i hosts "demo[0]" -e ansible_python_interpreter=/usr/bin/python3 -m ping
192.168.33.11 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

```
ansible -i hosts "demo" -l '192.168.33.11,192.168.33.12' -e ansible_python_interpreter=/usr/bin/python3 -m ping
192.168.33.11 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
192.168.33.12 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```


```
ansible -i hosts "demo" -l '192.168.33.11,192.168.33.12' -e ansible_python_interpreter=/usr/bin/python3 -m systemd -a "name=nginx state=restarted" -b
```

```
ansible -i hosts "demo" -l '192.168.33.11,192.168.33.12' -e ansible_python_interpreter=/usr/bin/python3 -m shell -a "touch /home/vagrant/abc.txt && chown vagrant:vagrant /home/vagrant/abc.txt" -b
```

```
ansible -i hosts "demo" -l '192.168.33.11' -e ansible_python_interpreter=/usr/bin/python3 -m file -a "dest=/home/vagrant/demo-mkdir owner=vagrant group=vagrant state=directory" -b
```
