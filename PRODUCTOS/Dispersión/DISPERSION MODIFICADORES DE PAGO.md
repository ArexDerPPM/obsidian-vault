# 💲 Dispersión — Modificadores de Pago

> [!INFO] Notas de práctica
> Guía práctica para configurar **modificadores de pago** en la dispersión de merchants.

> **Relacionado:** [[PRODUCTOS/Dispersión/Dispersión|Dispersión]], [[PRODUCTOS/Dispersión/DISPERSIÓN _1|Tipos de Dispersión]]

---

## 🔧 Configuración en el Dashboard

### Paso 1 — Seleccionar el Sitio

Ejemplo en el sitio: **EGM Dispersión Principal**

![[Pasted image 20260827105457.png]]

### Paso 2 — Crear Modificador de Pago

Ir a **Modificadores de pago** → **Crear**

| Campo | Valor |
|-------|-------|
| **Tipo** | Tarifa |
| **Acuerdo** | EGM - Comercio de demostración 1 |
| **Monto porcentual** | 0 |
| **Monto fijo** | 1 |

![[Pasted image 20260827105603.png]]

### Paso 3 — Limpiar Caché

> [!WARNING]
> Después de crear el modificador, **limpiar caché** para que tome el cambio.

Ahora al hacer un flujo de **$19**, se agrega **$1** más al pago por el modificador de pago asociado.

---

## 📋 ¿Cuándo se usa?

Este modelo se ocupa cuando se crean **sitios de GAD's** (Gobiernos Autónomos Descentralizados):
- Uno del sitio propio
- Y el cobro del acuerdo

---

## 🔗 Documentación Relacionada

| Documento | Enlace |
|-----------|--------|
| Dispersión principal | [[PRODUCTOS/Dispersión/Dispersión]] |
| Tipos de dispersión | [[PRODUCTOS/Dispersión/DISPERSIÓN _1]] |
| Aerolíneas | [[PRODUCTOS/Dispersión/DISPERSION AEROLINEAS]] |
