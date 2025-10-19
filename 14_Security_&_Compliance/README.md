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

## ¿Qué es un ataque DDoS*?
*Distributed Denial-of-Service

Un **ataque DDoS (Distributed Denial of Service)** ocurre cuando **muchos equipos distribuidos (a menudo infectados o controlados por un atacante)** envían **grandes volúmenes de tráfico o peticiones** a un servidor, aplicación o red, con el objetivo de **agotarle los recursos** (CPU, memoria o ancho de banda).

Como resultado, el sistema **se vuelve muy lento o deja de responder** para los usuarios legítimos.

*Ejemplo:* miles de bots accediendo simultáneamente a una web hasta colapsarla.

Existen varios tipos, como:
- **De volumen:** saturan el ancho de banda.
- **De protocolo:** explotan debilidades en TCP/IP o HTTP.
- **De capa de aplicación:** simulan tráfico legítimo (más difíciles de detectar).

![](./assets/ddos-attack.png)

## Protección DDoS en AWS
- **AWS Shield Standard:** protege contra ataques DDOS a tu sitio web y aplicaciones, para todos los clientes sin coste adicional
- **AWS Shield Advanced:** protección DDoS premium 24/7
- **AWS WAF:** Filtra solicitudes específicas basadas en reglas
- **CloudFront y Route 53:**
    - Protección de la disponibilidad mediante una red de borde global
    - Combinado con AWS Shield, proporciona mitigación de ataques en el borde
- **Prepárate para escalar:** aprovecha AWS Auto Scaling

*Ejemplo de arquitectura de referencia para la protección DDoS*

![](./assets/ddos-prevent-ex.png)

## [AWS Shield](https://aws.amazon.com/shield/)
### AWS Shield Standard:
- Servicio gratuito que se activa para cada cliente de AWS
- Proporciona protección contra ataques como SYN/UDP Floods, ataques de reflexión y otros ataques de capa 3/capa 4

### AWS Shield Advanced:
- Servicio opcional de mitigación de DDoS (3.000 dólares al mes por organización)
- Protege contra ataques más sofisticados en `Amazon EC2`, `Elastic Load Balancing (ELB)`, `Amazon CloudFront`, `AWS Global Accelerator` y `Route 53`
- Acceso 24 horas al día, 7 días a la semana, al equipo de respuesta DDoS de AWS
(DRP)
- Protegerte contra las tarifas más altas durante los picos de uso debidos a los DDoS

## [AWS WAF – Web Application Firewall](https://aws.amazon.com/waf/)
- Protege tus aplicaciones web de las vulnerabilidades web más comunes (Capa 7)
- La* **Capa 7 es HTTP** (frente a la Capa 4 que es TCP)
- Despliega en el `Application Load Balancer`, `API Gateway`, `CloudFront`

- Define la ACL (Lista de Control de Acceso a la Web):
    - Las reglas pueden incluir **direcciones IP**, cabeceras HTTP, cuerpo HTTP o cadenas URI
    - Protege de los ataques más comunes: **inyección SQL** y **Cross-Site Scripting (XSS)**
    - Restricciones de tamaño, **geo-match (bloquear países)**
    - **Reglas basadas en la tasa** (para contar las ocurrencias de los eventos) - **para la protección DDoS**

## [AWS Network Firewall](https://aws.amazon.com/network-firewall/)
- Protege toda tu Amazon VPC
- Protección de capa 3 a capa 7
- En cualquier dirección, puedes inspeccionar
    - Tráfico de VPC a VPC
    - Saliente a Internet
    - Entrante desde Internet
    - Hacia / desde Direct Connect y VPN Site-to-Site

![](./assets/network-firewall-ex.png)

> [!IMPORTANT]
> Si hay una pregunta que trate sobre proteger nuestra VPC en general piensa instantáneamente en AWS Network Firewall

