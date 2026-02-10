# Vista de Despliegue

- **Servidor Backend (Spring Boot):** Desplegado en contenedor Docker, conectado a la base de datos PostgreSQL.  
- **Base de Datos:** PostgreSQL en servidor dedicado o contenedor, con copias de seguridad diarias.  
- **Frontend (React SPA):** Servido desde un servidor web Nginx, accesible vía HTTPS.  
- **Integraciones:** API REST para sistemas externos, seguro mediante JWT y HTTPS.  
- **Usuarios Internos:** Acceden vía navegador, autenticados y con roles definidos.
