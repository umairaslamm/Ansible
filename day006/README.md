# Network Management

```
bat 01_ip_address.yml
ansible-playbook 01_ip_address.yml
```

if you get the error

TASK [set_fact] ****************************************************************************

fatal: [localhost]: FAILED! => {"msg": "Failed to import the required Python library (netaddr) on Umairs-MacBook-Pro-i9.local's Python /usr/local/opt/python@3.11/bin/python3.11. Please read the module documentation and install it in the appropriate location. If the required library is installed, but Ansible is using the wrong Python interpreter, please consult the documentation on ansible_python_interpreter"}


```
pip install netaddr
```