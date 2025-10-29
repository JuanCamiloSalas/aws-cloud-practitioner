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

