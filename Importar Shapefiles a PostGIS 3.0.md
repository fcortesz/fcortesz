## Importar Shapefiles a PostGIS 3.0

Subir carpeta de archivos a servidor mediante Winscp o herramienta similar.
Desde linea de comandos linux ejecutar.
```
shp2pgsql -s 4326 -W "UTF-8" xxxxx.shp > xxxxx.sql
psql -d xxxxx -h localhost -U postgres -p5432 -f xxxxx.sql
```
Solicitara la contraseña de PostgreSQL 12. 
asdf
