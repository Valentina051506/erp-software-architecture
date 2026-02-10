# Introducción y Metas
## Objetivo del Sistema ERP
El sistema ERP tiene como objetivo centralizar y automatizar los procesos de negocio de la empresa, permitiendo una gestión eficiente de Compras, Facturación, Stock/Costos, Activos Fijos, Empleados y EIS.
## Requisitos de Negocio - Módulo de Compras
1. Permitir registrar y gestionar proveedores.  
2. Permitir registrar y mantener el catálogo de productos.  
3. Gestionar solicitudes de compra y su aprobación.  
4. Generar órdenes de compra a partir de solicitudes aprobadas.  
5. Integrar con el sistema contable externo para enviar facturas y registros.  
6. Consultar historial de órdenes y solicitudes.  
7. Controlar permisos de usuario según roles (administrador, solicitante, directivo).

# Decisiones Tecnológicas

- **Backend:** Java con Spring Boot, para lógica de negocio centralizada.  
- **Frontend:** Aplicación web SPA desarrollada con React, accesible por navegadores modernos.  
- **Base de Datos:** PostgreSQL, para almacenamiento estructurado de datos del ERP.  
- **Integración con Sistemas Externos:** REST API para conexión con sistema contable y pasarela de pagos.  
- **Autenticación y Seguridad:** Gestión de roles y permisos por JWT.

# Alcance y Contexto del Sistema

El ERP abarca todos los procesos de negocio de la empresa. Este diagrama de contexto muestra al ERP como un sistema central que interactúa con usuarios internos (Compras, RRHH, Directivos) y sistemas externos (Contable, Banco).

## Diagrama de Contexto (C1)
IMAGEN

# Vista de Contenedores (C2)

El diagrama de contenedores muestra la arquitectura interna del ERP, separando los principales contenedores y sus responsabilidades:

1. **Aplicación Web (Web App):** Interfaz principal para usuarios internos, permite gestionar compras, solicitudes, empleados y consultar reportes.  
2. **Servidor API (API Server):** Exposición de servicios REST para interacción interna y con sistemas externos, maneja la lógica de negocio y validaciones.  
3. **Base de Datos Central (DB):** Almacena de manera estructurada todas las entidades del ERP: proveedores, productos, solicitudes, órdenes, empleados, activos fijos.  

## Diagrama de Contenedores (C2)

IMAGEN

# Vista de Ejecución (Runtime)

## Escenario Crítico: Generar una Orden de Compra

Este escenario describe cómo el sistema ERP procesa la creación de una orden de compra a partir de una solicitud aprobada.

### Flujo de Interacciones
1. El **Responsable de Compras** selecciona una solicitud aprobada en la web.  
2. La **Aplicación Web** envía la solicitud al **Servidor API**.  
3. El **API** verifica los datos en la **Base de Datos**.  
4. Se registra la **Orden de Compra** en la base de datos.  
5. El **API** envía la información de la orden al **Sistema Contable Externo**.  
6. Se confirma la creación de la orden en la **Aplicación Web** y se notifica al usuario.

## Diagrama de Secuencia

![Diagrama de Contexto](./docs/D1.png)

# Vista de Despliegue (Opcional)

- **Servidor Backend (Spring Boot):** Desplegado en contenedor Docker, conectado a la base de datos PostgreSQL.  
- **Base de Datos:** PostgreSQL en servidor dedicado o contenedor, con copias de seguridad diarias.  
- **Frontend (React SPA):** Servido desde un servidor web Nginx, accesible vía HTTPS.  
- **Integraciones:** API REST para sistemas externos, seguro mediante JWT y HTTPS.  
- **Usuarios Internos:** Acceden vía navegador, autenticados y con roles definidos.

# Glosario

- **Producto:** Artículo disponible para compra, con nombre, descripción, unidad de medida y precio unitario.  
- **Proveedor:** Empresa o persona que suministra productos a la compañía.  
- **Solicitud de Compra:** Petición de productos realizada por un usuario solicitante, que puede ser aprobada o rechazada.  
- **Detalle de Solicitud:** Relación entre una solicitud y los productos solicitados, con cantidades específicas.  
- **Orden de Compra:** Documento formal que autoriza la compra de productos a un proveedor, generado a partir de una solicitud aprobada.  
- **Usuario:** Persona que interactúa con el ERP, con roles como administrador de compras, solicitante, RRHH o directivo.  
