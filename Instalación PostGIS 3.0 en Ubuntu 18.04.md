## Instalación PostGIS 3.0 en Ubuntu 18.04

```
sudo apt update 
sudo apt -y install vim bash-completion wget
sudo apt -y upgrade
sudo reboot
```
```
echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" |sudo tee  /etc/apt/sources.list.d/pgdg.list
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt update
```
```
sudo apt -y install gnupg2
sudo apt install postgis postgresql-12-postgis-2.5
``` 
