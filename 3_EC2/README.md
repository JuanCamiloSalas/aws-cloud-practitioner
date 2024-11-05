[![aws-links](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../2_IAM/README.md)
[![aws-links](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)

# EC2: Elastic Computing Cloud

## Amazon EC2
- EC2 es una de las ofertas más populares de AWS.
- EC2 = Elastic Compute Cloud = Infraestructura como servicio (IaaS).
- Consiste principalmente en la capacidad de:
  - Alquilar máquinas virtuales (EC2).
  - Almacenar datos en unidades virtuales (EBS).
  - Distribuir la carga entre las máquinas (ELB).
  - Escalar los servicios mediante un Auto Scaling Group (ASG), también conocido en español como Grupo de Autoescalado.
- Conocer EC2 es fundamental para entender el funcionamiento del Cloud.

## Opciones de tamaño y configuración de EC2
- **Sistema operativo (OS)**: Linux, Windows o Mac OS
- **Cuánta potencia de cálculo y núcleos (CPU)**
- **Cuánta memoria de acceso aleatorio (RAM)**
- **Cuánto espacio de almacenamiento**:
  - Conectado a la red (**EBS y EFS**)
  - Hardware (**EC2 Instance Store**)
- **Tarjeta de red**: velocidad de la tarjeta, dirección IP pública
- **Reglas de firewall**: grupo de seguridad
- **Script de arranque** (configurar en el primer lanzamiento): Datos de usuario de EC2

## Datos del usuario de EC2
- Es posible arrancar nuestras instancias utilizando **un script de datos de usuario** de EC2.
- **Bootstrapping** significa lanzar comandos cuando una máquina se inicia.
- Ese script sólo **se ejecuta una vez** en el **primer arranque de la instancia**.
- Los datos de usuario de EC2 se utilizan para automatizar tareas de arranque como:
  - Instalar actualizaciones
  - Instalación de software
  - Descarga de archivos comunes de Internet
  - Cualquier cosa que se te ocurra
- El script de datos de usuario de EC2 se ejecuta con el usuario root.

## Tipos de instancias de EC2
[![aws-links](https://img.shields.io/badge/intance_types-orange?style=for-the-badge)](https://aws.amazon.com/ec2/instance-types/)
[![aws-links](https://img.shields.io/badge/intances_vantage-orange?style=for-the-badge)](https://instances.vantage.sh/)
- Se pueden utilizar diferentes tipos de instancias EC2 optimizadas para diferentes casos de uso.
- AWS tiene la siguiente convención de nombres:
  
  **m5.2xlarge**

  - **m**: clase de instancia
  - **5**: generación (AWS los mejora con el tiempo)
  - **2xlarge**: tamaño dentro de la clase de instancia

### Instancias de Propósito general - General Purpose
- Excelente para una diversidad de cargas de trabajo, como servidores web o repositorios de código.
- Equilibrio entre:
  - Computación
  - Memoria
  - Red

### Instancias de Computación optimizada - Compute Optimized
- Ideal para tareas de cálculo intensivo que requieren procesadores de alto rendimiento:
  - Cargas de trabajo de procesamiento por lotes
  - Transcodificación de medios
  - Servidores web de alto rendimiento
  - Computación de alto rendimiento (HPC)
  - Modelado científico y aprendizaje automático
  - Servidores dedicados a juegos
 
### Instancias de Memoria optimizada - Memory Optimized
- Rápido rendimiento para cargas de trabajo que procesan grandes conjuntos de datos en memoria.
- Casos de uso:
  - Alto rendimiento, bases de datos relacionales/no relacionales
  - Almacenes de caché distribuidos a escala web
  - Bases de datos en memoria optimizadas para BI (business intelligence)
  - Aplicaciones que realizan el procesamiento en tiempo real de grandes datos no estructurados

### Instancias de Almacenamiento optimizado - Storage Optimized
- Ideal para tareas de almacenamiento intensivo que requieran un acceso alto y secuencial de lectura y escritura a grandes conjuntos de datos en el almacenamiento local.
- Casos de uso:
  - Sistemas de procesamiento de transacciones en línea (OLTP) de alta frecuencia
  - Bases de datos relacionales y NoSQL
  - Caché para bases de datos en memoria (por ejemplo, Redis)
  - Aplicaciones de almacenamiento de datos
  - Sistemas de archivos distribuidos

## Introducción a los grupos de seguridad
- Los grupos de seguridad son la base de la seguridad de la red en AWS.
- Controlan cómo se permite el tráfico dentro o fuera de nuestras Instancias EC2.

  ![Security Group](path/to/image.png) <!--Subir imagen -->

- Los grupos de seguridad sólo contienen reglas de **permiso**.
- Las reglas de los grupos de seguridad pueden hacer referencia por IP o por grupo de seguridad.

### Grupos de seguridad - Inmersión más profunda
- Los grupos de seguridad actúan como un "firewall" en las instancias de EC2.
- Regulan:
  - El acceso a los puertos
  - Rangos de IP autorizados - IPv4 e IPv6
  - Control de la red de entrada (de otros a la instancia)
  - Control de la red saliente (desde la instancia hacia otra)

#### Ejemplo de grupo de seguridad: tráfinco entrante y saliente
![Security Group](path/to/image.png) <!--Subir imagen -->

#### Ejemplo de grupo de seguridad: tráfico entre más grupos
![Security Group](path/to/image.png) <!--Subir imagen -->

### Grupos de seguridad - Es bueno saber
- Puede adjuntarse a múltiples instancias.
- Bloqueado a una combinación de región / VPC.
- Vive "fuera" del EC2 - si el tráfico está bloqueado, la instancia EC2 no lo verá.
- **Es bueno mantener un grupo de seguridad separado para el acceso SSH.**
- Si tu aplicación no es accesible (tiempo de espera), entonces es un problema de grupo de seguridad.
- Si tu aplicación da un error de "conexión rechazada", entonces es un error de la aplicación o no se ha lanzado.
- Todo el tráfico de entrada está **bloqueado** por defecto.
- Todo el tráfico de salida está **autorizado** por defecto.

## Puertos clásicos que hay que conocer
- **22 = SSH (Secure Shell)** - iniciar sesión en una instancia de Linux
- **21 = FTP (File Transfer Protocol)** - subir archivos a un archivo compartido
- **22 = SFTP (Secure File Transfer Protocol)** - subir archivos usando SSH
- **80 = HTTP** - acceso a sitios web no seguros
- **443 = HTTPS** - acceso a sitios web seguros
- **3389 = RDP (Remote Desktop Protocol)** - iniciar sesión en una instancia de Windows

**Next Class => 45. Grupos de seguridad - Práctica**

[![aws-links](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../2_IAM/README.md)
[![aws-links](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
