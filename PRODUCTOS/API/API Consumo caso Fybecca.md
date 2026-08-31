# 🛍️ API Consumo — Caso Fybecca

> [!INFO] Caso de estudio
> Análisis del flujo de integración API del comercio **Fybecca**. Incluye el nuevo protocolo **3RI** y los flujos de tokenización.

---

## 🔑 Contexto

- **Fybecca** es un comercio que tiene la opción de guardar tarjeta para mantener la misma experiencia de usuario
- Se está implementando el nuevo protocolo **3RI** (validación de seguridad transparente de cara al usuario)
- Este método funciona bajo el flujo donde se agrega una tarjeta o cuando el comercio quiere tener la tarjeta para una recurrencia

---

## 📋 Tipos de Recurrencia

| Tipo | Descripción |
|------|-------------|
| **Mes vencido** | Tokenizo hoy pero el cobro empieza después (ej: meses de cortesía) |
| **Cobro inmediato** | Más claro, tipo pólizas/seguros — aplica desde que el usuario se suscribe |

> **Relacionado:** [[PRODUCTOS/PAGO ONCLICK/Pago On click|Pago On Click]], [[PRODUCTOS/Suscripción/Suscripción|Suscripción]]

---

## 🔄 Flujo 1 — Checkout con Guardado de Tarjeta

A nivel del checkout se puede guardar la tarjeta.

> [!IMPORTANT]
> Para mostrar las cuotas, el comercio en el `information` debe enviar un **payment** para que se muestren los créditos.

![[Pasted image 20260821101701.png]]

![[Pasted image 20260821101706.png]]

### Configuración del flujo

![[Pasted image 20260821101721.png]]

### Con payment vs sin payment

**Sin payment** (suscripción) — no muestra cuotas:
![[Pasted image 20260821102251.png]]

**Con payment** — muestra cuotas y créditos:
![[Pasted image 20260821102229.png]]

---

## 🔐 Flujo OTP

Cuando es **OTP** se puede hacer de cualquiera de las dos formas.

> [!WARNING]
> Es necesario que se envíe el `payment` para mostrar los tipos de crédito, y correspondería el `interestCalculation`.

### Generación de OTP → Tokenización

1. Generamos el OTP
2. Mandamos el objeto `otp generate` en la validación
3. El `tokenize` de 3DS cumple la función de validar la seguridad de la tarjeta

> [!NOTE]
> En los flujos de pago de suscripción, el OTP **nunca** se valida bajo `OTP validate`, sino bajo el `tokenize` de 3DS.

![[Pasted image 20260821102948.png]]

Error cuando se envía mal el OTP:
![[Pasted image 20260821103001.png]]

> [!WARNING]
> Aquí es donde se rompe el código del comercio, dado el nivel de mensajería ya que no revisan este escenario. Si el comercio restringe y no tiene un `instrument`, esto lo verificamos a nivel de certificación.

---

## 🔄 Flujo 2 — Agregar Nuevas Tarjetas (desde "Mis Tarjetas")

Desde "Mis tarjetas" se tiene la posibilidad de agregar nuevas tarjetas.

> [!IMPORTANT]
> Se requiere un cobro mínimo de **$1** que se reversa.

![[Pasted image 20260821102040.png]]

Se hace la validación por OTP o 3DS — este sería el flujo ideal para una **tokenización**.

![[Pasted image 20260824084735.png]]

> El objeto `subscription` sella toda la trazabilidad.

---

## 📊 Flujo 3 — Mostrar Cuotas

![[Pasted image 20260824084815.png]]

> [!IMPORTANT]
> Si o si debo enviar el `payment` y usar el `information`.

![[Pasted image 20260824084927.png]]

Esto se hace para ver las cuotas, y se puede hacer mediante una suscripción:
![[Pasted image 20260824085106.png]]

> **MANTENER LA MISMA REFERENCIA** en todo el flujo.

---

## 🔍 Identificación de Tokenización

![[Pasted image 20260824092659.png]]

| Campo | Significado |
|-------|-------------|
| `tokenizationID` | Indica si se envió el CVV |
| **Y** | Se envió CVV |
| **N** | No se envió CVV |

**Con CVV:**
![[Pasted image 20260824092821.png]]

**Sin CVV:**
![[Pasted image 20260824092808.png]]

---

## 🔐 Flujo 3DS en Fybecca

Para un flujo de 3DS en Fybecca se puede hacer:
- Con `information` + `payment` (si se necesitan cuotas)
- Solo con `subscription` (si no se necesitan cuotas)

> [!TIP] Recomendación P2P
> Desde P2P se recomienda que el flujo de pago se haga con una transacción de **3DS NPA (No Payment Autenticación)**.

> [!WARNING]
> Esto tiene un gran índice de **DECLINACIÓN** dado que los bancos restringen esto. Lo que debemos hacer es enviar como un flujo normal con un monto.

![[Pasted image 20260824093145.png]]

### Flujo post-autenticación

![[Pasted image 20260824093938.png]]

> En el `payment` debemos enviar la dispersión para ver quién es el responsable de la autenticación de 3DS.

---

## 📚 Recomendación

> [!TIP]
> Los ejemplos de la colección de **Postman** están más centralizados para un mejor entendimiento de los comercios.

---

## 🔗 Documentación Relacionada

| Documento | Enlace |
|-----------|--------|
| API principal | [[PRODUCTOS/API/API]] |
| Consumo API | [[PRODUCTOS/API/Consumo API]] |
| Pago OnClick | [[PRODUCTOS/PAGO ONCLICK/Pago On click]] |
| Suscripción | [[PRODUCTOS/Suscripción/Suscripción]] |
| Autenticación | [[Autenticación]] |
