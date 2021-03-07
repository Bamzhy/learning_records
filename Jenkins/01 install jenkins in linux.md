### download deployments
- jenkins.war [link](https://jenkins.io/download/)
- jdk1.8
- tomcat

### install deployments
- change environemnt varibales
```
# tar zxf jdk-8u45-linux-x64.tar.gz 
# mv jdk-8u45-linux-x64 /usr/local/jdk1.8 
# vi /etc/profile 
JAVA_HOME=/usr/local/jdk1.8 
PATH=$PATH:$JAVA_HOME/bin
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar 
export JAVA_HOME PATH CLASSPATH
# source /etc/profile
```

```
# tar zxf apache-tomcat-8.5.32.tar.gz 
# mv apache-tomcat-8.5.32 /usr/local/tomcat-jenkins 
# rm /usr/local/tomcat-jenkins/webapps/* -rf 
# unzip jenkins.war -d /usr/local/tomcat-jenkins/webapps/ROOT 
# cd /usr/local/tomcat-jenkins/bin/ 
# ./startup.sh 
# tail ../logs/catalina.out -f 
```

### get the initialize key
- cd 