# jvm

## get jvm info

```
jinfo -flags <pid>
```

## get jvm state

```
jstat -options
jstat -gc <pid>
```

## get jvm stack

```
jstack <pid>
```

## get jvm dump file

```
jmap -dump:<live,>format=b,file=out.dump <pid>
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/tmp
```
