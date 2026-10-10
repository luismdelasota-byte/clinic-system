# Clinic System — SaaS de Gestión Clínica

Sistema web de gestión de citas médicas diseñado como un producto **SaaS multiempresa (Software as a Service)**, adaptable a clínicas de distintas especialidades, como odontología, psicología, podología y medicina general.

El proyecto busca implementar una arquitectura modular y por capas, con separación de responsabilidades, seguridad y aislamiento de datos entre empresas.

Además, se desarrollará progresivamente como un proyecto Full Stack y DevOps, incorporando automatización, contenedores, integración continua y despliegue en la nube.

---

## Objetivos del proyecto

- Gestionar pacientes, doctores y citas médicas.
- Administrar usuarios, roles y permisos.
- Permitir que distintas clínicas utilicen el mismo sistema de forma aislada.
- Personalizar la configuración de cada empresa.
- Implementar una arquitectura modular, mantenible y escalable.
- Aplicar progresivamente prácticas de desarrollo y DevOps.

## Modelo SaaS multiempresa

Cada clínica será una empresa independiente dentro del sistema.

Las empresas podrán contar con:

- Usuarios, roles y permisos propios.
- Pacientes, doctores y citas independientes.
- Especialidades y horarios de atención configurables.
- Personalización visual mediante logotipo y colores.
- Reportes y estadísticas de gestión.

La arquitectura contempla la posibilidad de utilizar subdominios personalizados, por ejemplo:

- `clinica-dental.tusistema.com`
- `centro-psicologico.tusistema.com`

La implementación de subdominios, el aislamiento de datos y la configuración de infraestructura se realizarán en etapas posteriores.

## Roles del sistema

| Rol | Responsabilidades principales |
|---|---|
| Administrador | Configuración de la empresa, gestión de usuarios, roles y reportes. |
| Recepcionista | Registro de pacientes, gestión de citas y agenda diaria. |
| Doctor | Consulta de agenda, atención de pacientes e historial clínico autorizado. |

Los permisos y accesos se implementarán progresivamente mediante Spring Security y JWT.

---

## Tecnologías

### Backend

- Java 21
- Spring Boot
- Maven
- Spring Data JPA
- Hibernate
- PostgreSQL
- Spring Security
- JWT
- Flyway

### Frontend

- React
- TypeScript
- Vite

### Herramientas y DevOps

- Git y GitHub
- Linux
- Docker y Docker Compose
- GitHub Actions
- AWS
- Terraform
- Kubernetes

Las tecnologías se incorporarán progresivamente según las etapas del proyecto.

---

## Arquitectura del sistema

Se utilizará una arquitectura modular y por capas, evitando inicialmente la complejidad de los microservicios.

### Capas principales

- **Presentación:** interfaz web desarrollada con React y TypeScript.
- **Controladores:** recepción y validación inicial de solicitudes HTTP.
- **Servicios:** implementación de las reglas de negocio.
- **Repositorios:** acceso a datos mediante Spring Data JPA.
- **Entidades:** representación del modelo persistente.
- **DTOs y Mappers:** transferencia de datos y conversión entre objetos.
- **Seguridad:** autenticación, autorización y control de acceso por empresa.

### Módulos funcionales previstos

- Gestión de empresas y configuración.
- Usuarios, roles y permisos.
- Pacientes.
- Doctores y especialidades.
- Citas y horarios.
- Historias clínicas.
- Pagos y facturación.
- Notificaciones.
- Reportes y estadísticas.

La estructura definitiva se implementará a medida que se desarrollen los módulos.

---

## Base de datos

**Motor:** PostgreSQL  
**Base de datos local:** `clinic_db`

El modelo relacional contempla inicialmente las siguientes tablas:

| Tabla | Propósito |
|---|---|
| `companies` | Empresas o clínicas registradas en el SaaS. |
| `roles` | Roles disponibles en el sistema. |
| `users` | Cuentas de acceso y permisos por empresa. |
| `specialties` | Especialidades médicas configuradas por empresa. |
| `doctors` | Información de los profesionales médicos. |
| `patients` | Información de los pacientes. |
| `appointments` | Registro y seguimiento de citas médicas. |

En etapas posteriores se incorporarán tablas para horarios, historias clínicas, pagos, notificaciones y auditoría.

### Criterios de diseño

- Relaciones mediante claves primarias y foráneas.
- Restricciones de integridad y unicidad.
- Índices para consultas frecuentes.
- Migraciones versionadas con Flyway.
- Aislamiento de datos entre empresas.
- Uso de restricciones y validaciones para mantener la integridad del modelo.

La separación multiempresa se aplicará tanto en el diseño de la base de datos como en las reglas de autorización del backend.

---

## Configuración y variables de entorno

La aplicación utiliza variables de entorno para evitar almacenar credenciales directamente en el código fuente.

Variables previstas para la conexión con PostgreSQL:

```text
DB_HOST
DB_PORT
DB_NAME
DB_USER
DB_PASS
```

