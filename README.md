Role Name
=========

An ansible role for setting up a list of AWS VPC subnets

Requirements
------------

Uses the ec2_vpc_subnet extras module (http://docs.ansible.com/ansible/ec2_vpc_subnet_module.html)
Uses the python boto package for cloud services.

Role Variables
--------------

One to many subnets to be created for an application.

```
subnets:
  - availability_zone: AZ for the subnet. ex. us-west-1a
    cidr: IP range for the subnet
    region: Region for the subnet. ex. us-west-1
    vpc_id: VPC ID for the subnet. ex. vpc-abc123
    app_name: App that the subnet will support. ex. waffles
    app_environment: App environment. ex. production
    name_tag: Used to tag the subnet for things like dynamic inventory. ex. "us-west-1a-waffles-production"
```

Dependencies
------------

None

Example Playbook
----------------


```
- name: This creates the VPC subnets the application
  hosts: localhost
  vars_files:
    - "vars/{{ environment }}/subnets.yml"
  connection: local
  roles:
    - ansible-vpc-subnets
```

Command-line example usage

```ansible-playbook subnets.yml -i local -e "environment=production"```

License
-------

BSD

Author Information
------------------

https://github.com/amaabca
