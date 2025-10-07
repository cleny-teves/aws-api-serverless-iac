# API HTTP CRUD Serverless en AWS

Este proyecto es una implementación práctica de una arquitectura 100% serverless en AWS. El objetivo es demostrar la creación de una API CRUD (Crear, Leer, Actualizar, Borrar) completa, utilizando servicios gestionados que escalan automáticamente y siguen las mejores prácticas de seguridad.

## 🏛️ Diagrama de la Arquitectura

El flujo de la aplicación demuestra la integración nativa entre los servicios serverless de AWS:

![Diagrama de Arquitectura Serverless](arquitectura-serverless.png)

## 🛠️ Tecnologías y Servicios de AWS Utilizados

* **Amazon API Gateway:** Para crear y gestionar el endpoint de la API de tipo HTTP.
* **AWS Lambda:** Como capa de cómputo para ejecutar la lógica de negocio en Node.js.
* **Amazon DynamoDB:** Como base de datos NoSQL para la persistencia de los datos.
* **AWS IAM:** Para la gestión de permisos, asegurando una comunicación segura entre los servicios.

## 🚀 Proceso de Implementación

El proyecto se construyó siguiendo un proceso estructurado:

1.  **Base de Datos (DynamoDB):** Se creó la tabla NoSQL `crud-items`.
2.  **Permisos (IAM):** Se implementó el principio de mínimo privilegio creando una política de IAM que otorga a Lambda únicamente los permisos CRUD necesarios sobre la tabla.
3.  **Lógica de Cómputo (Lambda):** Se desarrolló la función `crud-lambda` en Node.js que contiene toda la lógica de negocio.
4.  **Endpoint Público (API Gateway):** Se configuró una API de tipo HTTP (`crud-api`) con sus respectivas rutas (`/items`, `/items/{id}`).
5.  **Integración y Ruteo:** Se conectaron las rutas del API Gateway para que cada una invoque a la función `crud-lambda`.

## ✅ Pruebas y Verificación

La API fue probada exitosamente utilizando Postman para verificar cada una de las operaciones CRUD.
