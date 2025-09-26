[![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../11_Cloud_Integrations/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![](https://img.shields.io/badge/>-FF4859?style=for-the-badge)](../10_Get_Advantage_Of_Cloud//README.md) -->

# Monitorización del Cloud

## [Amazon CloudWatch Metrics](https://aws.amazon.com/cloudwatch)
- CloudWatch proporciona métricas para todos los servicios de AWS
- La métrica es una variable a monitorizar (`CPU Utilization`, `Networking`...)
- Las métricas tienen marcas de tiempo
- Podemos crear dashboards de CloudWatch con las métricas

### Métricas importantes
- **Instancias EC2:** Utilización de la CPU, Comprobaciones de estado, Red
(no RAM)
    - Métricas por defecto cada 5 minutos
    - Opción de monitorización detallada ($$$): métricas cada 1 minuto
- **Volúmenes EBS:** Lecturas/escrituras de disco
- **Buckets S3:** BucketSizeBytes, NumberOfObjects, AllRequests
- **Facturación:** Cargo total estimado (sólo en us-east-1)
- **Límites de servicio:** cuánto has estado utilizando una API de servicio
- **Métricas personalizadas:** introduce tus propias métricas

## Amazon CloudWatch Alarms
- Las alarmas se utilizan para activar las notificaciones de cualquier métrica
- Acciones de las alarmas...
    - **Autoescalado:** aumentar o disminuir el número de instancias EC2 "deseadas
    - **Acciones de EC2:** detener, terminar, reiniciar o **recuperar una instancia de EC2**
    - **Notificaciones SNS:** enviar una notificación a un tema SNS
- Varias opciones (muestreo, porcentaje %, máximo, mínimo, etc...)
- Puedes elegir el periodo sobre el que evaluar una alarma
- Ejemplo: crear una **alarma de facturación** en la métrica de facturación de CloudWatch
- Estados de la alarma:
    - OK
    - INSUFFICIENT_DATA
    - ALARM