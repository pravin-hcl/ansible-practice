# Ansible Dynamic Inventory

- Mostly notice the `plugin` used here `amazon.aws.aws_ec2`

## Command to Run

- For listing the Details of the Server
```
ansible-inventory -i aws_ec2.yml --list
```

- Graph command
```
ansible-inventory -i aws_ec2.yml --graph
```

