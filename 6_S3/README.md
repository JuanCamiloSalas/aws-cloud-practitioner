[![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../5_ELB_&_ASG/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![](https://img.shields.io/badge/>-FF4859?style=for-the-badge)](../6_S3/README.md) -->

# S3: Simple Storage Service

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
  - Max. Tamaño del objeto es 5TB (5000GB)
  - Si subes más de 5GB, debes utilizar "subida multiparte"
- Metadatos (lista de pares clave / valor de texto - metadatos del sistema o del usuario)
- Etiquetas (par clave / valor - hasta 10) - útil para la seguridad / ciclo de vida
- ID de versión (si está activado el versionado)
