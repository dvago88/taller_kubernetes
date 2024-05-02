# Taller de Kubernetes: Despliegue y Comunicación entre Servicios

## Objetivo:
El objetivo de este taller es aplicar los conocimientos adquiridos en el curso de Kubernetes para desplegar un sistema con dos aplicaciones comunicándose entre sí y una base de datos MySQL. Se evaluarán las habilidades en el manejo de Pods, Deployments, Services, ConfigMaps, Secrets, y otros recursos de Kubernetes. Como desafío adicional, se implementará un sistema de logging y monitoreo usando el stack EFK.

## Requisitos del Sistema:

### Aplicaciones:
- **app_a**: Una aplicación Spring Boot que necesita comunicarse con **app_b** a través de HTTP.
- **app_b**: Una aplicación Spring Boot que se conectará a una base de datos MySQL.

### Imágenes de Docker:
- **app_a**: `dvago88/service_a:latest`
- **app_b**: `dvago88/service_b:latest`
- **MySQL**: `mysql:5.7`

### Configuración de las Aplicaciones:

#### app_a:
- `spring.application.name=serviceA`
- `server.port=<especificar en el despliegue>`
- `serviceb.url=<URL del servicio B>`

#### app_b:
- `spring.application.name=serviceB`
- `server.port=<especificar en el despliegue>`
- `spring.datasource.url=<URL de la base de datos MySQL>`
- `spring.datasource.username=<usuario de la base de datos>`
- `spring.datasource.password=<contraseña de la base de datos>`
- `spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver`
- `spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect`
- `spring.jpa.hibernate.ddl-auto=update`

### curls para probar:
`curl <IP_SERVICIO_A>:<PUERTO>/hello`
`curl -d Test_String <IP_SERVICIO_A>:<PUERTO>/save_greeting`
(revisar los logs de las apps para comprobar que no haya errores después de correrlos)

## Tareas a Realizar:

1. **Creación del Cluster de Kubernetes**:
    - Utilizar la infraestructura disponible para configurar un cluster de Kubernetes que soporte todos los componentes necesarios.

2. **Despliegue de las Aplicaciones y la Base de Datos**:
    - Implementar **app_a** y **app_b** usando Deployments, StatefulSets, o DaemonSets según lo consideren necesario.
    - Desplegar una instancia de MySQL como backend para **app_b**.
    - Configurar todos los componentes para que se comuniquen adecuadamente.

3. **Configuración y Gestión de Datos Sensibles**:
    - Utilizar ConfigMaps para manejar configuraciones que no sean sensibles.
    - Emplear Secrets para manejar información sensible como credenciales de la base de datos.

4. **Servicios y Comunicación**:
    - Crear servicios en Kubernetes que permitan la comunicación entre **app_a** y **app_b**.
    - Asegurar que **app_b** pueda comunicarse con la base de datos MySQL a través de un servicio interno.

5. **Monitoreo y Logging** (Punto Extra):
    - Instalar y configurar el stack EFK (Elasticsearch, Fluentd, y Kibana) para monitorear y almacenar logs del sistema.

## Criterios de Evaluación:
- Correcta implementación y funcionamiento de los servicios.
- Uso adecuado de ConfigMaps y Secrets.
- Comunicación efectiva entre **app_a** y **app_b**.
- Configuración adecuada del stack de monitoreo y logging (para quienes elijan realizar el desafío adicional).

## Entrega:
- Enviar los archivos pertinentes al correo daniel.vargas@cedesistemas.edu.co antes de la media noche del día 2 de mayo.

