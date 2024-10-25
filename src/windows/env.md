# env

## tmp env
```
set key=val
```

## del tmp env
```
set key=
```

## user env
```
setx key val
```

## del user env
```
setx key ""
```

## machine env
```
setx /m key val
```

## handle env by reg

> user env
```
reg query "HKCU\Environment" /v VariableName
reg add "HKCU\Environment" /f /v VariableName /t REG_SZ /d "NewValue"
reg delete "HKCU\Environment" /f /v VariableName
```

> machine env
```
reg query "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment" /v VariableName
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment" /f /v VariableName /t REG_SZ /d "NewValue"
reg delete "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment" /f /v VariableName
```
