``` For Runtime variable passing
ansible-playbook -v -i inventory/vm-setup-playbook/hosts main.yml --extra-vars '{"version":"1.0", "runtime_value":"Pravin Velusamy"}'
```

``` Bash Command
ansible-playbook -v -i inventory/vm-setup-playbook/hosts main.yml
```

``` Runtime Vars file Passing 
ansible-playbook -v -i inventory/vm-setup-playbook/hosts main.yml --extra-vars '@runtime-vars.yml'
```

