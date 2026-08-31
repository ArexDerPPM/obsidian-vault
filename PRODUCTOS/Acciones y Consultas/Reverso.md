# 🔄 Reverso — Anulación de Transacciones

> [!IMPORTANT] Requisito: Autenticación
> Para ejecutar un reverso es **obligatorio** autenticarse con **Login** y **SecretKey**.
> → [[Autenticación|Ver documentación completa de Autenticación]]

El **Reverso** permite anular una transacción **antes del cierre**, liberando los fondos reservados sin necesidad de un reembolso formal.

---

## 📋 ¿Cuándo usar el Reverso?

- Liberar fondos de una [[PRODUCTOS/Suscripción/Preautorización|Preautorización]] que no se va a capturar
- Anular una transacción que no debió procesarse
- Corregir errores antes del cierre del lote

---

## 🔗 Diferencia con Reembolso

| Aspecto | Reverso | [[PRODUCTOS/Acciones y Consultas/Reembolso\|Reembolso]] |
|---------|---------|----------------------|
| **Momento** | Antes del cierre / captura | Después de aprobado |
| **Tipo de txn** | Preautorizaciones | Pagos completados |
| **Fondos** | Se liberan sin moverse | Se devuelven del disponible |

---

## ⚙️ Restricciones por Red

> [!WARNING]
> Los reversos se pueden hacer **solo mediante el dashboard de PlacetoPay** o el consumo del API.

| Red | Reverso | Reembolso |
|-----|---------|-----------|
| **Austro** | ❌ No disponible | ❌ No disponible |
| **Bolivariano** | ❌ No disponible | — |
| **Medianet / Produbanco** | ✅ Disponible | ✅ Disponible |
| **Otras redes** | ✅ Disponible hasta las 7pm | — |

> [!NOTE]
> Los reversos hay para todas las redes **menos Austro**.
> Los reembolsos son solo para **Medianet** y **Produbanco**.

---

## 🔗 Diferencia con Cancelación

| Aspecto | Reverso | [[PRODUCTOS/Acciones y Consultas/Cancelación de Sesión\|Cancelación]] |
|---------|---------|----------------------|
| **Momento** | Después de aprobado (antes del cierre) | Antes de que se complete el pago |
| **Tipo de txn** | Preautorizaciones aprobadas | Sesiones pendientes |

---

## 📊 Acciones Relacionadas

| Acción | Descripción | Enlace |
|--------|-------------|--------|
| **Preautorización** | Reserva de fondos | [[PRODUCTOS/Suscripción/Preautorización\|Ver más]] |
| **Cancelación** | Cancelar sesión antes del pago | [[PRODUCTOS/Acciones y Consultas/Cancelación de Sesión\|Ver más]] |
| **Reportería** | Consultar historial | [[PRODUCTOS/Acciones y Consultas/Reportería\|Ver más]] |
| **Reembolso** | Devolución de un pago aprobado | [[PRODUCTOS/Acciones y Consultas/Reembolso\|Ver más]] |
