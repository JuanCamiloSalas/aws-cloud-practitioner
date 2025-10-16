[![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../12_Cloud_Monitorization/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![](https://img.shields.io/badge/>-FF4859?style=for-the-badge)]() -->

## Virtual Private Cloud (VPC)
- La VPC es algo que se debe conocer en profundidad para el AWS Certified Solutions Architect Associate y el AWS Certified SysOps Administrator

> [!TIP]
> **En el nivel AWS Certified Cloud Practitioner, se debe conocer:**
> - VPC, subredes `subnets`, puertas de enlace de Internet `internet gateways` y puertas de enlace NAT
> - Grupos de seguridad `security groups`, ACL de red `network ACL` (NACL), logs de flujo de la VPC
> - VPC Peering, VPC Endpoints
> - Site to Site VPN y Direct Connect
> - Transit Gateway
> - **Para el examen de CCP salen solo 1 ó 2 preguntassobre VPC**

### Direcciones IP en AWS
- IPv4 - Protocolo de Internet versión 4 (4.300 millones de direcciones)
    - **IPv4 pública** - puede utilizarse en Internet
    - La instancia EC2 obtiene una nueva dirección IP pública cada vez que se detiene y se inicia (por defecto)
    - **IPv4 privada** - se puede utilizar en redes privadas (LAN) como la red interna de AWS (por ejemplo, 192.168.1.1)
    - La IPv4 privada es fija para las Instancias EC2 aunque las inicies/detengas
- **IP elástica** - nos permite adjuntar una dirección IPv4 pública fija a la instancia EC2
    - **Nota: tiene un coste continuo si no se adjunta a la instancia EC2 o si se detiene la instancia EC2**
- **IPv6 - Protocolo de Internet versión 6** (3.4 x 10^38 direcciones)
    - Cada dirección IP es pública (no hay rango privado)
    - Ejemplo: 2001:db8:3333:4444:cccc:dddd:eeee:ffff

## Manual de VPC y subredes
- **VPC - Virtual Private Cloud**: red privada para desplegar nuestros recursos (recurso regional) 
- Las **subredes** nos permiten particionar tu red dentro de tu VPC (recurso de zona de disponibilidad)
- Una **subred pública** `public subnet` es una subred accesible desde Internet
- Una **subred privada** `private subnet` es una subred a la que no se puede acceder desde Internet 
- Para definir el acceso a internet y entre subredes, utilizamos las `route tables` tablas de rutas (tablas de enrutamiento).

![](./assets/vpc-and-subnets.png)

### Diagrama de VPC
![](./assets/vpc-diagram.png)

### Gateway de Internet y Gateways NAT

- Los [**Gateways de Internet**](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html) ayudan a nuestras instancias de la VPC a conectarse con Internet
- Las subredes públicas tienen una ruta hacia el gateway de Internet.
- Los [**Gateways NAT**](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html) (gestionados por AWS) y las [**Instancias NAT**](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_NAT_Instance.html) (autogestionadas) permiten que nuestras instancias en nuestros **subredes privadas** accedan a internet sin dejar de ser privadas

![](./assets/gateway-ex.jpg)

### ACL de red (NACL) y grupos de seguridad
- [**NACL (ACL de red)**](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)
    - Un firewall que controla el tráfico desde y hacia la subred
    - Puede tener reglas ALLOW y DENY
    - Se adjuntan a nivel de subred
    - Las reglas sólo incluyen direcciones IP
- [**Grupos de seguridad**](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html)
    - Un firewall que controla el tráfico hacia y desde una ENI / Instancia EC2
    - Puede tener sólo reglas ALLOW
    - Las reglas incluyen direcciones IP y otros grupos de seguridad

#### Grupo de seguridad vs ACL de red (NACL) 

[![aws-links](https://img.shields.io/badge/VPC_SECURITY_COMPARISON-orange?style=for-the-badge)](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html#VPC_Security_Comparison)

|Security group (Grupo de seguridad)|ACL de red|
|---|---|
|Opera en el nivel de la instancia|Opera en el nivel de la subred|
|Solo admite reglas de permiso|Admite reglas de permiso y de denegación|
|Es con estado: el tráfico de retorno se admite automáticamente, independientemente de las reglas|Es sin estado: las reglas deben permitir de forma explícita el tráfico de retorno|
|Evaluamos todas las normas antes de decidir si permitir el tráfico|Procesamos las reglas en orden, empezando por la regla numerada más baja, al decidir si permitir el tráfico|
|Se aplica a una instancia únicamente si alguien especifica el grupo de seguridad al lanzar la instancia, o asocia el grupo de seguridad a la instancia más adelante|Se aplica automáticamente a todas las instancias de las subredes con las que se ha asociado (por lo tanto, proporciona una capa de defensa adicional si las reglas del grupo de seguridad son demasiado permisivas)|
