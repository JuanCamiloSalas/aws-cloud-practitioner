[![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../9_Deploy_&_Infra/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![](https://img.shields.io/badge/>-FF4859?style=for-the-badge)](../10_Get_Advantage_Of_Cloud//README.md) -->

# Aprovechando la infraestrucutra global de AWS
## ¿Por qué hacer una solicitud global?
Una **aplicación global** es una aplicación desplegada en **múltiples geografías**, en AWS pueden ser **regiones** y/o **edge locations**

1. **Disminución de la latencia**
    - La latencia es el tiempo que tarda un paquete de red en llegar a un servidor
    - Un paquete de Asia tarda en llegar a Estados Unidos
    - Implementa tus aplicaciones más cerca de tus usuarios para disminuir la latencia y mejorar la experiencia
2. **Recuperación de desastres (Disaster Recovery - DR)**
    - Si una región de AWS se cae (terremoto, tormentas, corte de energía, política)...
    - Puedes conmutar por error a otra región y que tu aplicación siga funcionando
    - Un plan de RD es importante para aumentar la disponibilidad de tu aplicación
3. **Protección contra ataques** la infraestructura global distribuida es más difícil de atacar

## [Infraestructura global de AWS](https://aws.amazon.com/es/about-aws/global-infrastructure/regions_az/)
- **Regiones** para desplegar aplicaciones e infraestructura
- **Zonas de disponibilidad** formadas por múltiples centros de datos
- **Edge Locations** *(puntos de presencia)* para la entrega de contenidos lo más cerca posible de los usuarios

## Aplicaciones globales en AWS
- **DNS global: Route 53**
    - Ideal para encaminar a los usuarios al despliegue más cercano con la menor latencia
    - Excelente para las estrategias de recuperación de desastres
- **Red global de entrega de contenidos (CDN): CloudFront**
    - Replica parte de una aplicación a las ubicaciones edge de AWS - disminuye la latencia
    - Almacena las solicitudes comunes - mejora la experiencia del usuario y disminuye la latencia
- **S3 Transfer Acceleration:**
    - Acelera las cargas y descargas globales en Amazon S3
- **AWS Global Accelerator:**
    - Mejora la dispon