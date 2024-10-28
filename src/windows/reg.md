# reg

## get all key
```
reg query "HKCU\Environment"
```

## get val
```
reg query "HKCU\Environment" /v VariableName
```


## start item

### user
```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```

### system
```
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
```

### service
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services
```