## Pruebas de penetración en el Cloud de AWS
[![aws-links](https://img.shields.io/badge/LEER_MAS-orange?style=for-the-badge)](https://aws.amazon.com/security/penetration-testing/)

- Los clientes de AWS pueden llevar a cabo evaluaciones de seguridad o pruebas de penetración en su infraestructura de AWS **sin la aprobación previa de AWS en 8 servicios**:
    - Instancias de Amazon EC2, NAT Gateways y Elastic Load Balancers
    - Amazon RDS
    - Amazon CloudFront
    - Amazon Aurora
    - Amazon API Gateway
    - Funciones AWS Lambda y Lambda Edge
    - Recursos de Amazon Lightsail
    - Entornos de Amazon Elastic Beanstalk
- La lista puede aumentar con el tiempo (no se te hará la pregunta en el examen)
- **Actividades prohibidas:**
    - Caminar por la zona DNS a través de las Zonas Alojadas de Amazon Route 53
    - Denial of Service (DoS), Distributed Denial of Service (DDoS), DoS simulado, DDoS simulado
    - Inundación de puertos
    - Inundación de protocolos
    - Inundación de solicitudes (inundación de solicitudes de inicio de sesión, inundación de solicitudes de API)
- Para cualquier otro evento simulado, contacta con aws-securitysimulated-event@amazon.com

## Cifrado de datos - Datos en reposo vs. Datos en tránsito
![](./assets/data-states.png)

- **En reposo:** datos almacenados o archivados en un dispositivo
    - En un disco duro, en una instancia RDS, en S3 Glacier Deep Archive, etc.
- **En tránsito (en movimiento):** datos que se trasladan de un lugar a otro
    - Transferencia de las instalaciones a AWS, de EC2 a DynamoDB, etc.
    - **Significa que los datos se transfieren en la red**
- Queremos cifrar los datos en ambos estados para protegerlos.
- Para ello aprovechamos las **claves de cifrado**

## [AWS KMS (Key Management Service)](https://aws.amazon.com/kms/)
- KMS = **AWS gestiona las claves de cifrado por nosotros**
- **Opción de cifrado:** (lo podemos poner o no)
    - Volúmenes EBS: cifrar volúmenes
    - Buckets S3: Encriptación de objetos en el lado del servidor
    - Base de datos Redshift: cifrado de datos
    - Base de datos RDS: cifrado de datos
    - Unidades EFS: cifrado de datos
- **Cifrado activado automáticamente:** (AWS lo pone por defecto)
    - Logs de CloudTrail
    - S3 Glacier
    - Storage Gateway

> [!IMPORTANT]
> Cada vez que escuches "encriptación" para un servicio de AWS, lo más probable es que se trate de KMS

## [CloudHSM](https://aws.amazon.com/cloudhsm/)
- KMS => AWS gestiona el software de encriptación
- CloudHSM => AWS proporciona el **hardware** de encriptación
- Hardware dedicado (HSM = Módulo de Seguridad de Hardware)
- Gestionas por completo tus propias claves de cifrado (no AWS)
- El dispositivo HSM es resistente a la manipulación, cumple la normativa FIPS 140-2 Nivel 3

![](./assets/hsm-device.png)

### Diagrama CloudHSM

![](./assets/clñoud-hsm-diagram.png)

## Tipos de Customer Master Keys: CMK
- **CMK gestionado por el cliente:**
    - Creada, gestionada y utilizada por el cliente, puede ser activada o desactivada
    - Posibilidad de política de rotación (se genera una nueva clave cada año, se conserva la antigua)
    - Posibilidad de traer tu propia clave
- **CMK gestionada por AWS:**
    - Creada, gestionada y utilizada en nombre del cliente por AWS
    - Utilizada por los servicios de AWS (aws/s3, aws/ebs, aws/redshift)
- **CMK propiedad de AWS:**
    - Colección de CMKs que un servicio de AWS posee y gestiona para utilizarlas en múltiples cuentas
    - AWS puede utilizarlas para proteger los recursos de tu cuenta (pero no puedes ver las claves)
- **Claves CloudHSM (almacén de claves personalizado):**
    - Claves generadas desde tu propio dispositivo de hardware CloudHSM
    - Las operaciones criptográficas se realizan dentro del cluster CloudHSM


## [AWS Certificate Manager (ACM)](https://aws.amazon.com/certificate-manager/)
- Te permite aprovisionar, gestionar y desplegar  fácilmente los **certificados SSL/TLS**
- Se utilizan para proporcionar encriptación en vuelo para los sitios web (HTTPS)
- Admite certificados TLS públicos y privados
- Gratuito para los certificados TLS públicos
- Renovación automática de certificados TLS
- Integraciones con (carga de certificados TLS en)
    - Elastic Load Balancers
    - Distribuciones de CloudFront
    - APIs en API Gateway

![](./assets/acm-ex.png)

## [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/)
- Servicio más nuevo, destinado a almacenar secretos
- Capacidad para forzar la **rotación de secretos** cada X días
- Automatizar la generación de secretos en la rotación (utiliza Lambda)
- Integración con Amazon RDS (MySQL, PostgreSQL, Aurora)
- Los secretos se encriptan mediante KMS
- Principalmente pensado para la integración con RDS

## [AWS Artifact](https://aws.amazon.com/artifact/) (no es realmente un servicio)
- **Portal que proporciona a los clientes acceso bajo demanda a la documentación de conformidad de AWS y a los acuerdos de AWS**

### Artifact Reports
Te permite descargar los documentos de seguridad y conformidad de AWS de auditores externos, como las certificaciones ISO de AWS, los informes del sector de las tarjetas de pago (PCI) y los informes de control de sistemas y organizaciones (SOC)

### Artifact Agreements
Te permite revisar, aceptar y hacer un seguimiento del estado de los acuerdos de AWS, como el Business Associate Addendum (BAA) o la Health Insurance Portability and Accountability Act (HIPAA) para una cuenta individual o en tu organización

- Puede utilizarse para **apoyar la auditoría interna o la normativa**

> [!IMPORTANT]
> Cada vez que salgan estas siglas y nos pidan dónde obtener esta información, reponde AWS Artifact