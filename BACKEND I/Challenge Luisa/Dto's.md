¡Qué buen proyecto tienes entre manos! La **Arquitectura Hexagonal** (o de Puertos y Adaptadores) es excelente para mantener el código limpio, pero al principio puede ser confuso saber dónde poner cada cosa, especialmente los **DTOs (Data Transfer Objects)**.

He revisado la estructura general de este tipo de proyectos y cómo se integran con Spring Boot. Aquí tienes la claridad que necesitas para implementar DTOs correctamente.

---

## 1. ¿Qué es un DTO y por qué lo necesitas?

En arquitectura hexagonal, el **Dominio** (tus Entidades) es sagrado. No debería estar expuesto al mundo exterior (JSON, bases de datos, etc.).

* **El Problema:** Si devuelves tu Entidad directamente en un Controller, estás acoplando tu lógica de negocio a la API. Si cambias un campo en la DB, rompes el contrato con el cliente (Frontend).
* **La Solución (DTO):** Un objeto simple (POJO o Record) que solo transporta datos.
* **Request DTO:** Para recibir datos del cliente (ej. `CrearReservaRequest`).
* **Response DTO:** Para enviar datos al cliente (ej. `ReservaResponse`).



---

## 2. ¿Dónde ubicarlos en tu estructura?

En Arquitectura Hexagonal, los DTOs pertenecen a la capa de **Infraestructura** (específicamente en los adaptadores de entrada) o a la capa de **Aplicación**. **Nunca** deben estar en el Dominio.

### Estructura sugerida para tu proyecto:

```text
com.hotelcalifornia
│
├── domain (El núcleo: Reglas de negocio)
│   ├── model (Entidades puras, ej: Room, Reservation)
│   └── ports (Interfaces: RepositoryPort, ServicePort)
│
├── application (Casos de uso)
│   ├── services (Lógica que orquestra el dominio)
│   └── usecases
│
└── infrastructure (El mundo exterior)
    ├── adapters
    │   ├── input (REST Controllers)
    │   │   ├── rest
    │   │   │   ├── RoomController.java
    │   │   │   └── dtos  <-- AQUÍ VAN TUS DTOs DE ENTRADA/SALIDA
    │   │   │       ├── RoomRequest.java
    │   │   │       └── RoomResponse.java
    │   │   └── mapper <-- Mapeadores para pasar de DTO a Entidad
    │   └── output (Persistencia / DB)
    │       ├── persistence
    │       │   ├── RoomRepositoryAdapter.java
    │       │   └── entities (Entidades de JPA @Entity, diferentes a las de dominio)

```

---

## 3. Ejemplo Práctico (Implementación)

Supongamos que quieres crear una habitación.

### A. El DTO (Infraestructura)

Usa **Java Records** (disponibles desde Java 16/17) para que sean inmutables y limpios.

```java
// infrastructure/adapters/input/rest/dtos/RoomRequest.java
public record RoomRequest(
    String roomNumber,
    String type,
    Double price
) {}

```

### B. El Mapper (Infraestructura)

Necesitas convertir ese DTO a tu objeto de **Dominio**. Puedes usar una clase manual o una librería como **MapStruct**.

```java
// infrastructure/adapters/input/rest/mapper/RoomRestMapper.java
public class RoomRestMapper {
    public static Room toDomain(RoomRequest dto) {
        return new Room(dto.roomNumber(), dto.type(), dto.price());
    }

    public static RoomResponse toResponse(Room domain) {
        return new RoomResponse(domain.getId(), domain.getRoomNumber());
    }
}

```

### C. El Controller (Infraestructura)

El controlador recibe el DTO, lo mapea al dominio y llama al servicio.

```java
@RestController
@RequestMapping("/api/rooms")
public class RoomController {
    
    private final CreateRoomUseCase createRoomUseCase;

    @PostMapping
    public ResponseEntity<RoomResponse> create(@RequestBody RoomRequest request) {
        // 1. DTO -> Dominio
        Room roomToCreate = RoomRestMapper.toDomain(request);
        
        // 2. Ejecutar lógica de negocio
        Room createdRoom = createRoomUseCase.execute(roomToCreate);
        
        // 3. Dominio -> DTO de respuesta
        return ResponseEntity.ok(RoomRestMapper.toResponse(createdRoom));
    }
}

```

---

## 4. El "Truco" de las dos Entidades

Para que la arquitectura sea 100% pura:

1. **Domain Entity:** Una clase Java simple sin anotaciones de Spring o JPA.
2. **Infrastructure Entity (@Entity):** La clase que tiene `@Table`, `@Id`, etc.

El flujo de datos sería:
`DTO (API)` -> `Domain Entity (Lógica)` -> `JPA Entity (DB)`

### ¿Por qué hacer todo esto?

Si mañana decides dejar de usar SQL y pasar a MongoDB, solo cambias la capa de **Infrastructure**. Tu **Domain** y tus **DTOs** de la API no se enteran de nada. El sistema es totalmente modular.

**¿Te gustaría que te ayude a configurar MapStruct en tu proyecto para que estos mapeos se hagan automáticamente sin escribir tanto código manual?**