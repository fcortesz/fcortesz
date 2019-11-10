## Crear Base de datos Espacial

*`Abrir navegador http://[ServerIP_or_domain]/pgadmin4`* </br>
Iniciar sesion con usuario y contraseña proporcionados durante instalación.
```
Servers | [name] | Databases
Objects | Create | Database
General - Database [name]
Save
Tools | Query Tools
Create Extension Postgis;
Execute/Refresh(F5)
```
