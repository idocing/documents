# jvm

## get jvm info

```
jinfo -h
jinfo -flags <pid>
```

## get jvm state

```
jstat -h
jstat -gc <pid>
```

## get jvm stack

```
jstack -h
jstack <pid>
```

## get jvm dump file

```
jmap -h
jmap -dump:<live,>format=b,file=out.dump <pid>
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/tmp
```
