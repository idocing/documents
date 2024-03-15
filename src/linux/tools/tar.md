# tar

## tar compress
```
tar -czvf xxx.tar.gz src
tar -czvf xxx.tar.gz src -C dir
```

## tar extract
```
tar -xzvf xxx.tar.gz
tar -xzvf xxx.tar.gz -C dir
tar -xzvf xxx.tar.gz -C dir --strip-components N  // N=1,2,3...
```