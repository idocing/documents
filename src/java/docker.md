# jdk

## build jdk (debian)
```
FROM debian:10.0
COPY jdk-17 /usr/local/jdk
COPY apache-maven /usr/local/maven
COPY gradle-8.0 /usr/local/gradle
COPY gradle-8.0-bin.zip /root/.gradle/wrapper/dists/gradle-8.0-bin.zip

RUN apt update -y \
&& apt install -y tzdata less curl wget telnet vim zip unzip git \
&& \cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
&& apt autoremove \
&& apt autoclean \
&& apt clean

ENV JAVA_HOME=/usr/local/jdk
ENV CLASSPATH=${JAVA_HOME}/lib
ENV MAVEN_HOME=/usr/local/maven
ENV GRADLE_HOME=/usr/local/gradle
ENV GRADLE_USER_HOME=/root/.gradle
ENV PATH=${PATH}:${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${GRADLE_HOME}/bin
```


## build jdk (oraclelinux)
```
FROM oraclelinux:8.0
COPY jdk-17 /usr/local/jdk
COPY apache-maven /usr/local/maven
COPY gradle-8.0 /usr/local/gradle
COPY gradle-8.0-bin.zip /root/.gradle/wrapper/dists/gradle-8.0-bin.zip

RUN yum makecache -y \
&& yum install -y tzdata less curl wget telnet vim zip unzip git \
&& \cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
&& yum clean all

ENV JAVA_HOME=/usr/local/jdk
ENV CLASSPATH=${JAVA_HOME}/lib
ENV MAVEN_HOME=/usr/local/maven
ENV GRADLE_HOME=/usr/local/gradle
ENV GRADLE_USER_HOME=/root/.gradle
ENV PATH=${PATH}:${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${GRADLE_HOME}/bin
```


## build jdk myself
```
FROM irepoing/debian:base
COPY jdk-17 /usr/local/jdk
COPY apache-maven /usr/local/maven
COPY gradle-8.0 /usr/local/gradle
COPY gradle-8.0-bin.zip /root/.gradle/wrapper/dists/gradle-8.0-bin.zip

ENV JAVA_HOME=/usr/local/jdk
ENV CLASSPATH=${JAVA_HOME}/lib
ENV MAVEN_HOME=/usr/local/maven
ENV GRADLE_HOME=/usr/local/gradle
ENV GRADLE_USER_HOME=/root/.gradle
ENV PATH=${PATH}:${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${GRADLE_HOME}/bin
```