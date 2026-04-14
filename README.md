# Inventory Management System — Spring Boot 3 (Java 21)

[![CI](https://github.com/PabloByte/inventorymanagementsystem/actions/workflows/ci.yml/badge.svg)]
[(https://github.com/PabloByte/inventorymanagementsystem/actions/workflows/ci.yml)]
![Java 21](https://img.shields.io/badge/Java-21-red)
![Spring Boot 3](https://img.shields.io/badge/Spring_Boot-3.x-brightgreen)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

API de gestión de inventarios con **Swagger** y **Actuator**, migraciones con **Flyway** y generación de **PDF** para órdenes/recibos.

> **Nota demo (plan gratis):** el primer request puede demorar por *cold start*. Verifique estado en **/actuator/health** (`UP`).

## 🚀 Demo
Desplegada en vps Hostinger, con Base de datos Postgre, migraciones flyway.
- **API base:** http://173.212.214.15:8080/pages/login.html

- User : arnold2007@hotmail.com
- PassCode :  Liliana5813@
- **Swagger:** http://173.212.214.15.sslip.io/swagger-ui/index.html
- **Health:** http://173.212.214.15.sslip.io/actuator/health
- **Micrometer:** http://173.212.214.15.sslip.io/actuator/metrics/http.server.requests
- **Actuator:** http://173.212.214.15.sslip.io/actuator/metrics/http.server.requests?tag=uri:/api/suppliers/showAllSuppliers&tag=method:GET  


---

## 📌 Estado actual 
- **PRODUCTOS**
  - Filtro por prioridad para reposición
  - Pedido menor a stock personalizado
  - Exportar CSV
  - Listar / Crear / Editar  
  - **No se implementa borrar** (para preservar historial)

- **CATEGORÍA**
  - Filtrar por categoría con detalle de productos (id, nombre, descripción, precio, stock, proveedor, serial, lote, estadoCertificado, observación)
  - Crear / Actualizar  
  - **No eliminar** (no afectar inventario)

- **ÓRDENES ENTRANTES (InboundOrder)**
  - Crear orden (proveedor, bodega, estado inicial `PENDING`)
  - Selección de productos con **detalle enriquecido** (nombres similares, atributos diferenciadores)
  - **PDF**: id, número de orden, proveedor, estado, bodega, fecha, código/producto, cantidad, costo unitario, total, serial, lote, dimensiones, peso, estadoCertificado, observaciones

- **RECIBIR ORDEN ENTRANTE (InboundReceipt)**
  - Cargar orden, comparar pedido vs recibido
  - Nota de recepción
  - Calcula **pendientes**
  - **PDF** de recibo

- **CANCELAR ORDEN ENTRANTE**
  - Cancela sin afectar inventario

- **SUPPLIER**
  - Crear proveedor
  - -editar proveedor
  - ver proveedores con productos

- **STOCK**: autogestionado  
- **INVENTORY LEDGER**: autogestionado

- **WAREHOUSE**
  - **Pendiente** CRUD completo

- **OUTBOUND ORDER**
  - **Pendiente** CRUD + PDF (cliente/destino, entre bodegas)

- **SEGURIDAD**
  - **En implementación:** Spring Security (JWT, rol “encargado”)

--- SE ESTA IMPLEMENTANDO ACTUALMENTE POOL DE CONEXIONES Y SPRING SECURITY. A TRAVES DE SLICES - WALKING SKELETON.

## 🧠 Qué demuestra este proyecto
- Diseño de **API REST** documentada con **Swagger/OpenAPI**
- Observabilidad mínima: **Actuator** (`/health`) 
- Persistencia con **JPA/Hibernate** + **Flyway**
- Generación de **PDF** (Apache PDFBox) para flujos operativos
- Despliegue de aplicacion en VPS hostinger, ambiente UBUNTU,  Update a traves de GitHut, CI-CD/ Manejo de Java Core.
- **CI** con GitHub Actions (build en cada push/PR) (actualizado por foto, debido a desarrollo privado)

- 

---

## 🧱 Stack
Java 21 • Spring Boot 3 • Spring Web • Spring Data JPA • PostgreSQL/MySQL • Flyway • MapStruct • Apache PDFBox • Actuator • OpenAPI (springdoc)



