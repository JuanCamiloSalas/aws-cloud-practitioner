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

**Next Class => 44. Grupos de seguridad y puertos clásicos**

[![aws-links](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../2_IAM/README.md)
[![aws-links](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
