
# Comandos de configuración y demostración

Todos los comandos están destinados a ejecutarse en el equipo donde se configuraron los servicios. No se deben interpretar como comandos para acceder a servidores públicos.

## 1. SSH

Consultar el estado:

```powershell
Get-Service sshd
```

Comprobar el puerto:

```powershell
Get-NetTCPConnection -LocalPort 22 -State Listen
```

Conectarse localmente:

```powershell
ssh "$env:USERNAME@localhost"
```

Salir:

```powershell
exit
```

## 2. SFTP

Ir al escritorio:

```powershell
cd "$env:USERPROFILE\Desktop"
```

Comprobar el archivo:

```powershell
dir prueba_sftp.txt
```

Conectarse:

```powershell
sftp "$env:USERNAME@localhost"
```

Dentro de la consola SFTP:

```text
put prueba_sftp.txt
ls
get prueba_sftp.txt prueba_descargado.txt
exit
```

Comprobar la descarga:

```powershell
Test-Path "$env:USERPROFILE\Desktop\prueba_descargado.txt"
```

Resultado esperado:

```text
True
```

## 3. MariaDB

Comprobar el servicio:

```powershell
Get-Service MariaDB
```

Abrir el cliente:

```powershell
mariadb -u root -p
```

Dentro del cliente MariaDB:

```sql
SHOW DATABASES;
USE proyecto_redes;
SHOW TABLES;
SELECT * FROM usuarios;
EXIT;
```

No es necesario recrear la base de datos ni insertar nuevamente el registro durante la demostración.

## 4. Telnet

Habilitar el cliente (PowerShell como administrador):

```powershell
dism /online /Enable-Feature /FeatureName:TelnetClient
```

Comprobar el cliente:

```powershell
telnet
```

Salir:

```text
quit
```

Para realizar la prueba TCP, iniciar primero el servidor temporal en una ventana de PowerShell normal:

```powershell
$listener = [System.Net.Sockets.TcpListener]::new([System.Net.IPAddress]::Loopback, 2323)
$listener.Start()

Write-Host "Servidor de prueba iniciado en puerto 2323"
$client = $listener.AcceptTcpClient()
$stream = $client.GetStream()
$reader = New-Object System.IO.StreamReader($stream)
$writer = New-Object System.IO.StreamWriter($stream)
$writer.AutoFlush = $true

$writer.WriteLine("Conexion establecida correctamente.")
$writer.WriteLine("Escribe un mensaje. Para salir escribe: salir")

while (($line = $reader.ReadLine()) -ne $null) {
    if ($line -eq "salir") {
        $writer.WriteLine("Conexion finalizada.")
        break
    }

    Write-Host "Cliente envio: $line"
    $writer.WriteLine("Servidor recibio: $line")
}

$client.Close()
$listener.Stop()
```

En otra ventana:

```powershell
telnet localhost 2323
```

Enviar un mensaje de prueba y luego escribir `salir`.

## 5. DNS dinámico

Consultar el dominio:

```powershell
nslookup proyectodistribuida.duckdns.org
```

También:

```powershell
Resolve-DnsName proyectodistribuida.duckdns.org
```

Consultar la IP pública actual:

```powershell
Invoke-RestMethod "https://api.ipify.org"
```

La actualización del registro DuckDNS se realiza desde el mecanismo HTTPS oficial utilizando el token privado. El token no debe copiarse en este documento ni publicarse en el repositorio.

## 6. Comprobación general de puertos

SSH:

```powershell
Get-NetTCPConnection -LocalPort 22 -State Listen
```

MariaDB:

```powershell
Get-NetTCPConnection -LocalPort 3306 -State Listen
```

Nota: la disponibilidad de un puerto local no significa que sea accesible desde Internet.
