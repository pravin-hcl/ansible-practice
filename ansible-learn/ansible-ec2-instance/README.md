### Install Python First

### Check and Install Boto3 using pip

### Install Ansible AWS Collection from Ansible Galaxy 
```
ansible-galaxy collection install amazon.aws --force
```

### Creating Ansible Password File
```
openssl rand -base64 2048 > vault.pass
```

### Creating Viewing Ansible Vaults

It should be like in this fomat: `AWS_Access_Key:` , Like the same for Secret Key and region.

```
ansible-vault create groups/aws_login.yml --vault-password-file=vault.pass
ansible-vault view groups/aws_login.yml --vault-password-file=vault.pass
ansible-vault edit groups/aws_login.yml --vault-password-file=vault.pass
```

### Before running the below command, create the pass and the above vault file.

### Anisble command for Running the Ansible Command
```
ansible-playbook -i inventory.ini ec2_create.yml -e @group_vars/aws_login.yml --vault-password-file=vault.pass
```
