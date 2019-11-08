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
sudo nano /opt/tomcat/webapps/host-manager/META-INF/context.xml
```
*`<Context antiResourceLocking="false" privileged="true" >`*<br/>
**`<!--`**<br/>
*`  <Valve className="org.apache.catalina.valves.RemoteAddrValve"`*<br/>
*`         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />`*<br/>
**`-->`**<br/>
*`  <Manager sessionAttributeValueClassNameFilter="java\.lang\.(?:Boolean|Integer|Long|Number|String)|org\.apache\.catalina\.filters\.CsrfPreventionFilter\$LruCache(?:\$1)?|java\.util\.(?:Linked)?HashMap"/>`*<br/>
*`</Context>`*
```
sudo nano /opt/tomcat/webapps/manager/META-INF/context.xml
```
*`<Context antiResourceLocking="false" privileged="true" >`*<br/>
**`<!--`**<br/>
*`  <Valve className="org.apache.catalina.valves.RemoteAddrValve"`*<br/>
*`         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />`*<br/>
**`-->`**<br/>
*`  <Manager sessionAttributeValueClassNameFilter="java\.lang\.(?:Boolean|Integer|Long|Number|String)|org\.apache\.catalina\.filters\.CsrfPreventionFilter\$LruCache(?:\$1)?|java\.util\.(?:Linked)?HashMap"/>`*<br/>
*`</Context>`*
```
sudo nano /etc/systemd/system/tomcat.service
```
**`[Unit]`**<br/>
**`Description=Tomcat servlet container`**<br/>
**`After=network.target`**<br/>

**`[Service]`**<br/>
**`Type=forking`**<br/>

**`User=tomcat`**<br/>
**`Group=tomcat`**<br/>

**`Environment="JAVA_HOME=/usr/lib/jvm/default-java"`**<br/>
**`Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"`**<br/>

**`Environment="CATALINA_BASE=/opt/tomcat"`**<br/>
**`Environment="CATALINA_HOME=/opt/tomcat"`**<br/>
**`Environment="CATALINA_PID=/opt/tomcat/temp/tomcat.pid"`**<br/>
**`Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"`**<br/>

**`ExecStart=/opt/tomcat/bin/startup.sh`**<br/>
**`ExecStop=/opt/tomcat/bin/shutdown.sh`**<br/>

**`[Install]`**<br/>
**`WantedBy=multi-user.target`**<br/>
```
systemctl status tomcat.service
systemctl is-enabled tomcat
```
*`Abrir navegador http://[ServerIP_or_domain]:8080`*<br/>
*`Abrir navegador http://[ServerIP_or_domain]:8080/manager`*<br/>
*`Abrir navegador http://[ServerIP_or_domain]:8080/host-manager`*



