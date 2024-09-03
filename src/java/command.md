# java command

## java

### java -jar
```
java -Dloader.path=lib -jar app.jar
```

### java -server / java -client
```
java -server -jar app.jar
```

### java -cp
```
java -cp /path/config:/path/app.jar com.xxx.App
```

### java params
```
java $JAVA_OPTS -Dfile.encoding=UTF-8 -Duser.timezone=Asia/Shanghai -jar app.jar
```