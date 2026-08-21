# 🔄 Sonda (Cron) — Proceso de Barrido

La **Sonda** es un mecanismo de respaldo que actualiza los estados de las transacciones incluso si:

- No se recibió el [[General/Webhook|Webhook]] (problemas de red, túnel, firewalls, etc.)
- El usuario cerró la ventana del navegador y nunca volvió a la `returnUrl`

> [!TIP]
> Cada producto tiene configuraciones específicas para la sonda:
> - [[PRODUCTOS/Pago Único/Pago Único#Sonda\|Sonda en Pago Único]]
> - [[PRODUCTOS/Suscripción/Suscripción#Sonda\|Sonda en Suscripción]]
> - [[PRODUCTOS/CMS/Abiertos/Magento#Sonda\|Sonda en Magento]]

---

## ⚙️ ¿Qué dispara la Sonda?

- Normalmente es un **comando / job de consola** que se ejecuta periódicamente
- Mecanismos: `cron`, `scheduler`, servicio background
- **No recibe HTTP del exterior**: es el backend del comercio el que toma la iniciativa

## 📋 ¿Qué hace la Sonda?

### 1. Buscar pagos pendientes en la BD
- Consultar todos los pagos cuyo estado actual sea `PENDING`
- Opcionalmente filtrar por antigüedad, usuario, etc.

### 2. Para cada pago `PENDING`:
- Llamar al endpoint de la pasarela **Get Session / Get Status** usando el `requestId`
- Leer el `status.status` de la respuesta

### 3. Actualizar el registro local:

| Estado devuelto | Acción |
|-----------------|--------|
| `PENDING` | No modificar nada |
| `APPROVED` | Actualizar status, authorization, fechas. Cerrar carrito. |
| `REJECTED` o `FAILED` | Actualizar status. Mantener carrito disponible. |

### 4. Acciones de negocio
- **APPROVED**: Cerrar/eliminar el carrito asociado para evitar doble compra
- **REJECTED / FAILED**: Mantener el carrito para que el usuario pueda reintentar

### 5. Persistir cambios
- Guardar todos los cambios al final del proceso (o por cada pago, según diseño)

---

## 🆚 Sonda vs. Webhook

| Aspecto | Sonda | Webhook |
|---------|-------|---------|
| Dirección | Comercio → Pasarela (pull) | Pasarela → Comercio (push) |
| Velocidad | Depende del intervalo (5-10 min) | Inmediato |
| Propósito | Respaldo y reconciliación | Notificación en tiempo real |
| Configuración | Cron / Scheduler | `notificationUrl` en la sesión |
