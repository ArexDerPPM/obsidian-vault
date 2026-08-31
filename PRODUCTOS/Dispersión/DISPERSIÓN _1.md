# 💰 Dispersión 1 — Notas de Flujo y Tipos en Ecuador

> [!INFO] Notas de sesión
> Notas detalladas sobre los tipos de dispersión, flujos de seguridad y particularidades de aerolíneas en Ecuador.

> **Relacionado:** [[PRODUCTOS/Dispersión/Dispersión|Dispersión — Documentación principal]], [[PRODUCTOS/Dispersión/DISPERSION AEROLINEAS|Dispersión Aerolíneas]]

---

## 🔑 Concepto

Una **sesión de dispersión** es una sesión en la cual el monto total del pago será dividido en diferentes destinos.

Para usar este tipo de sesión, se debe enviar la propiedad `payment.dispersion` que contiene un arreglo de `DispersionRequests`.

![[Recursos/assets/Pasted image 20260812101939.png]]

---

## 📋 Tipos de Dispersión en Ecuador

| Tipo | Descripción |
|------|-------------|
| **1. PVA** | A aerolíneas |
| **2. Comercio** | Van a poder cobrar — se distribuye el monto entre diferentes cuentas |
| **3. Modificador de Pago (Merchants)** | Misma particularidad pero se controla directamente desde el panel |

> **Relacionado:** [[PRODUCTOS/Dispersión/DISPERSION MODIFICADORES DE PAGO|Modificadores de Pago]]

---

## 🏗️ Estructura de Sesiones

Al momento de crear la sesión se crea:
- **Sesión padre** de tipo `DISPERSION` — contiene el valor total y estado general
- **Sesiones hijas** de tipo `AUTH_ONLY` — contienen la información de cada parte dispersada

> Los datos de autorización y recibo de la transacción padre serán los mismos que la primera transacción procesada.

---

## 🔄 Flujo de Seguridad

```
INICIA EL FLUJO
  → Filtro de seguridad (Del sitio padre)
    → Datos de control (sitio hijo)
      → Datos de control (sitio hijo)
        → Datos de control (sitio hijo)
```

> [!WARNING]
> Se pueden realizar hasta **máximo 3 dispersiones** contando al sitio padre para cualquiera de los tres tipos.

---

## 📊 Dos Flujos de Dispersión

### 1. El sitio padre COBRA
- Se asegura el monto de comisión que cobra el sitio padre
- Modelo de tiendas grandes con tiendas internas (ej: Falabella, Marathon, Totto)

### 2. El sitio padre NO COBRA
- Solo es un paso a los hijos
- El sitio padre no cobra pero administra la dispersión

![[Pasted image 20260819093148.png]]

---

## 🔐 Seguridad en Dispersión

| Aspecto | Detalle |
|---------|---------|
| **3DS** | Pasa por el sitio padre |
| **OTP** | Pasa por el padre |
| **Hijas** | No tienen interacción directa con filtro de seguridad |
| **MerchanID** | Las hijas usan el del padre (MerchanID 0) |

> [!NOTE]
> Lo que hace 3DS es una **autenticación** más no un traslado de responsabilidad.

---

## ⚠️ Estados de Transacciones

| Escenario | Resultado |
|-----------|-----------|
| 1ra declina | Las demás se rechazan (se cierra el flujo) |
| 1ra aprueba, 2da rechaza | **Pago parcial** → 3ra se rechaza |
| 1ra y 2da aprueban, 3ra rechaza | **Pago parcial** |
| Se queda pendiente | Esperando a la red — si 1ra se resuelve y 2da en pendiente → **pago parcial** + estado `Pending Process` |

> [!TIP]
> El comercio decide cómo manejarlo:
> - Reversos fallidos → revisarlos
> - Aprobados parciales → poner como rechazado
> - Pending Process → tarde o temprano se resuelven

---

## 🔗 Documentación Relacionada

| Documento | Enlace |
|-----------|--------|
| Dispersión principal | [[PRODUCTOS/Dispersión/Dispersión]] |
| Aerolíneas | [[PRODUCTOS/Dispersión/DISPERSION AEROLINEAS]] |
| Modificadores de pago | [[PRODUCTOS/Dispersión/DISPERSION MODIFICADORES DE PAGO]] |
| Webhook | [[General/Webhook]] |
| Sonda | [[General/Sonda]] |
