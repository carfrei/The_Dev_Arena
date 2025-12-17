# The Nana Store 🛍️

Una plataforma de e-commerce especializada en venta y recarga de divisas in-game para videojuegos móviles, con soporte para 14+ países.

---

## 🎯 Descripción del Proyecto

**The Nana Store** es una aplicación web completa que permite a usuarios comprar recargas de divisas para videojuegos populares (Game Pass, Gemas, etc.). La plataforma incluye:

- **Tienda Online:** Interfaz responsiva para compra de recargas
- **Multi-región:** Soporte para 14+ países con precios localizados
- **Panel Admin (Big Nana):** Gestión de inventario, pedidos y usuarios
- **Checkout seguro** con múltiples pasarelas de pago

---

## 🛠️ Stack Tecnológico

| Capa | Tecnología |
|------|-----------|
| **Frontend** | HTML5, CSS3, JavaScript vanilla |
| **Backend** | Python / Flask |
| **Base de Datos** | MongoDB Atlas (cloud) |
| **Autenticación** | JWT + bcrypt |
| **Pagos** | Stripe, PayPal, Binance |
| **Almacenamiento** | Cloudflare R2 (comprobantes) |
| **Email** | Gmail API (notificaciones) |
| **Infraestructura** | Render.com (deployment) |

---

## 🏗️ Arquitectura y Desafíos Técnicos

### 1. **Multi-país con Precios Dinámicos**
Implementé un sistema modular que permite gestionar precios y productos específicos por región. Cada país tiene su propio archivo HTML con rutas y configuración local.

### 2. **Integración de Múltiples Pasarelas de Pago**
- **Stripe:** Pagos con tarjeta de crédito
- **PayPal:** Checkout seguro para transferencias
- **Binance:** Crypto-payments para usuarios tech-savvy
- **Sistema de fallback:** Si una pasarela falla, el flujo redirige automáticamente

### 3. **Autenticación y Seguridad**
- JWT tokens con expiración configurable
- Contraseñas hasheadas con bcrypt
- Rate limiting para proteger endpoints
- Validación de email en tiempo real

### 4. **Notificaciones Transaccionales**
Sistema de email integrado con Gmail API que envía:
- Confirmación de compra
- Recibos
- Alertas para admin en órdenes anormales

### 5. **Gestión de Archivos en la Nube**
Comprobantes y pruebas de pago se suben a Cloudflare R2, reduciendo almacenamiento local y mejorando performance.

### 6. **Logging y Monitoreo**
Sistema de logs persistente para rastrear errores en producción y auditoria de transacciones.

---

## 📸 Demostración Visual

### Splash Screen
![Splash](./screenshots/splash.png)
*Pantalla inicial de bienvenida con branding de The Nana Store.*

### Selector de País
![Selector País](./screenshots/selector_pais.png)
*Selección de región para precios localizados y disponibilidad de juegos.*

### Catálogo de Juegos
![Muestra Juegos](./screenshots/muestra_juegos.png)
*Catálogo de videojuegos disponibles con filtros y búsqueda.*

### Paquetes y Precios
![Paquetes](./screenshots/paquetes.png)
*Opciones de recarga con diferentes valores y divisas por juego.*

### Ranking
![Ranking](./screenshots/ranking.png)
*Sistema de clasificación y estadísticas de compras.*

### Autenticación
![Login](./screenshots/log.png)
*Interfaz de inicio de sesión segura con validación.*

### Panel de Dashboard
![Dashboard](./screenshots/dashboard.png)
*Panel administrativo: gestión de órdenes, usuarios e inventario.*

### Checkout Seguro
![Checkout](./screenshots/checkout.png)
*Flujo de pago multi-pasarela con validación de datos y manejo de errores.*

---

## 📊 Resultados Técnicos

✅ **Performance:**
- Página carga en <2s (optimización de assets)
- API responde en <500ms promedio
- Rate limiting previene abuse

✅ **Escalabilidad:**
- MongoDB Atlas maneja concurrencia automática
- Render.com escala dinámicamente con tráfico
- Queue de emails asíncrono no bloquea API

✅ **Seguridad:**
- 0 vulnerabilidades OWASP en endpoints
- Todas las transacciones encriptadas
- Logs de auditoría para cada cambio

✅ **UX:**
- 100% responsivo (mobile-first)
- Soporte para 14+ idiomas/regiones
- Checkout en 3 pasos máximo

---

## 🎓 Aprendizajes Clave

1. **Integración de APIs:** Trabajar simultáneamente con Stripe, PayPal, Binance enseña cómo manejar diferentes esquemas y errores de terceros.

2. **Manejo de Transacciones:** Implementar confirmación de pago + creación de orden + email atomáticamente fue complejo pero crítico.

3. **Modularidad:** Separar lógica de pagos, emails y uploads en módulos independientes (`stripe_utils.py`, `gmail_utils.py`, etc.) hace el código mantenible.

4. **Monitoreo en Producción:** Logs detallados son la diferencia entre "qué salió mal" y "dónde salió mal".

---

## 🔗 Demo & Repositorio

- **Sitio Live:** https://thenanastore.com
- **Portafolio GitHub:** https://github.com/carfrei/Portfolio

---

**Nota:** El código fuente completo es privado. Este documento actúa como guía técnica de la arquitectura y decisiones de diseño.
