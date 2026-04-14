# Inventory Management System — Spring Boot 3 / Java 21

[![CI](https://github.com/PabloByte/inventorymanagementsystem/actions/workflows/ci.yml/badge.svg)](https://github.com/PabloByte/inventorymanagementsystem/actions/workflows/ci.yml)
![Java 21](https://img.shields.io/badge/Java-21-red)
![Spring Boot 3](https://img.shields.io/badge/Spring_Boot-3.x-brightgreen)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Sistema de gestión de inventarios desarrollado con **Spring Boot 3** y **Java 21**, orientado a trazabilidad operativa, seguridad, mantenibilidad y despliegue real en infraestructura Linux.

El proyecto incluye documentación con **Swagger/OpenAPI**, observabilidad con **Actuator/Micrometer**, migraciones versionadas con **Flyway**, generación de **PDF** para órdenes y recibos, y autenticación/autorización con **Spring Security + JWT**.

---

## Demo

Aplicación desplegada en **VPS Linux (Ubuntu)** con **PostgreSQL**, migraciones con **Flyway** y actualización del proyecto a través de **GitHub**.

- **Aplicación web:** http://173.212.214.15:8080/pages/login.html
- **Swagger UI:** http://173.212.214.15.sslip.io/swagger-ui/index.html
- **Health check:** http://173.212.214.15.sslip.io/actuator/health
- **Métricas HTTP:** http://173.212.214.15.sslip.io/actuator/metrics/http.server.requests
- - **Actuator:** http://173.212.214.15.sslip.io/actuator/metrics/http.server.requests?tag=uri:/api/suppliers/showAllSuppliers&tag=method:GET

### Credenciales demo
- **Usuario demo:** demo.inventory@demo.local O  arnold2007@hotmail.com
- **Contraseña:** DemoInventory2026! O Liliana5813@

---

## Estado actual del proyecto

### Productos
- Listado de productos
- Creación y edición
- Filtro por prioridad de reposición
- Validación contra stock mínimo personalizado
- Exportación a CSV
- No se permite eliminación para preservar historial y trazabilidad

### Categorías
- Crear y actualizar categorías
- Filtrar por categoría
- Consultar productos relacionados con detalle extendido:
  - id
  - nombre
  - descripción
  - precio
  - stock
  - proveedor
  - serial
  - lote
  - estado del certificado
  - observación

### Proveedores
- Crear proveedor
- Editar proveedor
- Consultar proveedores con sus productos asociados

### Órdenes entrantes (Inbound Order)
- Crear orden con proveedor y bodega
- Estado inicial `PENDING`
- Selección de productos con detalle enriquecido para diferenciar ítems similares
- Generación de PDF con:
  - id
  - número de orden
  - proveedor
  - estado
  - bodega
  - fecha
  - código y producto
  - cantidad
  - costo unitario
  - total
  - serial
  - lote
  - dimensiones
  - peso
  - estado del certificado
  - observaciones

### Recepción de órdenes (Inbound Receipt)
- Cargar orden existente
- Comparar cantidades pedidas vs. recibidas
- Registrar nota de recepción
- Calcular cantidades pendientes
- Generar PDF del recibo
- Registrar el usuario autenticado que genera el comprobante para mantener trazabilidad real

### Cancelación de órdenes entrantes
- Cancelación sin afectar inventario
- Conservación del historial operativo

### Inventario
- **Stock** autogestionado a partir del flujo operativo
- **Inventory Ledger** autogestionado para trazabilidad de movimientos

### En progreso
- CRUD completo de bodegas
- Órdenes salientes (Outbound Order) con PDF
- Ampliación de reglas de autorización por módulo
- Más métricas y observabilidad
- Pruebas automatizadas y endurecimiento del entorno productivo

---

## Seguridad implementada

El sistema ya cuenta con una base funcional de seguridad construida con **Spring Security** y **JWT**, incluyendo:

- Autenticación basada en **JWT**
- Asignación de **roles**
- Encriptación de contraseñas con **BCrypt**
- Reglas de seguridad para proteger endpoints según el rol o nivel de acceso
- Implementación de **UserDetailsService** para carga de usuarios autenticados
- Filtro **JWTAuthenticationFilter** para el proceso de login
- Filtro **JwtValidationFilter** para validación del token en cada request protegida
- Validación de token y control de acceso en peticiones autenticadas
- Métodos de autenticación exitosa y fallida para manejar respuestas del proceso de login
- Configuración de **CORS** para permitir integración controlada con clientes
- Exclusión de atributos sensibles en respuestas JSON
- Creación de tablas de seguridad para usuarios, roles y tabla intermedia de asignación
- Integración de reglas de autorización dentro de la configuración de Spring Security

---

## Qué demuestra este proyecto

- Diseño e implementación de una **API REST** con Spring Boot
- Seguridad con **Spring Security**, **JWT**, **BCrypt** y autorización por roles
- Documentación técnica con **Swagger / OpenAPI**
- Persistencia con **Spring Data JPA**, **Hibernate** y **Flyway**
- Generación de documentos operativos en **PDF** con Apache PDFBox
- Observabilidad con **Actuator** y **Micrometer**
- Despliegue real en **VPS Ubuntu**
- Integración continua con **GitHub Actions**
- Aplicación de buenas prácticas de backend orientadas a trazabilidad, mantenibilidad y evolución progresiva

---

## Stack tecnológico

- **Java 21**
- **Spring Boot 3**
- **Spring Web**
- **Spring Data JPA**
- **Spring Security**
- **JWT**
- **PostgreSQL / MySQL**
- **Flyway**
- **MapStruct**
- **Apache PDFBox**
- **Actuator**
- **Micrometer**
- **OpenAPI / springdoc**
- **HTML, CSS y JavaScript**
- **GitHub Actions**
- **Docker**
- **Linux / VPS**

---

## Arquitectura y enfoque

El proyecto sigue una arquitectura por capas, separando responsabilidades entre:

- controladores
- servicios
- repositorios
- DTOs
- validaciones
- mapeadores
- seguridad
- generación documental

El enfoque prioriza:

- trazabilidad operativa
- separación de responsabilidades
- claridad en contratos API
- seguridad progresiva
- facilidad de mantenimiento
- despliegue reproducible

---

## Integración continua

Cada `push` y `pull request` ejecuta el pipeline de CI para validar compilación del proyecto.

Flujo actual:

- checkout del repositorio
- configuración de Java 21
- build con Maven

---

## Próximos pasos

- completar módulo de bodegas
- implementar órdenes salientes
- ampliar cobertura de pruebas
- reforzar observabilidad
- seguir endureciendo reglas de autorización
- mejorar experiencia visual del frontend

---

## Licencia

Este proyecto se distribuye bajo la licencia **MIT**.



