# Carrito de compras

```mermaid
classDiagram
    class Usuario {
        -int id
        +String nombre
        +String email
        +String direccion
        +int celular
        +Carrito carrito
        +agregarCarrito(Carrito carrito)
    }

    class Administrador {
        +gestionarUsuarios(): void
        +modificarEventos(): void
    }

    class Cliente {
        +String metodoPago
        +historialCompras(): List<Ticket>
    }

    class Vendedor {
        +String areaVentas
        +listarEventos(): List<Evento>
    }

    class Carrito {
        +int id
        +Date fechaCreacion
        -float total
        +agregarPedido(Pedido pedido)
        +calcularTotal(): float
    }

    class Pedido {
        +int id
        +Date fecha
        +String estado
        +detallesEnvio(): String
        +calcularTotal(): float
    }

    class Pago {
        +int id
        +Date fechaPago
        +float monto
        +String metodo
        +procesarPago(): bool
    }

    class Ticket {
        -int id
        +int cantidad
        +float precioUnitario
        +bool esFisico
        +calcularPrecioTotal(): float
    }

    class Evento {
        -int id
        +String nombre
        +Date fecha
        +String lugar
        +float precio
        +obtenerDetalles(): String
    }

    Usuario "1" -- "1" Carrito : contiene
    Carrito "1" -- "1" Pedido : genera
    Pedido "1" -- "1" Pago : procesa
    Pedido "1" -- "1..*" Ticket : incluye
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

    Usuario <|-- Administrador
    Usuario <|-- Cliente
    Usuario <|-- Vendedor

