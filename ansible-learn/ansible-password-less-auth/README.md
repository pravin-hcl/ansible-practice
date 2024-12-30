


### Create the key file in local machine

- Create the Pub Keyfile, by leaving everything as default.
```
ssh-keygen
```
- the above will create the file in  `~/.ssh/` folder.

- The instance pem file should be present in the current local machine where anisble is running, or else copy the pem file using scp command. For this check the **copy-file-to-remote-server** folder in this same repo.

## Using Pem file
### Run the command to copy the pub file from local to remote server


```
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
```


### Example Command:
```
ssh-copy-id -f "-o IdentityFile ansible-keypair.pem" ubuntu@3.107.172.85
```


## Using Password

- Go to the file `/etc/ssh/sshd_config.d/60-cloudimg-settings.conf`
- Update `PasswordAuthentication yes`
- Restart SSH -> `sudo systemctl restart ssh`

### try this as 
```
ssh-copy-id userName@IP_Address
```
- Now It will ask forthe Password.
  
