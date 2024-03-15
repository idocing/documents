# ssh

## ssh config (~/.ssh/config)
```
Host alias_name
    HostName target_host
    User username
    Port port_number
    IdentityFile path_to_private_key
```

## ssh authorized
```
local ~/.ssh/id_rsa.pub
remote ~/.ssh/authorized_keys
```