# 📡 Consumo API — Ejemplos de Flujo

> [!INFO] Notas de sesión
> Notas detalladas sobre el consumo de la API de PlacetoPay con ejemplos prácticos de flujos.

---

## 🔑 Identificadores

| Identificador | Uso |
|---------------|-----|
| **Request ID** | Identificador de la sesión |
| **Internal Reference** | Referencia interna del comercio |

> Los 3DS y OTP se manejan de forma **aislada**.

---

## 🔄 Flujo Sin OTP ni 3DS

Cuando no requiere OTP ni 3DS, solo se envía el `information` porque todo está en `false`.

![[Pasted image 20260820101559.png]]

Ejemplo del `information`:
![[Pasted image 20260820101627.png]]

> [!NOTE]
> **Medianet**, **Datafast** y **Austro** no consumen Interdin.

---

## ⚠️ Validación OTP

- Aparte del `otp validate`, **no debe cambiar nada**
- En el `process` se envía la firma — si no se envía, es una transacción no segura y se declina
- La información del pagador debe estar en el **mpi/lookup**

---

## 🔍 Consulta de Sesión (mpi/query)

- Solo es de consulta
- Consultar la sesión que **sea la correcta** — si consulto otra y existe, va a aparecer
- Es importante ver la **trazabilidad** en ese caso

> [!IMPORTANT]
> En transacciones de dispersión es fundamental mandar el `payment` porque es necesario este dato.

![[Pasted image 20260820102621.png]]

---

## 📋 Resumen de Flujos

### Pago Único (sin guardar tarjeta)
1. `information` → tipos de crédito
2. OTP / 3DS
3. Cálculo de intereses
4. `process`

### Wallet (guardar tarjeta)
- El comercio tiene su wallet y guarda las tarjetas
- Se envía `information` pero **no hay monto** (no es necesario mostrar el monto)
- La estructura de suscripción modifica su estructura

![[Pasted image 20260820103033.png]]

![[Pasted image 20260820103044.png]]

> El monto es **cero** y el sistema entiende que no van a existir cuotas, pero con `payment` sí muestra cuotas.

![[Pasted image 20260820103128.png]]

---

## 🔄 Suscripción vs Pago OnClick

- El usuario maneja la **wallet** desde el perfil
- Se envía **suscripción** solamente (la cuota es solo una)
- Para cobrar y tokenizar, revisar la grabación (minuto 35)

---

## 🔐 3DS en Suscripción

> [!IMPORTANT] Diferencia clave
> - **3DS en pago único**: Valida que el usuario sea quien dice ser
> - **3DS en suscripción**: Se evalúa solo en la tokenización inicial
> - **PA (Payment Amount)**: Tiene monto y se valida con mínimo de $1 (se reversa)
> - **NPA (No Payment Amount)**: Sin monto, siempre levanta el challenge para OTP

> [!WARNING]
> Puede haber reclamo de la red — decirle al comercio que la seguridad va en la tokenización. En cobros recurrentes ya no hay responsabilidad.

---

## 🔑 Tokenización y 3DS

> En todos los flujos de pago 3DS siempre debe estar en **"payer"**.

![[Pasted image 20260820104558.png]]

---

## 📋 Ejemplo de Tokenización

Siempre que `lookup` sea así, no es créditos:
![[Pasted image 20260820104827.png]]

Luego el mpi:
![[Pasted image 20260820104834.png]]

Flujo de no pago — el usuario ingresa la info:
![[Pasted image 20260820104912.png]]

Info que se lleva para la tokenización:
![[Pasted image 20260820105024.png]]

---

## 🛒 Pago On Click

Es pago rápido tipo **Rappi**.

![[Pasted image 20260820105703.png]]

---

## 🔗 Documentación Relacionada

| Documento | Enlace |
|-----------|--------|
| API principal | [[PRODUCTOS/API/API]] |
| Caso Fybecca | [[PRODUCTOS/API/API Consumo caso Fybecca]] |
| Pago Único | [[PRODUCTOS/Pago Único/Pago Único]] |
| Suscripción | [[PRODUCTOS/Suscripción/Suscripción]] |
| Pago OnClick | [[PRODUCTOS/PAGO ONCLICK/Pago On click]] |
