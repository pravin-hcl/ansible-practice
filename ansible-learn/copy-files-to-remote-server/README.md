## Copy files from local Machine to remote server:

- There are lot of ways to copy the file from local to Remote Sever. But i used the below method.

## Copy files from local Machine to remote server:

- Eg:
```
 scp -i ansible-keypair.pem history.json ubuntu@13.239.36.53:/home/ubuntu/
```

## Syntax 

```
scp -i <identity_file> <files_to_copy_from_local> username@IP:<path_to_paste_file_in_remote_server>
```

