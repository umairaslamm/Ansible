# Vault

## File level vaulting

Create vaulted file
```
ansible-vault create test1.yml
```
Try executing vaulted file
```
ansible-playbook test1.yml
```
Need to specifiy flag for executing vaulted files
```
ansible-playbook test1.yml --ask-vault-pass
```
Editing a vaulted file
```
ansible-vault edit test1.yml
```
Ecrypt an existing file
```
ansible-vault encrypt 01_first_playbook.yml
```
Decrypt an existing file
```
ansible-vault decrypt 01_first_playbook.yml
```

##

create a encrypted strng
```
ansible-vault encrypt_string --vault-id @prompt mysupersecretstring
```
copy it to 02_encrypted_vars.yml playbook
```
bat 02_encrypted_vars.yml
```
try executing the playbook
```
ansible-playbook 02_encrypted_vars.yml --ask-vault-pass
```

