# 💳 Dispersión — Distribución de Pagos

> [!IMPORTANT] Requisito: Autenticación
> Para utilizar dispersión es **obligatorio** autenticarse con **Login** y **SecretKey**.
> → [[Autenticación|Ver documentación completa de Autenticación]]

La **Dispersión** permite distribuir un pago entre múltiples destinatarios. Es útil para plataformas que necesitan dividir el monto de una transacción entre varios beneficiarios.

> **Relacionado:** [[PRODUCTOS/Pago Único/Pago Único|Pago Único]], [[PRODUCTOS/Suscripción/Suscripción|Suscripción]], [[DISPERSIÓN _1|Dispersión 1 — notas de flujo]]

---

## 📋 ¿Qué es la Dispersión?

La dispersión o "split payment" permite que un solo pago sea distribuido automáticamente entre:

- El comercio principal (comisión)
- Subcomercios o vendedores
- Terceros (logística, impuestos, etc.)

---

## 🔗 Webhook

El [[General/Webhook|Webhook]] en dispersión notifica:
- El estado del pago principal
- El estado de cada dispersión individual

> 🡒 Ver [[General/Webhook]] para el detalle completo del proceso.

---

## 🔄 Sonda

La [[General/Sonda|Sonda]] en dispersión:
- Revisa pagos y dispersiones en estado `PENDING`
- Consulta el estado actual mediante la API
- Actualiza los registros locales de cada dispersión

> 🡒 Ver [[General/Sonda]] para el detalle completo del proceso.

---

## 📖 Documentación Oficial

> *En construcción — próximamente más detalles sobre el payload y configuración de dispersión.*
