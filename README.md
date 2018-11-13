# Tomcat


### JVM Install

- Open JDK 8
~~~
sudo apt install openjdk-8-jdk -y || sudo yum install java-1.8.0-openjdk-devel -y
~~~

- JAVA HOME location
~~~
#### on centos7
JAVA_HOME=/usr/lib/jvm/java

~~~

### Create Tomcat User
~~~
sudo groupadd tomcat
sudo useradd -M -s /bin/nologin -g tomcat -d /app/tomcat tomcat
~~~

### Install Tomcat

Update Download URL from : http://tomcat.apache.org/download-80.cgi
~~~
cd ~
wget http://apache.tt.co.kr/tomcat/tomcat-8/v8.5.35/bin/apache-tomcat-8.5.35.tar.gz
~~~




### References
- How to insall Apache Tomcat8 on CentOS 7 :

https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-centos-7

