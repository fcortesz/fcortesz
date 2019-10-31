## Instalación pgAdmin4 en Ubuntu 18.04
```
echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" |sudo tee  /etc/apt/sources.list.d/pgdg.list
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt update
```
```
sudo apt install pgadmin4 pgadmin4-apache2
``` 
*`Abrir navegador http://[ServerIP_or_domain]/pgadmin4.`* 
