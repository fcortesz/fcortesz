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
*`</tomcat-users>`*<br/> 
**`<role rolename="manager-gui"/>`**<br/>
**`<role rolename="admin-gui"/>`**<br/> 
**`<user username="admin" password="password" roles="manager-gui,admin-gui"/>`**
```
```
sudo nano /opt/tomcat/webapps/host-manager/META-INF/context.xml
```
*`<Context antiResourceLocking="false" privileged="true" >`*<br/>
**`<!--`**<br/>
*`  <Valve className="org.apache.catalina.valves.RemoteAddrValve"`*<br/>
*`         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />`*<br/>
**`-->`**<br/>
*`  <Manager sessionAttributeValueClassNameFilter="java\.lang\.(?:Boolean|Integer|Long|Number|String)|org\.apache\.catalina\.filters\.CsrfPreventionFilter\$LruCache(?:\$1)?|java\.util\.(?:Linked)?HashMap"/>`*<br/>
*`</Context>`*



