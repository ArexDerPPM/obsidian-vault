# ❌ Cancelación de Sesión

> [!IMPORTANT] Requisito: Autenticación
> Para cancelar una sesión es **obligatorio** autenticarse con **Login** y **SecretKey**.
> → [[Autenticación|Ver documentación completa de Autenticación]]

Permite **cancelar una sesión de pago** antes de que expire o antes de que el usuario complete la transacción.

---

## 📋 ¿Cuándo cancelar?

- El usuario abandona el proceso de pago
- Se detecta una transacción fraudulenta
- El carrito expiró en el sistema del comercio
- Se necesita liberar el `requestId` para nuevos intentos

---

## 🔗 Integración

La cancelación se realiza mediante una llamada a la API de PlacetoPay con el `requestId` de la sesión.

> 📖 *Consultar documentación oficial para el endpoint específico de cancelación.*

---

## ⚠️ Consideraciones

- Solo se puede cancelar una sesión en estado `PENDING`
- Una vez que el pago fue `APPROVED` o `REJECTED`, no se puede cancelar
- Para pagos aprobados, usar [[PRODUCTOS/Acciones y Consultas/Reembolso|Reembolso]]
- Para preautorizaciones, usar [[PRODUCTOS/Acciones y Consultas/Reverso|Reverso]]

---

## 📊 Acciones Relacionadas

| Acción | Descripción | Enlace |
|--------|-------------|--------|
| **Reembolso** | Devolución de un pago ya aprobado | [[PRODUCTOS/Acciones y Consultas/Reembolso\|Ver más]] |
| **Reverso** | Anulación de una preautorización | [[PRODUCTOS/Acciones y Consultas/Reverso\|Ver más]] |
| **Reportería** | Consulta de transacciones | [[PRODUCTOS/Acciones y Consultas/Reportería\|Ver más]] |
