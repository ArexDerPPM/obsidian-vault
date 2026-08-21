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

## ⚙️ Integración

> 📖 *Consultar documentación oficial para el endpoint específico de reverso.*

---

## 📊 Acciones Relacionadas

| Acción | Descripción | Enlace |
|--------|-------------|--------|
| **Preautorización** | Reserva de fondos | [[PRODUCTOS/Suscripción/Preautorización\|Ver más]] |
| **Cancelación** | Cancelar sesión antes del pago | [[PRODUCTOS/Acciones y Consultas/Cancelación de Sesión\|Ver más]] |
| **Reportería** | Consultar historial | [[PRODUCTOS/Acciones y Consultas/Reportería\|Ver más]] |
SOLO PODEMOS HACER REVERSOS MEDIANTE EL DASHBOARD DE PLACETOPAY O EL CONSUMO DEL API CUANDO

Los reversos hay para todas las redes menos Austro

Los reembolsos si son solo para Medianet Produbanco


EN BOLIVARIANO  no podemos hacer reversos tampoco

Los demas los reversos se lo puede hacer hasta las 7pm.
