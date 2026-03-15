# Planio

**Planio** es una aplicación web colaborativa diseñada para la gestión de tareas y hábitos dentro de equipos o salas de trabajo. El sistema permite a los usuarios crear tableros compartidos donde pueden organizar tareas en diferentes estados (Backlog, WIP y Done), registrar hábitos diarios y recibir actualizaciones en tiempo real cuando otros miembros realizan cambios.

La arquitectura de Planio está basada en **microservicios**, separando la lógica transaccional, el sistema de eventos en tiempo real y la interfaz de usuario. 

## Objetivo del proyecto

Planio fue diseñado como una demostración práctica de:

* Arquitectura distribuida
* Comunicación entre microservicios
* Sistemas en tiempo real
* Persistencia con múltiples bases de datos
* Despliegue reproducible con contenedores

## Arquitectura del sistema

El proyecto se compone de varios servicios que se ejecutan mediante **Docker Compose**, permitiendo levantar todo el entorno con un solo comando.

## Funcionalidades principales

* Crear o unirse a salas de trabajo
* Gestionar tareas en un tablero tipo Kanban
* Asignar tareas a miembros
* Registrar hábitos diarios
* Visualizar quién completó sus hábitos
* Recibir actualizaciones en tiempo real
* Auditoría de eventos del sistema

### Componentes principales

**Infraestructura / Arquitectura**

Responsable de la configuración y funcionamiento general del sistema.

* Configuración de `docker-compose`
* Manejo de variables de entorno
* Configuración de bases de datos
* Healthchecks y volúmenes
* Documentación y diagrama de arquitectura

**Service A – Core API**

* API REST principal del sistema
* Gestión de salas, usuarios y tareas
* Persistencia en PostgreSQL
* Publicación de eventos hacia Service B

**Service A – Hábitos**

* Módulo para seguimiento de hábitos diarios
* Registro de hábitos y checks diarios
* Visualización del progreso por miembro
* Emisión de eventos cuando se completa un hábito

**Service B – Realtime + Auditoría**

* Servidor WebSocket para actualizaciones en tiempo real
* Recepción de eventos desde Service A
* Persistencia de eventos en MongoDB
* Emisión de notificaciones a clientes conectados

**Front-end Web**

* Interfaz web para interactuar con el sistema
* Tablero colaborativo de tareas
* Panel de hábitos diarios
* Notificaciones en tiempo real
* Integración con REST API y WebSockets

## Tecnologías utilizadas

* Docker / Docker Compose
* PostgreSQL
* MongoDB
* WebSockets
* REST APIs


