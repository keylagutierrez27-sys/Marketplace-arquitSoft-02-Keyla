# 🏛️ Diseño de Arquitectura en Capas - Marketplace de Mascotas

Para organizar la solución de manera limpia, escalable y mantenible, se propone una **arquitectura en tres capas**, separando claramente las responsabilidades del sistema en diferentes niveles.

## Estructura de Capas

| Capa | Pregunta que responde | Componentes / Módulos principales |
| :--- | :--- | :--- |
| **Presentación** | ¿Cómo interactúa el usuario? | Aplicación Web (Frontend), Interfaz de usuario, API REST. |
| **Lógica de Negocio** | ¿Qué hace el sistema? | Módulos de: Usuarios, Sellers, Catálogo, Carrito y Pedidos. |
| **Datos** | ¿Dónde se almacena la información? | Base de datos relacional/no relacional para persistencia de información. |

## Descripción de Responsabilidades

1. **Capa de Presentación:** Es la interfaz con la que interactúan directamente los actores (Clientes, Sellers y Administradores) a través de páginas web y catálogos, comunicándose con el backend mediante una API REST.
2. **Capa de Lógica de Negocio:** Es el núcleo del sistema (Backend). Se encarga de procesar las reglas de negocio, validar compras, gestionar los productos de los sellers, administrar carritos y coordinar el flujo de los pedidos.
3. **Capa de Datos:** Se encarga del almacenamiento persistente de la información del sistema (datos de usuarios, productos, stock, transacciones y pedidos). Además, desde esta capa o mediante el backend se gestionan las integraciones con sistemas externos (Pasarela de pago, Servicio de envío y ERP).

# 📊 Arquitectura Inicial del Sistema - Marketplace de Mascotas

## 1. Diagrama de Arquitectura en Capas

A continuación se presenta el diagrama esquemático que representa la organización de los actores, las tres capas principales del sistema (Presentación, Lógica de Negocio y Datos) y sus integraciones con sistemas externos.

```mermaid
flowchart TD
    %% =========================
    %% ACTORES
    %% =========================
    subgraph ACTORES ["ACTORES"]
        Cliente ["Cliente"]
        Seller ["Seller"]
        Admin ["Administrador"]
    end

    %% =========================
    %% PRESENTACIÓN
    %% =========================
    subgraph PRESENTACION ["PRESENTACIÓN"]
        Web ["Aplicación Web / API REST"]
    end

    %% =========================
    %% LÓGICA DE NEGOCIO
    %% =========================
    subgraph NEGOCIO ["LÓGICA DE NEGOCIO"]
        Usuarios ["Usuarios"]
        Sellers ["Sellers"]
        Catalogo ["Catálogo"]
        Carrito ["Carrito"]
        Pedidos ["Pedidos"]
    end

    %% =========================
    %% DATOS
    %% =========================
    subgraph DATOS ["DATOS"]
        BD ["Base de Datos Principal"]
    end

    %% =========================
    %% SISTEMAS EXTERNOS
    %% =========================
    subgraph EXTERNOS ["SISTEMAS EXTERNOS"]
        Pago ["Pasarela de Pago"]
        ERP ["ERP"]
        Envio ["Servicio de Envío"]
    end

    %% =========================
    %% FLUJO PRINCIPAL
    %% =========================
    ACTORES --> PRESENTACION
    PRESENTACION --> NEGOCIO
    NEGOCIO --> BD
    BD -.->|Integraciones| EXTERNOS

    %% =========================
    %% DISTRIBUCIÓN HORIZONTAL (Alineación)
    %% =========================
    Cliente ~~~ Seller
    Seller ~~~ Admin
    Usuarios ~~~ Sellers
    Sellers ~~~ Catalogo
    Catalogo ~~~ Carrito
    Carrito ~~~ Pedidos
    Pago ~~~ ERP
    ERP ~~~ Envio

    %% =========================
    %% ESTILOS VISUALES
    %% =========================
    style ACTORES fill:#1f2937,stroke:#3b82f6,stroke-width:2px,color:#fff
    style PRESENTACION fill:#1f2937,stroke:#10b981,stroke-width:2px,color:#fff
    style NEGOCIO fill:#1f2937,stroke:#f59e0b,stroke-width:2px,color:#fff
    style DATOS fill:#1f2937,stroke:#8b5cf6,stroke-width:2px,color:#fff
    style EXTERNOS fill:#1f2937,stroke:#ec4899,stroke-width:2px,color:#fff
    
    style Cliente fill:#374151,stroke:#60a5fa,color:#fff
    style Seller fill:#374151,stroke:#60a5fa,color:#fff
    style Admin fill:#374151,stroke:#60a5fa,color:#fff
    style Web fill:#374151,stroke:#34d399,color:#fff
    style Usuarios fill:#374151,stroke:#fbbf24,color:#fff
    style Sellers fill:#374151,stroke:#fbbf24,color:#fff
    style Catalogo fill:#374151,stroke:#fbbf24,color:#fff
    style Carrito fill:#374151,stroke:#fbbf24,color:#fff
    style Pedidos fill:#374151,stroke:#fbbf24,color:#fff
    style BD fill:#374151,stroke:#a78bfa,color:#fff
    style Pago fill:#374151,stroke:#f472b6,color:#fff
    style ERP fill:#374151,stroke:#f472b6,color:#fff
    style Envio fill:#374151,stroke:#f472b6,color:#fff