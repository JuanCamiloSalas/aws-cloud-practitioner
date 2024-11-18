[![aws-links](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../3_EC2/README.md)
[![aws-links](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![aws-links](https://img.shields.io/badge/>-FF4859?style=for-the-badge)](../xxx/README.md) -->

# EBS: Elastic Block Store
[![aws-links](https://img.shields.io/badge/Documentación-orange?style=for-the-badge)](https://docs.aws.amazon.com/es_es/ebs/latest/userguide/what-is-ebs.html)

## ¿Qué es un volumen EBS?
- Un volumen EBS (Elastic Block Store) es una unidad de red que puede
adjuntar a las instancias mientras se ejecutan
- Permite que las instancias persistan los datos, incluso después de su
finalización
- Sólo pueden montarse en una instancia a la vez (a nivel de CCP)

> [!CAUTION]
> Para términos de la cetificación Cloud Practitioner se omite el tema de la función **EBS Multi-Attach** que es propia de los volúmenes io1 e io2.

- Están vinculados a una zona de disponibilidad específica
- Analogía: Piensa en ellos como una "memoria USB de red"
- Nivel gratuito: 30 GB de almacenamiento EBS gratuito de tipo Propósito
General (SSD) o Magnético al mes
- Es una unidad de red (es decir, no es una unidad física)
    - Utiliza la red para comunicar la instancia, lo que significa que puede haber un poco de latencia
    - Se puede separar de una instancia EC2 y conectarla a otra rápidamente
- Está bloqueado en una Zona de Disponibilidad (AZ)
    - Un volumen EBS en us-east-1a no puede adjuntarse a us-east-1b
    - Para trasladar un volumen, primero hay que hacer un snapshot del mismo
- Tener una capacidad provisionada (tamaño en GBs, e IOPS)
    - Se facturará toda la capacidad aprovisionada
    - Puede aumentar la capacidad de la unidad con el tiempo

![ebs-example](./assets/ebs-example.png)

## EBS - Atributo "Borrar al terminar”
- Controla el comportamiento de EBS cuando una instancia EC2 termina
    - Por defecto, se elimina el volumen EBS root / raíz (atributo habilitado)
    - Por defecto, cualquier otro volumen EBS adjunto no se elimina (atributo deshabilitado)
- Esto puede ser controlado por la consola de AWS / AWS CLI
- Caso de uso: preservar el volumen root / raíz cuando se termina la instancias

## Snapshot / Instantáneas de EBS
Una instantánea es una copia de seguridad incremental, lo que significa que solo se guardan los bloques del volumen que han cambiado desde la instantánea más reciente. Esto disminuye el tiempo necesario para crearlo y ahorra costos de almacenamiento, ya que no se duplican los datos.
- No es necesario separar el volumen para hacer la instantánea, pero se recomienda
- Se puede copiar las instantáneas a través de AZ o Región:

![ebs-example](./assets/ebs-snapshot.png)

### Características de los Snapshots de EBS
#### a. Archivo de Snapshots de EBS
- Mover un snapshot a un "nivel de archivo" que es un 75% más barato
- La restauración del archivo tarda entre 24 y 72 horas

![ebs-example](./assets/ebs-snapshot-archive.png)

#### b. Papelera de reciclaje para Snapshots EBS
- Configura reglas para retener los snapshots eliminados para poder recuperarlos después de un borrado accidental
- Especifica la retención (de 1 día a 1 año)

![ebs-example](./assets/ebs-snapshot-delete.png)

## AMI: Amazon Machine Image
- Las AMI son una **personalización** de una instancia EC2
    - EL usuario puede añadir su propio software, configuración, sistema operativo, monitorización...
    - Tiempo de arranque/configuración más rápido porque todo el software está preempaquetado
- Las AMI se construyen para una **región específica** (y pueden copiarse entre regiones)

Se pueden lanzar instancias EC2 desde:
- **Una AMI pública**: proporcionada por AWS
- **Una AMI propia**: creada y mantenida por el usuario
- **Una AMI de AWS Marketplace**: una AMI hecha por otra persona (y
potencialmente vendida)

### Proceso AMI (desde una instancia EC2)
- Iniciar una instancia EC2 y personalizarla
- Detener la instancia (para la integridad de los datos)
- Construir una AMI - esto también creará instantáneas de EBS
- Lanzar instancias desde otras AMIs

![create-ami-ec2](./assets/ami-ec2.png)