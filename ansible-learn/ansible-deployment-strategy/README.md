
``` For Env output - Use Verbose at the end
ansible-playbook -i inventory/vm-setup-playbook/hosts main.yml -v
```

## Default Command

```bash
ansible-playbook -i inventory/vm-setup-playbook/hosts main.yml -v
```

## Using "--limit" Command

```bash
ansible-playbook -i inventory/vm-setup-playbook/hosts main.yml -v --limit target-1
```

