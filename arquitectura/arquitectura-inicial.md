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