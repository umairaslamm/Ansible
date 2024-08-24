# Roles

vagrant up
vagrant ssh-config
ansible all -i hosts --limit host1 -m ping
ansible all -i hosts --limit host2 -m ping

## Install tree for viewing directory structure

##
    brew install tree

## Create a test role
```
ansible-galaxy init testrole1
cd testrole1
tree
bat defaults/main.yml
bat 010_roles.yml
bat tasks/main.yml
ansible-playbook 010_roles.yml
```

Add the following to vars/main.yml 
myvar: This is the value from vars in role 

```
bat testrole1/vars/main.yml
ansible-playbook 010_roles.yml
```

cli has the highest precedence

```
ansible-playbook 010_roles.yml -e "myvar='This is from cli'"
```
