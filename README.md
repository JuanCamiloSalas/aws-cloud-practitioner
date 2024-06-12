# AWS

## 🔗 Links
[![aws-links](https://img.shields.io/badge/Links%20del%20curso-orange?style=for-the-badge)](https://blockstellart.com/aws-cloud-practitioner/)
[![aws-links](https://img.shields.io/badge/Examen%20de%20práctica-orange?style=for-the-badge)](https://d1.awsstatic.com/es_ES/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Sample-Questions.pdf)
[![aws-links](https://img.shields.io/badge/Nivel%20gratuito%20de%20AWS-orange?style=for-the-badge)](https://aws.amazon.com/es/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all)

## Qué es el Cloud Computing

### Problemas con el enfoque tradicional de las IT

- Pagar el alquiler del centro de datos
- Pagar el suministro eléctrico, la refrigeración y el mantenimiento
- Añadir y sustituir el hardware lleva tiempo
- El escalado es limitado
- Contratar un equipo 24/7 para supervisar la infraestructura
- ¿Cómo hacer frente a las catástrofes? (terremoto, apagón, incendio...)
- ¿Podemos externalizar todo esto?

### ¿Qué es el Cloud Computing?
- El Cloud Computing (Computación en la nube) es el **suministro bajo demanda** de potencia de cálculo, almacenamiento en bases de datos, aplicaciones y otros recursos informáticos.
- A través de una plataforma de servicios en el cloud con **precios de pago por uso**.
- Puedes **aprovisionar exactamente el tipo y el tamaño** de los recursos informáticos que necesitas.
- Puedes acceder a tantos recursos como necesites, **casi al instante**.
- Forma sencilla de acceder a **servidores, almacenamiento, bases de datos** y un conjunto de **servicios de aplicaciones**.
- Amazon Web Services (AWS) posee y mantiene el hardware conectado a la red necesario para estos servicios de aplicaciones, mientras que aprovisionas y utilizas lo que necesitas a través de una aplicación web.

### Los modelos de despliegue del Cloud

#### Cloud privado:
- Servicios en el cloud utilizados por una sola organización, no expuestos al público
- Control total
- Seguridad para aplicaciones sensibles
- Satisfacer necesidades empresariales específicas

<img src="https://www.channelbiz.es/wp-content/uploads/2015/09/Rackspace-684x450.jpg" alt="Logo Cloud Privado" width="200px">

#### Cloud público:
- Recursos en el cloud que son propiedad de un proveedor de servicios en el cloud y son operados por él, y que se suministran a través de Internet
- Seis ventajas de la computación en el cloud

<img src="https://scontent.fbog9-1.fna.fbcdn.net/v/t39.30808-6/352781533_691513629654207_1365767299445157464_n.png?_nc_cat=105&ccb=1-7&_nc_sid=5f2048&_nc_ohc=eDevusealwoQ7kNvgGv579u&_nc_ht=scontent.fbog9-1.fna&oh=00_AYDYgIirNUzjqcq1ztCNOh1i_EywGEw089myg8S_zmJypg&oe=666BAF3E" alt="Logo Cloud Privado" width="200px">

#### Cloud híbrido:
- Mantener algunos servidores en las instalaciones y extender algunas capacidades al cloud
- Control de los activos sensibles en tu infraestructura privada
- Flexibilidad y rentabilidad del cloud público

### Las cinco características del Cloud computing

**Autoservicio bajo demanda (on-demand):**
- Los usuarios pueden aprovisionar recursos y utilizarlos sin interacción humana del proveedor de servicios

**Amplio acceso a la red:**
- Los recursos están disponibles a través de la red, y pueden ser accedidos por diversas plataformas de clientes

**Alquiler múltiple y agrupación de recursos:**
- Varios clientes pueden compartir la misma infraestructura y aplicaciones con seguridad y privacidad
- Múltiples clientes reciben servicio desde los mismos recursos físicos

**Rápida elasticidad y escalabilidad:**
- Adquirir y disponer de recursos de forma automática y rápida cuando sea necesario
- Escala rápida y fácilmente en función de la demanda

**Servicio medido:**
- El uso se mide, los usuarios pagan correctamente por lo que han utilizado

### Seis ventajas del Cloud computing

**Cambia el gasto de capital (CAPEX) por el gasto operativo (OPEX)**
- Pagar bajo demanda: no poseer el hardware
- Reducción del coste total de propiedad (TCO) y de los gastos operativos (OPEX)

**Te beneficias de economías de escala masivas**
- Los precios se reducen ya que AWS es más eficiente debido a la gran escala

**Deja de adivinar la capacidad**
- Escala basada en el uso real medido

**Aumentar la velocidad y la agilidad**

**Deja de gastar dinero en el funcionamiento y el mantenimiento de los centros de datos**

**Se global en minutos:** aprovecha la infraestructura global de AWS

### Problemas resueltos por el Cloud

- **Flexibilidad:** Cambia los tipos de recursos cuando sea necesario.
- **Rentabilidad:** Paga por lo que utilizas.
- **Escalabilidad:** Permite acomodar mayores cargas reforzando el hardware o añadiendo nodos adicionales.
- **Elasticidad:** Capacidad de reducir y aumentar la escala cuando sea necesario.
- **Alta disponibilidad y tolerancia a los fallos:** Construye a través de los centros de datos (data centers).
- **Agilidad:** Desarrollar, testear y lanzar rápidamente aplicaciones de software.

### Tipos de Cloud Computing
#### Infraestructura como servicio (IaaS)
- Proporciona bloques de construcción para la IT en el cloud
- Proporciona redes, ordenadores y espacio de almacenamiento de datos
- Máximo nivel de flexibilidad
- Fácil paralelismo con la IT tradicional en las instalaciones
#### Plataforma como servicio (PaaS)
- Elimina la necesidad de que tu organización gestione la infraestructura
subyacente
- Se centra en el despliegue y la gestión de tus aplicaciones
#### Software como servicio (SaaS)
- Producto completo que es ejecutado y gestionado por el proveedor de servicios

![Modelos](https://www.redhat.com/rhdc/managed-files/styles/wysiwyg_full_width/private/iaas-paas-saas-diagram5.1-1638x1046.png?itok=Ul0Em30u)

|                      | En las instalaciones | Infraestructura como servicio (IaaS) | Plataforma como servicio (PaaS) | Software como servicio (SaaS) |
|----------------------|----------------------|-------------------------------------|--------------------------------|------------------------------|
![Aplicaciones](https://img.shields.io/badge/Aplicaciones-blue?style=for-the-badge) | ![Aplicaciones](https://img.shields.io/badge/Aplicaciones-blue?style=for-the-badge) | ![Aplicaciones](https://img.shields.io/badge/Aplicaciones-orange?style=for-the-badge) | ![Aplicaciones](https://img.shields.io/badge/Aplicaciones-orange?style=for-the-badge) |
![Datos](https://img.shields.io/badge/Datos-blue?style=for-the-badge) | ![Datos](https://img.shields.io/badge/Datos-blue?style=for-the-badge) | ![Datos](https://img.shields.io/badge/Datos-orange?style=for-the-badge) | ![Datos](https://img.shields.io/badge/Datos-orange?style=for-the-badge) |
![Tiempo de ejecución](https://img.shields.io/badge/Tiempo%20de%20ejecución-blue?style=for-the-badge) | ![Tiempo de ejecución](https://img.shields.io/badge/Tiempo%20de%20ejecución-orange?style=for-the-badge) | ![Tiempo de ejecución](https://img.shields.io/badge/Tiempo%20de%20ejecución-orange?style=for-the-badge) | ![Tiempo de ejecución](https://img.shields.io/badge/Tiempo%20de%20ejecución-orange?style=for-the-badge) |
![Middleware](https://img.shields.io/badge/Middleware-blue?style=for-the-badge) | ![Middleware](https://img.shields.io/badge/Middleware-orange?style=for-the-badge) | ![Middleware](https://img.shields.io/badge/Middleware-orange?style=for-the-badge) | ![Middleware](https://img.shields.io/badge/Middleware-orange?style=for-the-badge) |
![O/S](https://img.shields.io/badge/O%2FS-blue?style=for-the-badge) | ![O/S](https://img.shields.io/badge/O%2FS-orange?style=for-the-badge) | ![O/S](https://img.shields.io/badge/O%2FS-orange?style=for-the-badge) | ![O/S](https://img.shields.io/badge/O%2FS-orange?style=for-the-badge) |
![Virtualización](https://img.shields.io/badge/Virtualización-orange?style=for-the-badge) | ![Virtualización](https://img.shields.io/badge/Virtualización-orange?style=for-the-badge) | ![Virtualización](https://img.shields.io/badge/Virtualización-orange?style=for-the-badge) | ![Virtualización](https://img.shields.io/badge/Virtualización-orange?style=for-the-badge) |
![Servidores](https://img.shields.io/badge/Servidores-orange?style=for-the-badge) | ![Servidores](https://img.shields.io/badge/Servidores-orange?style=for-the-badge) | ![Servidores](https://img.shields.io/badge/Servidores-orange?style=for-the-badge) | ![Servidores](https://img.shields.io/badge/Servidores-orange?style=for-the-badge) |
![Almacenamiento](https://img.shields.io/badge/Almacenamiento-orange?style=for-the-badge) | ![Almacenamiento](https://img.shields.io/badge/Almacenamiento-orange?style=for-the-badge) | ![Almacenamiento](https://img.shields.io/badge/Almacenamiento-orange?style=for-the-badge) | ![Almacenamiento](https://img.shields.io/badge/Almacenamiento-orange?style=for-the-badge) |
![Networking](https://img.shields.io/badge/Networking-orange?style=for-the-badge) | ![Networking](https://img.shields.io/badge/Networking-orange?style=for-the-badge) | ![Networking](https://img.shields.io/badge/Networking-orange?style=for-the-badge) | ![Networking](https://img.shields.io/badge/Networking-orange?style=for-the-badge) |



### Ejemplo de tipos de Cloud Computing 
- Infraestructura como servicio: 
    - Amazon EC2 (en AWS) 
    - GCP, Azure, Rackspace, Digital Ocean, Linode 
- Plataforma como servicio: 
    - Elastic Beanstalk (en AWS) 
    - Heroku, Google App Engine (GCP), Windows Azure (Microsoft) 
- Software como servicio: 
    - Muchos servicios de AWS (por ejemplo, Rekognition para el
aprendizaje automático)
    - Google Apps (Gmail), Dropbox, Zoom

### Precios del Cloud - Visión general rápida
AWS tiene 3 fundamentos de precios, siguiendo el modelo de precios
de pago por uso
1. **Computación:** Pagar por el tiempo de computación
2. **Almacenamiento:** Paga por los datos almacenados en el Cloud
3. **Transferencia de datos FUERA del Cloud:** La transferencia de datos hacia adentro es gratuita

> [!IMPORTANT]
> Resuelve el costoso problema de las IT tradicionales

## Infraestructura global de AWS 
[![aws-links](https://img.shields.io/badge/aws%20Infraestructura-orange?style=for-the-badge)](https://aws.amazon.com/es/about-aws/global-infrastructure)
- AWS Regions 
- Regiones de AWS 

- AWS Availability Zones 
- Zonas de disponibilidad de AWS 

- AWS Data Centers 
- Centros de datos de AWS 

- AWS Edge Locations / Points of Presence 
- Puntos de presencia de AWS

### Regiones de AWS
[![aws-links](https://img.shields.io/badge/aws%20regiones-orange?style=for-the-badge)](https://aws.amazon.com/es/about-aws/global-infrastructure/regions_az/)
- AWS tiene Regiones en todo el mundo 
- Los nombres pueden ser us-east-1, eu-west-3... 
- Una región es un grupo de centros de datos 
- La mayoría de los servicios de AWS son de ámbito regional

### ¿Cómo elegir una región de AWS?
- **Cumplimiento de los requisitos legales y de gobernanza de datos:** los datos nunca salen de una región sin tu permiso explícito.
- **Proximidad a los clientes:** latencia reducida.
- **Servicios disponibles en una región:** los nuevos servicios y las nuevas funciones no están disponibles en todas las regiones.
- **Precios:** los precios varían de una región a otra y son transparentes en la página de precios del servicio.

### Zonas de disponibilidad de AWS
- Cada región tiene muchas zonas de disponibilidad (normalmente 3, el mínimo es 3, el máximo es 6). Ejemplo:
    - ap-southeast-2a
    - ap-southeast-2b
    - ap-southeast-2c
- Cada zona de disponibilidad (AZ) es uno o varios centros de datos discretos con alimentación, red y conectividad redundantes.
- Están separadas unas de otras, de modo que están aisladas de las catástrofes.
- Están conectadas con redes de alto ancho de banda y latencia ultrabaja.

![AWS-region-az](https://disaster-recovery.workshop.aws/images/aws-region2.png)

### Puntos de presencia de AWS (Edge Locations)
- Amazon tiene +450 puntos de presencia (+10 cachés regionales) en +90 ciudades de +40 países.
- El contenido se entrega a los usuarios finales con menor latencia.

![AWS edge locations](https://docs.aws.amazon.com/es_es/whitepapers/latest/aws-fault-isolation-boundaries/images/amazon-cloudfront.png)

### Tour por la consola de AWS
[![aws-links](https://img.shields.io/badge/Servicios%20de%20AWS%20por%20región-orange?style=for-the-badge)](https://aws.amazon.com/es/about-aws/global-infrastructure/regional-product-services/)

- AWS cuenta con servicios globales:
    - Identity and Access Management (IAM)
    - Route 53 (servicio DNS)
    - CloudFront (Red de entrega de contenido)
    - WAF (Firewall de aplicaciones web)
- La mayoría de los servicios de AWS son de ámbito regional:
    - Amazon EC2 (Infraestructura como servicio)
    - Elastic Beanstalk (Plataforma como servicio)
    - Lambda (Función como servicio)
    - Rekognition (Software como servicio)

