# Proyecto de Infraestructura de Servicios de Red

## 1. Descripción

Proyecto académico orientado a la implementación, configuración y verificación de servicios fundamentales de infraestructura de red utilizando Windows y herramientas gratuitas.

El proyecto aborda el acceso remoto, la transferencia segura de archivos, la administración de bases de datos, la comunicación TCP y la resolución de nombres de dominio.

## 2. Objetivos

- Implementar servicios de infraestructura de red.
- Configurar y verificar conexiones mediante protocolos de red.
- Comprobar la transferencia de archivos.
- Crear y administrar una base de datos relacional.
- Configurar un nombre de dominio mediante DNS dinámico.
- Documentar los procedimientos y resultados obtenidos.

## 3. Tecnologías utilizadas

| Tecnología | Función |
|---|---|
| Windows | Sistema operativo del entorno de pruebas |
| OpenSSH Server | Acceso remoto seguro |
| SFTP | Transferencia cifrada de archivos |
| MariaDB | Gestión de bases de datos |
| Telnet Client | Prueba de comunicación TCP |
| DuckDNS | Servicio de DNS dinámico |
| GitHub | Control y almacenamiento del proyecto |
| GitHub Pages | Publicación de la página web |

## 4. Servicios implementados

| Servicio | Puerto | Resultado |
|---|---:|---|
| SSH | TCP 22 | Verificado localmente |
| SFTP | TCP 22 | Transferencia comprobada |
| MariaDB | TCP 3306 | Base de datos y consultas comprobadas |
| Telnet | TCP 2323 | Prueba TCP local con servidor temporal |
| DNS | 53 TCP/UDP | Resolución de nombre comprobada mediante DuckDNS |

Nota: el puerto 2323 corresponde al servidor temporal de prueba creado con PowerShell. No representa un servidor Telnet completo.

## 5. Dominio DNS

Subdominio configurado:

**proyectodistribuida.duckdns.org**

Proveedor: DuckDNS.

Tipo: DNS dinámico (DDNS).

La resolución se comprobó utilizando `nslookup` y `Resolve-DnsName` desde Windows.

## 6. Estructura del repositorio

- `index.html`: página web de presentación.
- `README.md`: descripción general del proyecto.
- `docs/servicios.md`: explicación técnica de los servicios.
- `docs/comandos.md`: comandos de configuración y demostración.
- `docs/seguridad.md`: consideraciones de seguridad.
- `docs/evidencias.md`: relación de evidencias.
- `evidencias/README.md`: organización de capturas y pruebas.

## 7. Cómo realizar las demostraciones

1. Consultar el estado del servicio SSH.
2. Establecer una conexión SSH local.
3. Transferir y recuperar un archivo mediante SFTP.
4. Ingresar a MariaDB y consultar los registros.
5. Ejecutar la prueba TCP local mediante Telnet.
6. Consultar el dominio mediante herramientas DNS.

Los comandos completos se encuentran en `docs/comandos.md`.

## 8. Alcance y limitaciones

Las pruebas de SSH, SFTP, MariaDB y Telnet se realizaron localmente en el equipo de implementación.

El dominio DuckDNS fue registrado y su resolución fue comprobada. Esto no implica que los servicios locales estén disponibles desde Internet.

La página de presentación se publica de manera independiente mediante GitHub Pages.

No se incluyen contraseñas, tokens ni credenciales en este repositorio.

## 9. Conclusión

La implementación permitió conocer y comprobar el funcionamiento de servicios esenciales para una infraestructura de red. Se realizaron pruebas prácticas de acceso remoto, transferencia de archivos, almacenamiento de información, comunicación TCP y resolución de nombres.

La documentación permite reproducir las comprobaciones y comprender el propósito de cada servicio.

## 10. Recursos oficiales

- [OpenSSH](https://www.openssh.com/)
- [MariaDB](https://mariadb.org/)
- [DuckDNS](https://www.duckdns.org/)
- [GitHub Pages](https://pages.github.com/)
- [Documentación de GitHub Pages](https://docs.github.com/en/pages)
- https://chatgpt.com/
