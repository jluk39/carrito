# Carrito de compras

```mermaid
classDiagram
    class Usuario {
        +int id
        +String nombre
        +String email
        +String direccion
        +int celular
        +Carrito carrito
        +agregarCarrito(Carrito carrito)
    }
    
    class Carrito {
        +int id
        +Date fechaCreacion
        -float total
        +agregarTicket(Ticket ticket)
        +removerTicket(Ticket ticket)
        +calcularTotal(): float
    }
    
    class Ticket {
        +int id
        +int cantidad
        +float precioUnitario
        +calcularPrecioTotal(): float
    }
    
    class Evento {
        +int id
        +String nombre
        +Date fecha
        +String lugar
        +float precio
        +obtenerDetalles(): String
    }
    
    Usuario "1" -- "1" Carrito : contiene
    Carrito "1" -- "1..*" Ticket : incluye
    Ticket "1" -- "1" Evento : corresponde a
    
    Evento <|-- Concierto
    Evento <|-- PartidoFutbol
    
    class Concierto {
        -String banda
        -String genero
        +obtenerDetalles(): String
    }
    
    class PartidoFutbol {
        -String equipoLocal
        -String equipoVisitante
        -String liga
        +obtenerDetalles(): String
    }
