# jvm

## get dump file
```
jmap -dump<:live>,format=b,file=out.dump pid

-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/tmp
```