La configuración se gestionará mediante archivos YAML y perfiles de Spring Boot, diferenciando los entornos de desarrollo y producción.

Las credenciales y los secretos no deben subirse al repositorio.

---

## Estado actual del proyecto

El proyecto se encuentra en la **Etapa 1: desarrollo local de la aplicación clínica**.

### Configuración inicial

- [x] Crear el repositorio Git.
- [x] Crear el proyecto Spring Boot.
- [x] Configurar Java 21.
- [x] Configurar Maven.
- [x] Instalar y configurar PostgreSQL.
- [x] Crear la base de datos `clinic_db`.
- [x] Configurar la conexión entre Spring Boot y PostgreSQL.
- [x] Configurar variables de entorno.
- [x] Configurar los perfiles `dev` y `prod`.

### Backend y base de datos

- [ ] Definir la arquitectura modular y por capas.
- [ ] Configurar y verificar Flyway.
- [ ] Crear las migraciones iniciales.
- [ ] Implementar las entidades JPA y sus relaciones.
- [ ] Crear DTOs y Mappers.
- [ ] Implementar validaciones y manejo global de excepciones.
- [ ] Implementar autenticación JWT.
- [ ] Implementar autorización por roles.
- [ ] Implementar aislamiento de datos por empresa.
- [ ] Desarrollar el módulo de pacientes.
- [ ] Desarrollar el módulo de doctores y especialidades.
- [ ] Desarrollar el módulo de citas.
- [ ] Implementar pruebas automatizadas.

### Frontend

- [ ] Crear la aplicación React con TypeScript y Vite.
- [ ] Implementar autenticación e integración con el backend.
- [ ] Desarrollar los paneles según el rol del usuario.
- [ ] Implementar la gestión de pacientes, doctores y citas.

---

## Hoja de ruta de desarrollo y DevOps

El proyecto se desarrollará en siete etapas progresivas.

### Etapa 1 — Aplicación local

- [ ] Finalizar el backend y el modelo relacional.
- [ ] Desarrollar el frontend.
- [ ] Integrar frontend, backend y PostgreSQL.
- [ ] Implementar seguridad y pruebas.
- [ ] Verificar el funcionamiento de los módulos principales.

### Etapa 2 — Docker

- [ ] Crear el `Dockerfile` del backend.
- [ ] Crear el `Dockerfile` del frontend.
- [ ] Configurar Docker Compose.
- [ ] Ejecutar la aplicación y PostgreSQL mediante contenedores.
- [ ] Comprender redes, volúmenes y persistencia.

### Etapa 3 — Integración y entrega continuas (CI/CD)

- [ ] Configurar GitHub Actions.
- [ ] Automatizar compilación y pruebas.
- [ ] Validar los cambios mediante pipelines.
- [ ] Preparar el proceso de publicación de versiones.

### Etapa 4 — Despliegue en la nube

- [ ] Estudiar los fundamentos de AWS.
- [ ] Preparar los entornos de despliegue.
- [ ] Configurar la base de datos y los secretos.
- [ ] Desplegar la aplicación.
- [ ] Configurar dominio, HTTPS y monitoreo básico.

### Etapa 5 — Infraestructura como código

- [ ] Aprender Terraform.
- [ ] Definir infraestructura mediante código.
- [ ] Gestionar variables y estados.
- [ ] Automatizar la creación de recursos.

### Etapa 6 — Orquestación con Kubernetes

- [ ] Aprender los conceptos fundamentales de Kubernetes.
- [ ] Crear Deployments y Services.
- [ ] Configurar ConfigMaps y Secrets.
- [ ] Implementar gestión de configuración y escalado.

### Etapa 7 — Observabilidad y seguridad

- [ ] Centralizar logs.
- [ ] Implementar métricas y alertas.
- [ ] Supervisar disponibilidad y rendimiento.
- [ ] Revisar permisos, secretos y vulnerabilidades.
- [ ] Fortalecer la seguridad de la aplicación y su infraestructura.

---

## Seguridad y buenas prácticas

- No almacenar credenciales en el repositorio.
- Cifrar las contraseñas con un algoritmo adecuado, como BCrypt.
- Validar entradas y aplicar manejo centralizado de errores.
- Aplicar autorización en el backend, no solamente en el frontend.
- Impedir el acceso a información perteneciente a otras empresas.
- Restringir el acceso a historias clínicas y otros datos sensibles.
- Utilizar migraciones versionadas para modificar la base de datos.
- Incorporar pruebas automatizadas y controles en CI/CD.

---

## Objetivo final

Construir una aplicación clínica funcional que pueda evolucionar hacia un producto SaaS multiempresa, utilizando tecnologías modernas de desarrollo backend y frontend, una base de datos relacional y prácticas de DevOps.

El objetivo es aprender e implementar cada componente de manera progresiva, priorizando primero una aplicación local funcional antes de avanzar hacia la contenerización, automatización y despliegue en la nube.
