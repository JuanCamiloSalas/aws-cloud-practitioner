[![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../15_Machine_Learning/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![](https://img.shields.io/badge/>-FF4859?style=for-the-badge)](../16_Account_Billing_Support/README.md) -->

# Gestión de cuentas, facturación y asistencia

## [AWS Organizations](https://aws.amazon.com/organizations)
- Servicio global
- Permite gestionar **varias cuentas de AWS**
- La cuenta principal es la master account (cuenta maestra)
- Beneficios de costes:
    - **Facturación consolidada** en todas las cuentas: método de pago único
    - Beneficios de precios por **uso agregado** (descuento por volumen para EC2, S3...)
    - **Agrupación de instancias EC2 reservadas** para un ahorro óptimo
- La API está disponible para **automatizar la creación de cuentas de AWS**
- **Restringe los privilegios de las cuentas mediante Políticas de Control de Servicios (SCP)**
 
### Estrategias multicuenta
- Crear cuentas por **departamento**, por **centro de costes**, por **dev / test / prod**, en función de las **restricciones normativas** (usando SCP), para un **mejor aislamiento de los recursos** (ej.: VPC), para tener **límites de servicio separados por cuenta**, cuenta aislada para **logs**
- Cuenta múltiple vs. Cuenta única VPC múltiple
- Utilizar normas de etiquetado para la facturación
- Activa CloudTrail en todas las cuentas, envía los logs a la cuenta S3 central
- Enviar los logs de CloudWatch a la cuenta central de logs

### Unidades Organizativas (UO) - Ejemplos

[![aws-links](https://img.shields.io/badge/AWS_MULTI_ACOUNT_BILLING_STRATEGY-orange?style=for-the-badge)](https://aws.amazon.com/answers/account-management/aws-multi-account-billing-strategy/)

![](./assets/multi-account-strategies.png)

### AWS Organization

![](./assets/aws-organizations.png)

## Políticas de Control de Servicios (SCP)

- Lista blanca o negra de acciones IAM
- Se aplican a nivel de **OU** (organizational Unit) o de **Cuenta**
- No se aplica a la Cuenta Maestra
- El SCP se aplica a todos los **usuarios y roles** de la cuenta, incluido el usuario root
- El SCP no afecta a los roles vinculados al servicio
- Los roles vinculados a servicios permiten que otros servicios de AWS se integren con las AWS Organizations y no pueden ser restringidos por SCP.
- El SCP debe tener un ALLOW explícito (no permite nada por defecto)

> *Casos de uso:*
> - Restringir el acceso a determinados servicios (por ejemplo: no se puede utilizar EMR)
> - Aplicar la normativa PCI deshabilitando explícitamente los servicios

## Jerarquía SCP
[![aws-links](https://img.shields.io/badge/scp_examples-orange?style=for-the-badge)](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_examples.html)

![](./assets/scp-hierarchy.png)

## AWS Organization – Facturación consolidada
- Cuando se activa, te proporciona:
    - **Uso combinado** - combina el uso en todas las cuentas de AWS en la Organización de AWS para **compartir los precios por volumen, las Instancias Reservadas y los descuentos de los Planes de Ahorro**
    - **Una factura** - obtener una factura para todas las cuentas de AWS en la Organización de AWS
- La cuenta de administración puede desactivar el uso compartido de los descuentos de las instancias reservadas para cualquier cuenta de la organización de AWS, incluida ella misma

![](./assets/consolidate-billing.png)

## [AWS Control Tower](https://aws.amazon.com/controltower)
- Una forma fácil de **configurar y gobernar un entorno AWS multicuenta seguro** y conforme a las mejores prácticas
- Ventajas:
    - Automatiza la configuración de tu entorno en unos pocos clics
    - Automatiza la gestión continua de las políticas
    - Detecta las infracciones de las políticas y las corrige
    - Supervisa la normativa a través de un dashboards interactivo
- La AWS Control Tower se ejecuta sobre las Organizaciones de AWS:
    - Configura automáticamente las AWS Organizations para organizar las cuentas e implementar las SCP (Políticas de Control de Servicios)

## [AWS Resource Access Manager (AWS RAM)](https://aws.amazon.com/ram)
- Comparte los recursos de AWS que poseas con otras cuentas de AWS
- Comparte con cualquier cuenta o dentro de tu organización
- ¡Evita la duplicación de recursos!
- Los recursos soportados incluyen Aurora, Subredes de VPC, Transit Gateway, Route 53, EC2 Hosts dedicados...

![](./assets/aws-ram.png)