# Ansible with localhost

## ad hoc commands

https://docs.ansible.com/ansible/latest/command_guide/intro_adhoc.html

$ ansible [pattern] -m [module] -a "[module options]"

```ansible localhost -m ping```

```ansible localhost -m ansible.builtin.debug -a var=inventory_hostname```

```ansible localhost -m find -a "paths=~/Downloads file_type=directory"```

Install bat - https://github.com/sharkdp/bat

##
        brew install bat

## first playbook
A simple playbook to execute a couple of tasks
##
    bat 01_first_playbook.yml
    ansible-playbook 01_first_playbook.yml


## first challenge
Write a playbook to find files on current path and display them
##
    ansible-playbook 02_first_challenge.yml

