# 🏪 Prestashop — CMS Abierto

> [!IMPORTANT] Requisito: Autenticación
> La integración requiere las credenciales **Login** y **SecretKey** configuradas en el plugin.
> → [[Autenticación|Ver documentación completa de Autenticación]]

**Prestashop** es un CMS abierto que permite personalización a nivel de código para integrar PlacetoPay.

---

## 📦 Clasificación

| Característica | Descripción |
|----------------|-------------|
| **Tipo** | CMS Abierto |
| **Personalización** | Modificable por el comercio |
| **Modalidad** | Soporta **Lightbox** |
| **Plugin** | [Descargar desde docs.placetopay.dev](https://docs.placetopay.dev/checkout/plugins/) |

---

## 💡 Lightbox en Prestashop

Al igual que WooCommerce, Prestashop **soporta Lightbox** como modalidad de pago.

> 🡒 [[PRODUCTOS/Pago Único/Lightbox|Ver documentación de Lightbox]]

> **Nota:** En Magento no es posible usar Lightbox porque da errores.

---

## 🔗 Webhook

El [[General/Webhook|Webhook]] en Prestashop sigue el mismo flujo estándar:
- Se configura el `notificationUrl` en la sesión de pago
- La pasarela notifica los cambios de estado automáticamente

> 🡒 [[General/Webhook|Ver documentación de Webhook]]

---

## 🔄 Sonda

La [[General/Sonda|Sonda]] en Prestashop se configura como tarea programada (cron) a nivel de hosting.
