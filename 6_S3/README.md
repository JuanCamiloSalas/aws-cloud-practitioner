[![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../5_ELB_&_ASG/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![](https://img.shields.io/badge/>-FF4859?style=for-the-badge)](../6_S3/README.md) -->

# S3: Simple Storage Service
[![aws-links](https://img.shields.io/badge/Documentación-orange?style=for-the-badge)](https://docs.aws.amazon.com/s3/?icmpid=docs_homepage_featuredsvcs)

## Introducción de la sección
- Amazon S3 es uno de los principales bloques de construcción de AWS
- Se anuncia como almacenamiento de "escala infinita".
- Muchos sitios web utilizan Amazon S3 como columna vertebral
- Muchos servicios de AWS utilizan Amazon S3 como una integración también
- Tendremos una aproximación paso a paso a S3
- El examen CCP requiere un conocimiento "más profundo" sobre S3

## S3 Casos de uso 
- Copia de seguridad y almacenamiento
- Recuperación de desastres
- Almacenamiento en el Cloud híbrido
- Alojamiento de aplicaciones
- Alojamiento de medios
- Data Lakes y análisis de big data
- Entrega de software
- Sitio web estático

## S3 - Buckets
- Amazon S3 permite almacenar objetos (archivos) en "buckets" (directorios)
- Los buckets deben tener un **nombre único global** (en todas las regiones y todas las cuentas)
- Los buckets se definen a **nivel de región**
- S3 parece un servicio global, pero los buckets se crean en una región

### Convención de nombres
- Sin mayúsculas, sin guión bajo
- De 3 a 63 caracteres
- No es una IP
- Debe empezar por letra minúscula o número
- NO debe empezar por el prefijo **xn--**
- NO debe terminar con el sufijo **-s3alias**

## Objetos
- Los objetos (archivos) tienen una clave
- La *clave* es la ruta **COMPLETA**:
  - `s3://mi-bucket/mi-archivo.txt`
  - `s3://mi-bucket/mi_carpeta1/otra_carpeta/mi-archivo.txt`
- La clave se compone de prefijo + nombre del objeto
  - `s3://mi-bucket/mi_carpeta1/otra_carpeta/mi-archivo.txt`
- No existe el concepto de "directorios" dentro de los buckets (aunque la interfaz de usuario te hará pensar lo contrario)

### Objetos: valores y contenido
Los valores de los objetos son el contenido del cuerpo:
- Peso  
  - Máx. Tamaño del objeto es 5TB (5000GB)
  - Si se sube más de 5GB, se debe utilizar "subida multiparte"
- Metadatos (lista de pares clave / valor de texto - metadatos del sistema o del usuario)
- Etiquetas (par clave / valor - hasta 10) - útil para la seguridad / ciclo de vida
- ID de versión (si está activado el versionado)

## Seguridad S3
#### Basada en el usuario
- **Políticas IAM:** qué llamadas a la API deben permitirse a un usuario concreto desde IAM

#### Basada en recursos
- **Políticas de bucket:** reglas para todo el bucket desde la consola de S3 - permite cuentas cruzadas
- **Lista de control de acceso a objetos (ACL):** nivel de detalle profundo (puede desactivarse)
- **Lista de control de acceso a bucket (ACL):** menos común (puede desactivarse)

#### Cifrado
Cifra objetos en Amazon S3 utilizando claves de cifrado

> [!NOTE]
> Un usuario IAM puede acceder a un objeto S3 si
> - Los permisos IAM del usuario LO PERMITEN **`OR`** la política de recursos LO PERMITE
> - **`AND`** no hay una DENEGACIÓN explícita

## Políticas de bucket S3
#### Políticas basadas en JSON 
- *Resource*: buckets y objetos 
- *Effect*: permitir (Allow) o denegar (Deny) 
- *Action*: conjunto de API a permitir o denegar 
- *Principal*: la cuenta o usuario al que aplicar la política

``` json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": [
        "s3:GetObject"
      ],
      "Resource": [
        "arn:aws:s3:::examplebucket/*"
      ]
    }
  ]
}
```
#### Utilizar una política de bucket S3 para: 
- Conceder acceso público al bucket 
- Forzar que los objetos se cifren al subirlos 
- Conceder acceso a otra cuenta (cuenta cruzada)

### Ejemplo: Acceso público - Política de uso de bucket
![](./assets/s3-policies-example-1.png)

### Ejemplo: Acceso del usuario al S3 - Permisos IAM
![](./assets/s3-policies-example-2.png)

### Ejemplo: Acceso de la instancia EC2 - Utilizar roles IAM 
![](./assets/s3-policies-example-3.png)

### Avanzado: Acceso entre cuentas - Uso de la política de bucket
![](./assets/s3-policies-example-4.png)

> [!CAUTION]
> **Configuración del bucket para bloquear el acceso público**
> Estos ajustes se crearon para **evitar la filtración de datos** de la empresa
> Si se sabe que el bucket no debe ser nunca público, es mejor dejarlo activado
> Pueden establecerse a nivel de cuenta

## Amazon S3 - Alojamiento de sitios web estáticos
- S3 puede alojar sitios web estáticos y hacerlos accesibles en Internet
- La URL del sitio web será (dependiendo de la región)
  - `http://bucket-name.s3-website-aws-region.amazonaws.com`
  **`OR`**
  - `http://bucket-name.s3-website.aws-region.amazonaws.com`
- Si entrega un error 403 Forbidden, ¡asegúrate de que la política del bucket permite lecturas públicas!

## Amazon S3 - Versionado
- Puedes versionar tus archivos en Amazon S3
- Se activa **a nivel de bucket**
- La misma clave de sobrescritura cambiará la "versión": 1, 2, 3....
- Es una buena práctica versionar tus buckets
  - Protege contra borrados involuntarios (posibilidad de restaurar una versión)
  - Rolling fácil a la versión anterior

> [!NOTE]
> - Cualquier archivo que no esté versionado antes de activar el versionado tendrá la versión "nula".
> - Suspender el versionado no elimina las versiones anteriores