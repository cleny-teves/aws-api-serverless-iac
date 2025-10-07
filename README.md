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

El proyecto se construyó siguiendo un proceso estructurado para garantizar la seguridad y funcionalidad:

1.  **Base de Datos (DynamoDB):** Se creó una tabla NoSQL llamada `crud-items` con `id` como clave de partición para almacenar los datos de la aplicación.
2.  **Permisos (IAM):** Se implementó el **principio de mínimo privilegio** mediante la creación de una política de IAM (`policy-access-to-dynamoDB`). Esta política otorga a la función Lambda únicamente los permisos CRUD necesarios (`PutItem`, `Scan`, `GetItem`, `UpdateItem`, `DeleteItem`) y solo sobre el ARN específico de la tabla `crud-items`.
3.  **Lógica de Cómputo (Lambda):** Se desarrolló una función Lambda (`crud-lambda`) en Node.js que contiene toda la lógica para procesar las peticiones del API y interactuar con DynamoDB.
4.  **Endpoint Público (API Gateway):** Se configuró una API de tipo HTTP (`crud-api`) para exponer la funcionalidad al exterior.
5.  **Integración y Ruteo:** Se crearon las rutas (`GET /items`, `GET /items/{id}`, `PUT /items`, `DELETE /items/{id}`) en API Gateway y se integraron para que cada una invoque a la misma función `crud-lambda`, que se encarga de gestionar la lógica correspondiente a cada petición.

## ✅ Pruebas y Verificación

La API fue probada exitosamente utilizando Postman para verificar cada una de las operaciones CRUD. Los datos enviados a través del endpoint `PUT /items` se validaron correctamente en la tabla de DynamoDB, y las operaciones de lectura y borrado funcionaron como se esperaba.
