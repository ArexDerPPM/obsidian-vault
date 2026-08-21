# 🏦 PlacetoPay — Documentación Interna

> **PlacetoPay** es una pasarela de pagos que se integra con los comercios para realizar transacciones a través de múltiples redes y marcas. Actualmente la última actualización es la integración con **DEUNA**.
> *(Última actualización: 2026-07-22)*

> [!CAUTION] ⚠️ Requisito #1: Autenticación
> **Todos los productos y servicios** de PlacetoPay requieren autenticación obligatoria con **Login** y **SecretKey**. Sin las credenciales no es posible operar Pago Único, Suscripción, Preautorización, Dispersión, ni las Acciones y Consultas.
> → [[Autenticación|Ver documentación completa de Autenticación]]

---

## 📦 Productos

| Producto            | Descripción                                                   | Enlaces                                            |
| ------------------- | ------------------------------------------------------------- | -------------------------------------------------- |
| **Pago Único**      | Flujo básico de pago: creación de sesión + consulta de estado | [[PRODUCTOS/Pago Único/Pago Único\|Ver más]]       |
| **Lightbox**        | Modal emergente sin salir del sitio del comercio              | [[PRODUCTOS/Pago Único/Lightbox\|Ver más]]         |
| **Suscripción**     | Pagos recurrentes con tokenización de tarjeta                 | [[PRODUCTOS/Suscripción/Suscripción\|Ver más]]     |
| **Diferido**        | Modalidad de pago diferido en suscripciones                   | [[PRODUCTOS/Suscripción/Diferido\|Ver más]]        |
| **Preautorización** | Reserva de fondos antes del cobro final                       | [[PRODUCTOS/Suscripción/Preautorización\|Ver más]] |
| **Dispersión**      | Distribución de pagos a múltiples destinatarios               | [[PRODUCTOS/Dispersión/Dispersión\|Ver más]]       |
| **Dispersión 1**    | Notas de flujo y tipos de dispersión en Ecuador               | [[DISPERSIÓN _1\|Ver más]]     |
| **Reautorizaciones**| Reautorización de preautorizaciones (incrementos/liberación)  | [[PRODUCTOS/PREAUTORIZACIONES/Reautorizaciones\|Ver más]] |
| **Pago On click**   | Pago con tarjeta guardada (wallet) en un solo clic            | [[PRODUCTOS/PAGO ONCLICK/Pago On click\|Ver más]]  |

### ⚙️ Acciones y Consultas

| Acción | Descripción |
|--------|-------------|
| [[PRODUCTOS/Acciones y Consultas/Reportería\|📊 Reportería]] | Consultas de transacciones, reportes y conciliación |
| [[PRODUCTOS/Acciones y Consultas/Cancelación de Sesión\|❌ Cancelación de Sesión]] | Cancelar una sesión de pago antes de su vencimiento |
| [[PRODUCTOS/Acciones y Consultas/Reembolso\|💰 Reembolso]] | Devolución total o parcial de un pago |
| [[PRODUCTOS/Acciones y Consultas/Reverso\|🔄 Reverso]] | Anulación de una transacción antes del cierre |

---

## 🖥️ CMS

### 📖 Abiertos (modificables por el comercio)

| CMS | Descripción | Enlace |
|-----|-------------|--------|
| **WooCommerce (WordPress)** | Plugin open-source para tiendas en WordPress | [[PRODUCTOS/CMS/Abiertos/WordPress\|Ver más]] |
| **Magento** | Plataforma empresarial de código abierto | [[PRODUCTOS/CMS/Abiertos/Magento\|Ver más]] |
| **Prestashop** | CMS open-source para e-commerce | [[PRODUCTOS/CMS/Abiertos/Prestashop\|Ver más]] |

### 🔒 Cerrados (no modificables por el comercio)

| CMS | Descripción | Enlace |
|-----|-------------|--------|
| **Shopify** | Plataforma SaaS de e-commerce | [[PRODUCTOS/CMS/Cerrados/Shopify\|Ver más]] |
| **VTEX** | Plataforma empresarial SaaS | [[PRODUCTOS/CMS/Cerrados/VTEX\|Ver más]] |
| **Jumpseller** | CMS cerrado para tiendas online | [[PRODUCTOS/CMS/Cerrados/Jumpseller\|Ver más]] |

---

## 🔗 API

| Tema | Descripción | Enlace |
|------|-------------|--------|
| **Autenticación** | Login, TranKey, Seed, Nonce para consumir la API | [[Autenticación\|Ver más]] |
| **3DS** | Autenticación 3D Secure para mayor seguridad | [[Autenticación#3D Secure (3DS)\|Ver más]] |
| **OTP** | One-Time Password para validación de transacciones | [[Autenticación#OTP (One-Time Password)\|Ver más]] |

---

## ⚙️ General

| Componente | Descripción | Enlace |
|------------|-------------|--------|
| **Webhook** | Notificaciones automáticas de cambio de estado | [[General/Webhook\|Ver más]] |
| **Sonda (Cron)** | Barrido periódico de transacciones pendientes | [[General/Sonda\|Ver más]] |
| **XAMPP** | Entorno de desarrollo local | [[General/XAMPP Control\|Ver más]] |

---

## 💻 Desarrollos

| Proyecto | Descripción | Enlace |
|----------|-------------|--------|
| **Proyecto GYE** | Landing de pagos SEP/prediales para el municipio de Guayaquil | [[DESARROLLOS/Proyecto GYE\|Ver más]] |

---

## 📚 Capacitaciones

| Tema | Descripción | Enlace |
|------|-------------|--------|
| **Link de Pagos** | Capacitación técnica del Link de Pagos (JV) | [[LINK DE PAGOS AUTOMATIZAZOS\|Ver más]] |

---

## 📎 Recursos Útiles

| Recurso | Enlace |
|---------|--------|
| 🌐 Documentación técnica oficial | [docs.placetopay.dev](https://docs.placetopay.dev/) |
| 📚 Librerías (SDKs) | [SDKs y Plugins](https://docs.placetopay.dev/checkout/plugins/) |
| 💳 Tarjetas de prueba | [Testing Cards](https://docs.placetopay.dev/gateway/testing-card/) |
| 🔌 Plugins disponibles | [Shopify, WordPress, Magento, Prestashop, Jumpseller, VTEX](https://docs.placetopay.dev/checkout/plugins/) |
| 📄 Enlaces Útiles (notas) | [[Recursos/Enlaces Útiles\|Ver más]] |
| 💳 Tarjetas de Prueba (notas) | [[Recursos/Tarjetas de Prueba\|Ver más]] |

> [!TIP]
> Usa las notas al pie y los enlaces `[[wiki]]` para navegar entre documentos. Cada producto tiene sus propias páginas de [[General/Webhook|Webhook]] y [[General/Sonda|Sonda]] con detalles específicos.
