## Instalación Apache Tomcat 9 en Ubuntu 18.04

```
sudo apt-get update -y
sudo apt-get upgrade -y
```
```
sudo apt-get install default-jdk -y
java --version
```
```
sudo apt-get install unzip
```
```
sudo groupadd tomcat
sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
``` 
```
wget https://www-eu.apache.org/dist/tomcat/tomcat-9/v9.0.27/bin/apache-tomcat-9.0.27.zip
unzip apache-tomcat-9.0.27.zip
sudo mv apache-tomcat-9.0.27 /opt/tomcat
sudo chmod -R 755 /opt/tomcat/
sudo chown -R tomcat:tomcat /opt/tomcat
``` 
```
sudo nano /opt/tomcat/conf/tomcat-users.xml
```
*`</tomcat-users>
*`<role rolename="manager-gui"/>
*`<role rolename="admin-gui"/>
*`<user username="admin" password="password" roles="manager-gui,admin-gui"/>
```



