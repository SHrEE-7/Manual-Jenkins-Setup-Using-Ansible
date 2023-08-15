## Manual setup of jenkins container with already created instance. 

### Ansible Installation-Master
Note : Use amazon-linux as master instance. 
```
yum update 
yum install ansible
```

1. Check the source & destination paths in ansible-playbook.yaml of jenkins folder.
2. configure the hosts file at /etc/ansible/hosts location in master / anible controller instance


3. make these chages in Master Instance at location /etc/ansible/ansible.cfg 

```
[defaults]
host_key_checking = False
ansible_python_interpreter=/usr/bin/python3
```

### Configuration of hosts file-Master
1. We have used docker_server as group name in hosts file & calling that group name in ansible-playbook.yaml. Define the ip address of slave instance [docker_server] in hosts file.


### Launch new instance of amazon-linux for slave.
1. insert the Public_IP address of slave in hosts file of master instance.
2. Enable passwordAuthentication of slave instance & we have given username as ```root``` & password as ```root```. These have been defined in the [docker_server:vars] in hosts file in master instance.
3. Expose the expected/required ports in slave security group.

### Ansible Commands 
```
ansible-playbook -i hosts docker_server ansible-playbook.yaml
```
```
ansible --help
```

https://docs.ansible.com/ansible/latest/collections/ansible/builtin/set_fact_module.html 