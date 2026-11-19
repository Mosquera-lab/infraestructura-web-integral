
# Consideraciones de seguridad

## Protección de credenciales

- No almacenar contraseñas en archivos del repositorio.
- No publicar el token de DuckDNS.
- No compartir credenciales de MariaDB.
- No subir capturas que expongan información privada.
- Utilizar contraseñas robustas para las cuentas administrativas.

## SSH y SFTP

SSH y SFTP utilizan cifrado para proteger la comunicación.

Se recomienda:
- Mantener OpenSSH actualizado.
- Utilizar autenticación segura.
- Limitar el acceso a usuarios autorizados.
- Revisar las reglas del firewall antes de habilitar conexiones externas.

## MariaDB

La base de datos se mantuvo en el entorno local.

Se recomienda:
- No exponer el puerto 3306 directamente a Internet.
- Utilizar usuarios con permisos limitados.
- Evitar utilizar la cuenta root desde aplicaciones.
- Realizar copias de seguridad.
- Proteger las credenciales.

## Telnet

Telnet no cifra la comunicación.

La prueba realizada fue exclusivamente local y no utilizó contraseñas ni datos sensibles.

No se recomienda utilizar Telnet para administrar servidores a través de redes públicas.

## DNS

El token de DuckDNS es privado y permite modificar el registro DNS.

No debe publicarse en GitHub, documentos, capturas ni presentaciones.

## Publicación web

GitHub Pages publica el contenido del sitio en Internet.

Antes de publicar, revisar los archivos para eliminar credenciales, tokens, direcciones privadas y datos personales.

## Alcance de la infraestructura

La publicación de la página web no implica que SSH, SFTP o MariaDB estén disponibles públicamente.

Los servicios se verificaron localmente y no se habilitó su exposición directa a Internet.
