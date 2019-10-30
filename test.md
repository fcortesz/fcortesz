>
sudo apt update
sudo apt -y install vim bash-completion wget
sudo apt -y upgrade
sudo reboot

wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" |sudo tee  /etc/apt/sources.list.d/pgdg.list
sudo apt update

sudo apt -y install postgresql-12 postgresql-client-12

systemctl status postgresql.service
systemctl status postgresql@12-main.service
systemctl is-enabled postgresql

sudo su - postgres
psql -c "alter user postgres with password 'StrongAdminP@ssw0rd'"
$ psql
postgres=# \conninfo
postgres=# \q

modificar en archivo /etc/postgresql/12/main/postgresql.conf linea listen_addresses = '*'
reiniciar Ubuntu
