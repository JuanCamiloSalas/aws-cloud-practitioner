[![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../7_DB/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md)
<!-- [![](https://img.shields.io/badge/>-FF4859?style=for-the-badge)](../9_Deploy_&_Infra/README.md) -->

# Despliegue y gestión de la infraestructura a escala
## [CloudFormation](https://aws.amazon.com/cloudformation)
CloudFormation es una forma declarativa de esbozar tu infraestructura de AWS, para cualquier recurso (la mayoría de ellos son compatibles).

Por ejemplo, dentro de una plantilla de CloudFormation, el usuario indica:
- Quiero un grupo de seguridad
- Quiero dos instancias EC2 que utilicen este grupo de seguridad
- Quiero un bucket S3
- Quiero un load balancer (ELB) delante de estas máquinas

Entonces CloudFormation los crea por el usuario, en el orden correcto, con la configuración exacta que este especificó

## Ventajas de AWS CloudFormation
#### Infraestructura como código
- No se crean recursos manualmente, lo que es excelente para el control
- Los cambios en la infraestructura se revisan a través del código

#### Coste
- Cada recurso dentro de la pila está etiquetado con un identificador para que se pueda ver fácilmente cuánto cuesta una pila
- Se puede estimar los costes de tus recursos utilizando la plantilla de CloudFormation
- *Estrategia de ahorro:* En Dev, se podría automatizar la eliminación de plantillas a las 5 de la tarde y volver a crearlas a las 8 de la mañana, de forma segura

#### Productividad
- Posibilidad de destruir y volver a crear una infraestructura en el Cloud sobre la marcha
- Generación automatizada de diagramas para tus plantillas
- Programación declarativa (no es necesario averiguar el orden y la orquestación)

#### No volver a inventar la rueda
- Aprovecha las plantillas existentes en la web
- Aprovecha la documentación

#### Soporta (casi) todos los recursos de AWS:
- Todo lo que veremos en este curso es compatible
- Puedes utilizar "recursos personalizados" para los recursos que no son compatibles

### Stack Designer de CloudFormation 
**Ejemplo: Stack de CloudFormation para WordPress**

- Podemos ver todos los recursos 
- Podemos ver las relaciones entre los componentes

![](./assets/cloudformation-ex.png)

<!-- [![](https://img.shields.io/badge/<-FF4859?style=for-the-badge)](../7_DB/README.md)
[![](https://img.shields.io/badge/CONTENT_TABLE-175074?style=for-the-badge)](../README.md) -->