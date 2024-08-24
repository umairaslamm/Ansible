# Ansible Playbooks


Lets bring up the vm's
##
    vagrant up

## First playbook -- a couple of tasks
* add user
+ copy file with permissions

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


### Executing first playbook
```
ansible-playbook 001_first_playbook.yml
```

## Second playbook - execute tasks with root privileges

https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_privilege_escalation.html

- upgrade all apt packages
* install package
+ start and register service as startup up


```
ansible-playbook 002_esclated_privilege_playbook.yml
```

## Third playbook - using variables

```
ansible-playbook 003_variables.yml
```

## Lets use some tags

select tags
```
ansible-playbook 004_tags.yml --tags ntp
```
list tags
```
ansible-playbook 004_tags.yml --list-tags
```
skip tags
```
ansible-playbook 004_tags.yml --skip-tags ntp_start
```

## Using command line to control execution

```
ansible-playbook 004_tags.yml --start-at-task 'Install NTP'
```

```
ansible-playbook 004_tags.yml --step
```

## Specifying variables in inventory file

add the following to hosts file
[all:vars]
temp_file=/tmp/somefile

```
bat hosts
bat 005_invvars.yml
ansible-playbook 005_invvars.yml -e file_state=touch
```

## Using jinja templating

```
bat jinja2.j2
bat 006_use_templates.yml
ansible-playbook 006_use_templates.yml
```
### Steps to fix apache2 startup due to port collision
```
vagrant ssh host1
sudo vi /etc/apache2/ports.conf -- replace Listen 80 with Listen 8080
sudo vi /etc/apache2/sites-enabled/000-default.conf -- replace <VirtualHost *:80> with <VirtualHost *:8080>
sudo systemctl restart apache2
exit
```

