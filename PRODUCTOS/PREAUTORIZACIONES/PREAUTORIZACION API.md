# 🔐 Preautorización API — Flujo Técnico

> [!INFO] Notas de sesión
> Notas técnicas sobre el flujo de preautorización a nivel de API: retención de fondos, decrementos, 3DS y OTP.

> **Relacionado:** [[PRODUCTOS/Suscripción/Preautorización|Preautorización]], [[PRODUCTOS/PREAUTORIZACIONES/Reautorizaciones|Reautorizaciones]]

---

## 🔑 Concepto

Una **API de preautorización** nos permite **retener o reservar dinero** y siempre va a tener una **fecha de corte** (generalmente **30 días**). Si se supera este plazo, se libera el cupo.

![[Pasted image 20260824102528.png]]

---

## 📋 Caso Especial — Red Interdin

| Aspecto | Detalle |
|---------|---------|
| **Incrementos** | Hasta **6 veces** de aumento |
| **Decrementos** | **N-** a infinitos |
| **Monto cero** | Una reautorización de monto **CERO** no se puede |

---

## 🔄 Ejercicios de Flujo

![[Pasted image 20260824103646.png]]

![[Pasted image 20260824103832.png]]

> [!WARNING]
> Todas las transacciones de reautorización quedan en **PENDIENTE** hasta que se termine el flujo o expiren los 30 días y se cancelen.

![[Pasted image 20260824103858.png]]

---

## 🔐 3DS y Cobertura

> [!IMPORTANT]
> En preautorizaciones de 3DS, la **cobertura** es solo al monto inicial. Si se aumenta el valor, el excedente **no tiene cobertura**.

**Ejemplo:**
- Inicial: **$100**
- Reautorización: **$130**
- Los **$30** adicionales no tienen cobertura de contracargo

---

## 🔑 CAVV vs CVV

| Concepto | Relación |
|----------|----------|
| **CAVV** | Dato sensible que hace relación directa a **3DS** |
| **CVV** | Hace relación al **plástico** mismo de la tarjeta |

![[Pasted image 20260824104602.png]]

![[Pasted image 20260824104835.png]]

---

## 🔄 Flujo OTP

Para las validaciones de contrato, se valida:
- **Referencia** — referencia interna que sea justamente del pago
- En **dispersión** o **recurrencia**

El OTP funciona igual que el 3DS:

![[Pasted image 20260824105431.png]]

---

## ⚠️ Restricciones de Red

> [!WARNING]
> - **Solo preautorización por Interdin** — Medianet está en desarrollo
> - En producción, las únicas tarjetas habilitadas en red Interdin para preautorizaciones son las de **CRÉDITO**
> - El banco está en gestión de validar las de **débito**

> [!IMPORTANT]
> - En **3DS** NO soportan contracargos
> - En **OTP** sí aceptan contracargos en caso de fraudes

---

## 🔄 Checkout sin Reautorización

Funciona si en el checkout **sin pasar** la reautorización, pero no todos los bancos lo soportan. Otros necesitan pasar por la reautorización y luego el checkout.

---

## 🔗 Documentación Relacionada

| Documento | Enlace |
|-----------|--------|
| Preautorización | [[PRODUCTOS/Suscripción/Preautorización]] |
| Reautorizaciones | [[PRODUCTOS/PREAUTORIZACIONES/Reautorizaciones]] |
| Reverso | [[PRODUCTOS/Acciones y Consultas/Reverso]] |
| API principal | [[PRODUCTOS/API/API]] |
| Autenticación | [[Autenticación]] |
