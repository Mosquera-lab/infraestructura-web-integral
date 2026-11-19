
# Documentación técnica de los servicios

## 1. SSH

SSH (Secure Shell) es un protocolo que permite establecer conexiones remotas cifradas entre equipos.

En este proyecto se instaló OpenSSH Server en Windows. Se inició el servicio `sshd`, se configuró para inicio automático y se comprobó el puerto TCP 22.

Comandos de comprobación:

```powershell
Get-Service sshd
Get-NetTCPConnection -LocalPort 22 -State Listen
ssh "$env:USERNAME@localhost"
```

La conexión local permitió verificar el funcionamiento del servicio.

## 2. SFTP

SFTP (SSH File Transfer Protocol) permite transferir archivos mediante una conexión SSH cifrada.

Se realizó una prueba con el archivo `prueba_sftp.txt`. Se envió al servidor, se comprobó su presencia y posteriormente se descargó como `prueba_descargado.txt`.

Comandos utilizados:

```powershell
cd "$env:USERPROFILE\Desktop"
sftp "$env:USERNAME@localhost"
```

Dentro de SFTP:

```text
put prueba_sftp.txt
ls
get prueba_sftp.txt prueba_descargado.txt
exit
```

Verificación:

```powershell
Test-Path "$env:USERPROFILE\Desktop\prueba_descargado.txt"
```

El resultado obtenido fue `True`.

## 3. MariaDB

MariaDB es un sistema gestor de bases de datos relacionales.

Se instaló en Windows y se creó una base de datos llamada `proyecto_redes`, junto con una tabla llamada `usuarios`.

Se insertó información de prueba y se verificó su persistencia mediante consultas SQL.

Comandos de comprobación:

```powershell
Get-Service MariaDB
mariadb -u root -p
```

Dentro del cliente:

```sql
SHOW DATABASES;
USE proyecto_redes;
SHOW TABLES;
SELECT * FROM usuarios;
```

La consulta permitió recuperar el registro almacenado.

## 4. Telnet

Telnet es un protocolo de comunicación cliente-servidor que no cifra los datos transmitidos.

Se habilitó el cliente Telnet de Windows y se realizó una prueba TCP local utilizando un servidor temporal implementado con PowerShell.

La prueba utilizó el puerto TCP 2323 y permitió enviar un mensaje desde el cliente y recibir una respuesta.

Esta actividad demuestra conectividad TCP mediante el cliente Telnet, pero no corresponde a la instalación de un servidor Telnet completo.

## 5. DNS dinámico

DNS permite traducir nombres de dominio a direcciones IP.

Se registró el subdominio:

`proyectodistribuida.duckdns.org`

Proveedor: DuckDNS.

Se actualizó el registro mediante el mecanismo HTTPS proporcionado por DuckDNS y se comprobó la resolución desde Windows.

Comandos de verificación:

```powershell
nslookup proyectodistribuida.duckdns.org
Resolve-DnsName proyectodistribuida.duckdns.org
```

La configuración corresponde a DNS dinámico (DDNS), que permite actualizar la dirección IP asociada al nombre cuando cambia la conexión.
