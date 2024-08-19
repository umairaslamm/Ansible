# Ansible Playbooks


Lets bring up the vm's
##
    vagrant up

## First playbook with three tasks
- upgrade all apt packages
* add user
+ copy file hosts with permissions

### Setup inventory file to avoid specifying the location with -i

```
cat << EOF > ansible.cfg
[defaults]
inventory=./hosts
EOF
```

#### Ansible configuration file

https://docs.ansible.com/ansible/latest/reference_appendices/config.html#ansible-configuration-settings

The configuration file - changes can be made and used in a configuration file which will be searched for in the following order:

ANSIBLE_CONFIG (environment variable if set)

ansible.cfg (in the current directory)

~/.ansible.cfg (in the home directory)

/etc/ansible/ansible.cfg

Ansible will process the above list and use the first file found, all others are ignored.

```
ansible-inventory --list
```

Test connectivity

```
ansible all -i hosts --limit host1 -m ping
ansible all -i hosts --limit host2 -m ping
```


## Executing first playbook
```
ansible-playbook 001_first_playbook.yml
```
