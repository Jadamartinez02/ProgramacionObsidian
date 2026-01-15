# Infraestructuras

* terminar base de datos 

BFF micro servicios - yo

mvc 
arquitectura por capas
arquitectura hexagonal 

---
# Ejemplo estructura 

ecommerce-microservices/
├── user-service/
│   ├── src/
│   ├── pom.xml
├── product-service/
│   ├── src/
│   ├── pom.xml
├── order-service/
│   ├── src/
│   ├── pom.xml
└── api-gateway/
    ├── src/
    ├── pom.xml

# Desafíos

Gestión de Múltiples Servicios
Gestionar una gran cantidad de servicios independientes puede ser abrumador.

Mantener la configuración actualizada para muchos componentes pequeños.

Configuración y gestión manual para muchos componentes pequeños.

----
## Comunicación Interservicios
La comunicación interservicios debe ser eficiente y segura, y a menudo se logra mediante protocolos.

La comunicación síncrona puede causar problemas de cadena de fallos.

---

## Consistencia de Datos

Es difícil rastrear una solicitud que se está procesando e involucra muchos componentes.

Pérdida de integridad y redundancia de datos.

---
## Tolerancia a fallos

Evita que los fallos se propaguen por el sistema.

Las estrategias garantizan que los servicios puedan fallar de forma independiente sin afectar al sistema general.

---

## Complejidad operativa
Enfatizando la entrega rápida, frecuente y confiable mediante pasos automatizados.

Ingeniería de confiabilidad del sitio (SRE)
Site Reliability Engineering