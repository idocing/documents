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

## del env by reg
> user env
```
reg delete "HKCU\Environment" /F /V key
```

> machine env
```
reg delete "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment" /F /V key
```
