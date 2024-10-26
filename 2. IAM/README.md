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

> [!WARNING]
> Nunca usar el usuario root para hacer operaciones

### Los usarios pueden tener permisos de tres maneras:
1. Agregando el usuario a un grupo
2. Copiando permisos
3. Adjuntando políticas directamente

> [!TIP]
> En IAM podemos crear un alias de cuentas para la mejor gestión de nuestras cuentas de AWS

## Estructura de las política de IAM:
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
### Constan de:
- **Version**: versión del lenguaje de la política, siempre incluye `"2012-10-17"`
- **Id**: un identificador para la política (opcional)
- **Statement**: una o más declaraciones individuales (obligatorio)

### Las declaraciones constan de:
- **Sid**: un identificador para la declaración (opcional)
- **Effect**: si la sentencia permite o deniega el acceso (Permitir, Denegar)
- **Principal**: cuenta/usuario/rol al que se aplica esta política
- **Action**: lista de acciones que esta política permite o deniega
- **Resource**: lista de recursos a los que se aplican las acciones
- **Condition**: condiciones para cuando esta política está en efecto (opcional)

## Política de contraseñas

- **Contraseñas fuertes** = mayor seguridad para tu cuenta
- En AWS, puedes configurar una política de contraseñas:
  - Establecer una longitud mínima de contraseña
  - Requerir tipos de caracteres específicos:
    - incluyendo letras mayúsculas
    - letras minúsculas
    - números
    - caracteres no alfanuméricos
  - Permitir a todos los usuarios de IAM cambiar sus propias contraseñas
  - Requerir a los usuarios que cambien su contraseña después de un tiempo (caducidad de la contraseña)
  - Impedir la reutilización de la contraseña

## Multi Factor Authentication - MFA
Autenticación de dos factores, las cuentas deben protegerse con contraseña y un MFA. 

### Dispositivos de MFA:
  - Aplicación del autenticador
  - Llave de seguridad
  - Token de contraseña temporal de un solo uso (TOTP) de hardware

Clave de seguridad del segundo factor universal U2F

## ¿Cómo pueden los usuarios acceder a AWS?

Para acceder a AWS, tienes tres opciones:

- **Consola de administración de AWS** (protegida por contraseña + MFA)
- **Interfaz de línea de comandos de AWS (CLI)**: protegida por claves de acceso
- **AWS Software Developer Kit (SDK)** - para el código; protegido por claves de acceso

    - Las claves de acceso se generan a través de la consola de AWS

- Los usuarios gestionan sus propias claves de acceso
- **Las claves de acceso son secretas, como una contraseña. No las compartas**

    - ID de la clave de acceso ≈= nombre de usuario
    - Clave de acceso secreta ≈= contraseña

## ¿Qué es la CLI de AWS?

- Una herramienta que permite interactuar con los servicios de AWS mediante comandos en tu shell de línea de comandos
- Acceso directo a las API públicas de los servicios de AWS
- Puedes desarrollar scripts para gestionar tus recursos
- Es de código abierto [https://github.com/aws/aws-cli](https://github.com/aws/aws-cli)
- Alternativa al uso de la consola de administración de AWS

## ¿Qué es el SDK de AWS?

- Kit de desarrollo de software de AWS (AWS SDK)
- APIs específicas para cada lenguaje (conjunto de bibliotecas)
- Permite acceder y administrar los servicios de AWS mediante programación
- Integrado en la aplicación
- Admite:
  - SDKs (JavaScript, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++)
  - SDKs para móviles (Android, iOS, ...)
  - SDKs para dispositivos IoT (Embedded C, Arduino, ...)
- Ejemplo: AWS CLI está construido sobre AWS SDK para Python

## Roles IAM para los servicios

- Algún servicio de AWS tendrá que realizar acciones en tu nombre.
- Para ello, asignaremos **permisos** a los servicios de AWS con **Roles IAM**.
- Roles comunes:
  - Roles de Instancia EC2
  - Roles de la función Lambda
  - Roles para CloudFormation

**....Siguiente clase: 28**

[![aws-links](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../1.%20Cloud%20Computing/README.md)
[![aws-links](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
[![aws-links](https://img.shields.io/badge/->_-FF4859?style=for-the-badge)](../3)
