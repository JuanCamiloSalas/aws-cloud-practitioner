[![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../13_VPC/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![](https://img.shields.io/badge/>-FF4859?style=for-the-badge)](../14_Security_&_Compliance/README.md) -->

# Seguridad y normativa
## Modelo de responsabilidad compartida de AWS
#### Responsabilidad de AWS - Seguridad DEL Cloud

- Proteger la infraestructura (hardware, software, instalaciones y redes) que ejecuta todos los servicios de AWS
- Servicios gestionados como S3, DynamoDB, RDS, etc.

#### Responsabilidad del cliente - Seguridad DENTRO DEL Cloud
- En el caso de la instancia EC2, el cliente es responsable de la gestión del sistema operativo invitado (incluidos los parches y actualizaciones de seguridad), la configuración del firewall y la red, el IAM
- Encriptación de los datos de la aplicación
- Controles compartidos:
- Gestión de parches, gestión de la configuración, concienciación y formación

### Ejemplo para RDS
#### Responsabilidad de AWS:
- Gestionar la instancia EC2 subyacente, desactivar el acceso SSH
- Parcheo automatizado de la BD
- Parcheo automatizado del SO
- Auditar la instancia subyacente y los discos y garantizar su funcionamiento

#### Tu responsabilidad:
- Comprobar las reglas de entrada de puertos / IP / grupo de seguridad en el SG de la BD
- Creación de usuarios en la base de datos y permisos
- Crear una base de datos con o sin acceso público
- Asegúrate de que los grupos de parámetros o la BD están configurados para permitir sólo conexiones SSL
- Configuración del cifrado de la base de datos

### Ejemplo para S3
#### Responsabilidad de AWS:
- Garantizarte que obtienes almacenamiento ilimitado
- Garantizarte la encriptación
- Garantizar la separación de los datos entre diferentes clientes
- Garantizar que los empleados de AWS no puedan acceder a tus datos

#### Tu responsabilidad:
- Configuración del bucket
- Política de bucket / configuración pública
- Usuario y roles IAM
- Habilitar el cifrado