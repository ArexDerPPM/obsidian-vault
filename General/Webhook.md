# 📡 Webhook — Proceso de Notificación

El **Webhook** es un mecanismo mediante el cual la pasarela PlacetoPay notifica al backend del comercio cuando el estado de un pago cambia.

> [!TIP]
> Cada producto tiene sus particularidades. Consulta:
> - [[PRODUCTOS/Pago Único/Pago Único#Webhook\|Webhook en Pago Único]]
> - [[PRODUCTOS/Suscripción/Suscripción#Webhook\|Webhook en Suscripción]]
> - [[PRODUCTOS/Dispersión/Dispersión#Webhook\|Webhook en Dispersión]]

---

## ⚙️ ¿Cómo funciona?

### 1. La pasarela envía un POST al `notificationUrl`

Cuando la pasarela detecta un cambio de estado, hace un **POST** al `notificationUrl` configurado al crear la sesión de pago. El body JSON incluye:

| Campo           | Descripción                                               |
| --------------- | --------------------------------------------------------- |
| `requestId`     | ID de la sesión en la pasarela                            |
| `reference`     | Referencia de la orden asignada por tu sistema            |
| `status.status` | Nuevo estado: `APPROVED`, `REJECTED`, `FAILED`, `PENDING` |
| `status.date`   | Fecha/hora del cambio                                     |
| `signature`     | Firma digital para verificar autenticidad                 |

### 2. El backend procesa el webhook

#### a. Parsear y validar
- Leer el JSON payload
- Validar que tenga los campos mínimos necesarios

#### b. Validar la firma (`signature`)

```javascript
stringToHash = requestId + status.status + status.date + secretKey;
hash = SHA256(stringToHash); //200 ok
// Comparar hash generado con la firma recibida
// Si no coincide → HTTP 403
```

> ⚠️ La notificación debe estar en **SHA-256**.

#### c. Localizar el pago en BD
- Usar `requestId` y/o `reference`
- Si no se encuentra → responder error (HTTP 404)

#### d. Verificar estado consultando la API oficial
- Llamar al endpoint **Get Session** / **Get Status**
- Enviar credenciales de autenticación
- El estado "real" es el que devuelve esta consulta
- Esto evita que un webhook manipulado cambie el estado sin confirmación

#### e. Actualizar el pago local
- Actualizar `status` con el estado verificado
- Guardar `updatedAt`
- Si hay `authorization`, guardar el código de autorización

#### f. Acciones de negocio según estado

| Estado                | Acción                                                                  |
| --------------------- | ----------------------------------------------------------------------- |
| `APPROVED`            | Marcar como aprobado, cerrar/eliminar el carrito asociado               |
| `REJECTED` o `FAILED` | Marcar como rechazado, dejar el carrito disponible para reintento       |
| `PENDING`             | No hacer nada extra, esperar otro webhook o la [[General/Sonda\|Sonda]] |

#### g. Responder a la pasarela
- Devolver **HTTP 200 OK** con mensaje simple `OK`
- Esto confirma que el webhook fue recibido y procesado correctamente

---

## 🔁 Diferencia entre Webhook y Sonda

| Característica | Webhook | [[General/Sonda\|Sonda]] |
|----------------|---------|----------------------|
| **Iniciador** | Pasarela → Comercio | Comercio → Pasarela |
| **Tiempo** | Inmediato | Periódico (cron) |
| **Propósito** | Notificar cambios | Barrer pendientes |
| **Redundancia** | No | Sí (respaldo) |

> [!IMPORTANT]
> La **Sonda** es el mecanismo de respaldo. Si el webhook falla (problemas de red, firewalls, túnel), la sonda actualizará los estados pendientes.
