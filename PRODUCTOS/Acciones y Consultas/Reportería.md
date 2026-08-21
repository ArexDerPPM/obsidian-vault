# 📊 Reportería — Consultas y Reportes

> [!IMPORTANT] Requisito: Autenticación
> Todas las consultas a la API requieren autenticación con **Login** y **SecretKey**.
> → [[Autenticación|Ver documentación completa de Autenticación]]

La **Reportería** agrupa todas las operaciones de consulta sobre transacciones, necesarias para conciliación, auditoría y monitoreo del negocio.

---

## 🔍 Consulta de Transacciones

### Get Request Information
```
GET https://checkout-test.placetopay.ec/api/session/{requestId}
```

Consulta el estado de una sesión de pago específica usando su `requestId`.

**Uso típico:**
- Después de recibir un [[General/Webhook|Webhook]] para verificar el estado
- En la [[General/Sonda|Sonda]] para actualizar transacciones pendientes
- Para reconciliación manual

> 📄 Notas del endpoint de reportería: [[Recursos/documentos/ENDPOINT REPORTERIA|ENDPOINT REPORTERIA]]

### Campos de Respuesta

| Campo | Descripción |
|-------|-------------|
| `requestId` | ID de la sesión |
| `status.status` | Estado actual (`APPROVED`, `REJECTED`, `FAILED`, `PENDING`) |
| `status.date` | Fecha del último cambio |
| `payment.reference` | Referencia del comercio |
| `authorization` | Código de autorización (solo pagos aprobados) |
| `payment.amount` | Monto y moneda |

---

## 📈 Conciliación

La conciliación permite cotejar los pagos registrados en el comercio contra los reportes de PlacetoPay.

### Para CMS Cerrados

En [[PRODUCTOS/CMS/Cerrados/VTEX|VTEX]] se puede obtener información de conciliación desde el panel administrativo.

![[Recursos/assets/imagen-19.png]]

### Proceso Recomendado

1. Ejecutar la [[General/Sonda|Sonda]] para actualizar estados pendientes
2. Consultar todas las transacciones del día
3. Cruzar contra los registros del comercio
4. Conciliar diferencias

---

## 📋 Acciones Relacionadas

| Acción | Descripción | Enlace |
|--------|-------------|--------|
| **Cancelación** | Cancelar una sesión antes del vencimiento | [[PRODUCTOS/Acciones y Consultas/Cancelación de Sesión\|Ver más]] |
| **Reembolso** | Devolución de un pago aprobado | [[PRODUCTOS/Acciones y Consultas/Reembolso\|Ver más]] |
| **Reverso** | Anulación de una preautorización | [[PRODUCTOS/Acciones y Consultas/Reverso\|Ver más]] |
