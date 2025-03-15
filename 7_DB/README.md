[![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../6_S3/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![](https://img.shields.io/badge/>-FF4859?style=for-the-badge)](../8) -->

# Bases de Datos
[![aws-links](https://img.shields.io/badge/Documentación-orange?style=for-the-badge)]()

## Introducción a las bases de datos

- El almacenamiento de datos en disco (EFS, EBS, EC2 Instance Store, S3) puede tener sus límites.
- A veces, quieres almacenar datos en una base de datos...
  - Puedes **estructurar** los datos.
  - Construyes **índices** para **consultar / buscar** eficientemente en los datos.
  - Defines **relaciones** entre tus **conjuntos de datos**.

> Las bases de datos están **optimizadas para un propósito** y vienen con diferentes características, formas y restricciones.

### Bases de datos relacionales
- Tiene el mismo aspecto que las hojas de cálculo de Excel, ¡con enlaces entre ellas!
- Puede utilizar el lenguaje SQL para realizar consultas / búsquedas

### Bases de datos NoSQL
- NoSQL = no-SQL = bases de datos no relacionales
- Las bases de datos NoSQL están creadas para modelos de datos específicos y
tienen esquemas flexibles para construir aplicaciones modernas.
- Ventajas:
    - *Flexibilidad*: modelo de datos fácil de evolucionar
    - *Escalabilidad*: diseñadas para escalar utilizando clusters distribuidos
    - *Alto rendimiento*: optimizado para un modelo de datos específico
    - *Alta funcionalidad*: tipos optimizados para el modelo de datos

> [!NOTE]
> *Ejemplos*: Bases de datos clave-valor, documento, gráfico, en memoria, de búsqueda

## Bases de datos y responsabilidad compartida en AWS
- AWS ofrece el uso para *gestionar* diferentes bases de datos
- Los *beneficios* incluyen:
    - Aprovisionamiento rápido, alta disponibilidad, escalado vertical y horizontal
    - Copia de seguridad y restauración automatizadas, operaciones y actualizaciones
    - El parcheo del sistema operativo lo gestiona AWS
    - Monitorización, alertas

> [!NOTE]
> muchas tecnologías de bases de datos pueden ejecutarse en EC2, pero debes ocuparte tú mismo de la resiliencia, las copias de seguridad, los parches, la alta disponibilidad, la tolerancia a fallos, el escalado...
