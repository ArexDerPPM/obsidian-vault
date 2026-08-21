# 🔒 Shopify — CMS Cerrado

> [!IMPORTANT] Requisito: Autenticación
> El plugin requiere las credenciales **Login** y **SecretKey** de PlacetoPay para funcionar.
> → [[Autenticación|Ver documentación completa de Autenticación]]

**Shopify** es un CMS **cerrado**, lo que significa que **no se pueden hacer modificaciones** en el código del plugin de PlacetoPay.

> *Última actualización: 2026-07-22*

---

## 📥 Instalación

El plugin se descarga desde el enlace oficial:
[https://docs.placetopay.dev/checkout/plugins/](https://docs.placetopay.dev/checkout/plugins/)

---

## ⚙️ Configuración del Webhook de IVA

Pasos desde el panel de administración de Shopify:

1. Ir a **Notificaciones**
2. Crear nuevo **Webhook**
3. Configurar:
   - **Evento:** Actualización de pago
   - **Versión:** `2026-04`
   - **URL:** `https://plugin-latam.placetopay.com/api/webhooks/shopify/checkouts/update`
4. Copiar la **firma** que genera Shopify
5. Ir al plugin de PlacetoPay → **Más acciones → Gestionar**
6. Pegar la firma copiada

> [!IMPORTANT]
> El webhook de Shopify es **general para todos los comercios**, no deben desarrollarlo. La [[General/Sonda|Sonda]] también viene incluida con la instalación del plugin.

---

## 📝 Configuraciones Adicionales

### Términos y Condiciones / Políticas de Protección de Datos
Se configuran a nivel de **código HTML/CSS/JS**:
1. Inspeccionar la página con las herramientas del navegador
2. Localizar la sección del botón del carrito
3. Modificar el código para controlar los checkboxes

### Imagen de PlacetoPay
- Llamar al SVG de PlacetoPay desde el código
- Subir la imagen de las franquicias (PNG) a la **biblioteca de archivos** de Shopify

---

## ℹ️ Consideraciones Técnicas

### Estructura Buyer
En Shopify, al ser CMS cerrado, la estructura `buyer` solo llega con:
- `name`
- `email`

Los campos `document` y `mobile` llegan **vacíos**, pero el consumidor debe ingresarlos al pagar.

### Doble Pago
**No es necesario** validar el control de doble pago, ya que el CMS cerrado no lo permite.

### Redirección Post-Pago
En la configuración del plugin se puede marcar la opción:
- ☑ **"Omitir pantalla de PlacetoPay"** — Redirige al comercio al terminar el pago directamente.

---

## 🚀 Salida a Producción

Cuando el comercio tenga las credenciales de producción:
1. **Deshabilitar** el checkbox "Permitir pruebas"
2. **Deshabilitar** el slider "Modo pruebas" en la configuración de pagos de Shopify

---

## 🔗 Webhook

El [[General/Webhook|Webhook]] en Shopify es **general para todos los comercios** — no deben desarrollarlo.

> 🡒 [[General/Webhook|Ver documentación de Webhook]]

---

## 🔄 Sonda

La [[General/Sonda|Sonda]] en Shopify **viene incluida con la instalación del plugin** — no requiere configuración adicional.

> 🡒 [[General/Sonda|Ver documentación de Sonda]]
