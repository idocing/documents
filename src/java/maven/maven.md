# maven

## deploy

### 1. settings.xml
```
<servers>
    <server>
        <id>one</id>
        <username>admin</username>
        <password>123456</password>
    </server>

</servers>
```

### 2. pom.xml

#### 2.1 distribution
```
<distributionManagement>
    <repository>
        <id>one</id>
        <name>Repository one</name>
        <url>http://one.com/repository/maven-public</url>
        <layout>default</layout>
        <uniqueVersion>false</uniqueVersion>
    </repository>

</distributionManagement>
```

#### 2.2 skip test
```
mvn -DskipTests clean package
mvn -Dmaven.test.skip=true clean package
```
> or
```
<properties>
    <maven.test.skip>true</maven.test.skip>
</properties>
```

#### 2.3 build sub module
```
mvn -am -pl sub1/sub2/sub3 clean package
mvn -Drevision=1.0.0-snapshot -am -pl :sub-artifact clean install
```
