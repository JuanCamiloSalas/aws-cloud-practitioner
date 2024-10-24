[![aws-links](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../1.%20Cloud%20Computing/README.md)
[![aws-links](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
[![aws-links](https://img.shields.io/badge/->_-FF4859?style=for-the-badge)](../3)

# IAM: Identity & Access Management
## Usuarios y Grupos

- **IAM** = Identity and Access Management, servicio **global**.
- **Cuenta root / raíz** creada por defecto, no debe ser utilizada ni compartida.
- Los **usuarios** son personas dentro de tu organización, y pueden ser agrupados.
- Los **grupos** solo contienen usuarios, no otros grupos.
- Los usuarios no tienen que pertenecer a un grupo, y el usuario puede pertenecer a varios grupos.

## Permisos
A los **usuarios o grupos** se les pueden asignar documentos JSON llamados **políticas**.
Ejemplo de una política de IAM:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "ec2:Describe*",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "elasticloadbalancing:Describe*",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "cloudwatch:ListMetrics",
        "cloudwatch:GetMetricStatistics",
        "cloudwatch:Describe*"
      ],
      "Resource": "*"
    }
  ]
}
```

> [!WARNING]
> Nunca usar el usuario root para hacer operaciones

> [!IMPORTANT]
> Los usarios pueden tener permisos de tres maneras:
> 1. Agregando el usuario a un grupo
> 2. Copiando permisos
> 3. Adjuntando políticas directamente

> [!TIP]
> En IAM podemos crear un alias de cuentas para la mejor gestión de nuestras cuentas de AWS

**....Siguiente clase: 22**

[![aws-links](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../1.%20Cloud%20Computing/README.md)
[![aws-links](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
[![aws-links](https://img.shields.io/badge/->_-FF4859?style=for-the-badge)](../3)
