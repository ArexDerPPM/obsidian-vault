# 💰 Reembolso — Devolución de Pagos

> [!IMPORTANT] Requisito: Autenticación
> Para realizar reembolsos es **obligatorio** autenticarse con **Login** y **SecretKey**.
> → [[Autenticación|Ver documentación completa de Autenticación]]

El **Reembolso** permite devolver total o parcialmente el monto de un pago que ya fue aprobado.

---

## 📋 Tipos de Reembolso

| Tipo | Descripción |
|------|-------------|
| **Total** | Devolución del 100% del monto original |
| **Parcial** | Devolución de una parte del monto original |

---

## 🔗 Integración

El reembolso se realiza mediante una llamada a la API de PlacetoPay.

> 📖 *Consultar documentación oficial para el endpoint específico de reembolso.*

---

## ⚠️ Consideraciones

- Solo aplica para pagos en estado `APPROVED`
- El reembolso parcial se puede realizar múltiples veces hasta agotar el monto original
- Los tiempos de procesamiento varían según la red y el banco emisor
- Para preautorizaciones no capturadas, usar [[PRODUCTOS/Acciones y Consultas/Reverso|Reverso]]

---

## 📊 Acciones Relacionadas

| Acción | Descripción | Enlace |
|--------|-------------|--------|
| **Cancelación** | Cancelar sesión antes del pago | [[PRODUCTOS/Acciones y Consultas/Cancelación de Sesión\|Ver más]] |
| **Reverso** | Anulación de preautorización | [[PRODUCTOS/Acciones y Consultas/Reverso\|Ver más]] |
| **Reportería** | Consultar historial de transacciones | [[PRODUCTOS/Acciones y Consultas/Reportería\|Ver más]] |
