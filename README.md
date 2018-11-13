# Tomcat


### JVM Install

- Open JDK 8
~~~
sudo apt install wget openjdk-8-jdk -y || sudo yum install wget java-1.8.0-openjdk-devel -y
~~~

- JAVA HOME location
~~~
#### on centos7
JAVA_HOME=/usr/lib/jvm/jre

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
sudo mkdir /app/tomcat -p
sudo tar -xvzf apache-tomcat-8*tar.gz -C /app/tomcat --strip-components=1
sudo chgrp -R tomcat /app/tomcat
sudo chown -R tomcat /app/tomcat
~~~


### Enable APR connector ( Option for Performance )
~~~
yum install apr-devel apr-util-devel openssl-devel -y
sudo yum groupinstall "Development Tools"
~~~

~~~
./configure --with-apr=/usr/bin/apr-1-config \
            --with-java-home=/usr/lib/jvm/java-1.8.0 \
            --with-ssl=yes \
            --prefix=/usr

make && make install
~~~



### Install Systemd Unit File ( Service Register )

~~~
sudo vi /etc/systemd/system/tomcat.service
~~~

at /etc/systemd/system/tomcat.services
~~~
# Systemd unit file for tomcat
[Unit]
Description=Apache Tomcat Web Application Container
After=syslog.target network.target

[Service]
Type=forking

Environment=JAVA_HOME=/usr/lib/jvm/jre
Environment=CATALINA_PID=/app/tomcat/temp/tomcat.pid
Environment=CATALINA_HOME=/app/tomcat
Environment=CATALINA_BASE=/app/tomcat
Environment='CATALINA_OPTS=-Xms2G -Xmx2G -server'
Environment='JAVA_OPTS=-Djava.awt.headless=true -Djava.security.egd=file:/dev/./urandom'

ExecStart=/app/tomcat/bin/startup.sh
ExecStop=/app/kill -15 $MAINPID

User=tomcat
Group=tomcat
UMask=0007
RestartSec=10
Restart=always

[Install]
WantedBy=multi-user.target
~~~





### References
- How to insall Apache Tomcat8 on CentOS 7 :

https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-centos-7

