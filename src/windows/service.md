# service

## sc list
```
sc query state= all
```

## sc query
```
sc query <ServiceName>
```

## sc create
```
sc create <ServiceName> binPath= "<PathToExecutable>"
```

## sc start
```
sc start <ServiceName>
```

## sc stop
```
sc stop <ServiceName>
```

## sc delete
```
sc delete <ServiceName>
```

## sc failure
```
sc failure <ServiceName> reset= 0 actions= restart/0
```

## sc change type
- auto
- demand
- disabled
```
sc config <ServiceName> start= <StartupType>
```

## sc setting dependency
```
sc config <ServiceName> depend= <Dependency>
```
