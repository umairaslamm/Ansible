# Setup a couple of vms

## Install:

https://www.virtualbox.org

##
    brew install --cask virtualbox
    VirtualBox --help


https://www.vagrantup.com

##
    brew install --cask vagrant
    vagrant --version


## Setup VM using vagrant

```vagrant up```

Display ssh configs

```vagrant ssh-config```

Create Ansible invertory hosts file with configs

```bat hosts```

Test connectivity

```ansible all -i hosts --limit host1 -m ping```

```ansible all -i hosts --limit host2 -m ping```

Lets run a live command

```ansible all -i hosts --limit host2 -a "/bin/echo hello"```

Another example will be to copy file 

```ansible all -i hosts -m ansible.builtin.copy -a "src=./hosts dest=/tmp/hosts"```

Lets verify the copy by sshing into a managed node

```
vagrant ssh host1
cat /tmp/hosts
```

### Some useful vagrant commands

```
vagrant suspend  ## suspends the machine
vagrant resume   ## resume a suspended vagrant machine 
vagrant halt     ## stops the vagrant machine
vagrant destroy  ## stops and deletes all traces of the vagrant machine
```
### Remove ssh keys from known hosts

```
sed -i '' "/11022/d" ~/.ssh/known_hosts

sed -i '' "/12022/d" ~/.ssh/known_hosts
```