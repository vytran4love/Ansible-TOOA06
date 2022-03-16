# Lab Inventory

## Description
This lab will help you more understand about Inventory and group\_vars. 

## Exercise

1. Create a static Inventory with following description:
  - Web ( ip 10.0.0.71, 10.0.1.71, 10.0.2.70, 10.0.2.71)
  - Api ( ip 10.0.0.72, 10.0.1.72, 10.0.2.72, 10.0.2.73)
  - Environment nightly: 10.0.0.71, 10.0.0.72 => using ssh\_key: dev.pem
  - Environment staging: 10.0.1.71, 10.0.1.72 => using ssh\_key: staging.pem
  - Environment prod: 10.0.2.71, 10.0.2.72 => using ssh\_key: prod.pem
  - user\_ssh: ubuntu

2. Using group\_var to define vars 

## Ansible-inventory

Command check inventory

```
ansible-inventory -i hosts --graph
```

