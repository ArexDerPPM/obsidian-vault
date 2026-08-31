# 🔓 Reautorizaciones — Incrementos y Liberación

> [!INFO] Notas de sesión (5 de agosto 2026)
> Notas detalladas sobre el flujo de **reautorizaciones**: incrementos, decrementos, liberación y casos con suscripciones.

> **Relacionado:** [[PRODUCTOS/Suscripción/Preautorización|Preautorización]], [[PRODUCTOS/Acciones y Consultas/Reverso|Reverso]]

---

## 🔑 Conceptos Clave

- Lo único que viaja son los **incrementos**
- Se simula un flujo de pago normal y finalmente se reserva un monto
- Ese monto puede verse afectado por la **variación**
- Solo se puede hacer hasta **7 reautorizaciones**
- El comercio implementa un control: si se superan **30 días**, se libera el monto

---

## 📋 Estados en el Panel

![[Recursos/assets/Pasted image 20260805102010.png]]

En PlacetoPay se muestran: preautorización, crédito, dispersión, entre otras.

> [!WARNING]
> La transacción siempre va a estar en estado **PENDIENTE** pese a que en el flujo dice **Aprobada**.

![[Recursos/assets/Pasted image 20260805102137.png]]

---

## 🔄 Flujo de Reautorización

### Requisitos de la transacción inicial
La transacción inicial de preautorización **debe pasar** por:
- **OTP** o **3DS**
- **CVV**

![[Recursos/assets/Pasted image 20260805102824.png]]

### Incrementos vs Decrementos

| Tipo | Va a la red | Efecto |
|------|-------------|--------|
| **Incrementos** | ✅ Sí | Aumenta el monto reservado |
| **Decrementos** | ❌ No | Reduce el monto (no viaja a la red) |

> [!NOTE]
> Siempre sería en la posición **0**. Al recargar se muestra la reautorización, y se tiene hasta el **5to intento** — el 6to no permite.

![[Recursos/assets/Pasted image 20260805103026.png]]

![[Recursos/assets/Pasted image 20260805103033.png]]

![[Recursos/assets/Pasted image 20260805103236.png]]

> [!TIP]
> Es potestad del comercio si maneja **aumentos**, **decrementos** o los dos.

---

## 🔓 Liberación de Fondos

Para liberar el cupo de la tarjeta:
1. Hacer un control donde el comercio libera el cupo
2. Mandar un monto con valor **0**
3. Si solo se pueden reautorizaciones mayores a cero, se debe hacer el **checkout en 0**

> [!WARNING]
> Una reautorización de monto **CERO (0)** no se puede directamente — se debe hacer mediante **Postman**.

### Ejemplo de liberación

![[Recursos/assets/Pasted image 20260805104726.png]]

Si no me deja en el panel:
![[Recursos/assets/Pasted image 20260805104928.png]]

![[Recursos/assets/Pasted image 20260805105116.png]]

### Proceso de liberación

![[Recursos/assets/Pasted image 20260805105217.png]]

![[Recursos/assets/Pasted image 20260805105254.png]]

Queda declinada bajo el motivo:
![[Recursos/assets/Pasted image 20260805105306.png]]

---

## 🔄 Suscripción con Preautorización

### Flujo de suscripción

Es tal cual al flujo de suscribirse:

![[Recursos/assets/Pasted image 20260805105436.png]]

![[Recursos/assets/Pasted image 20260805105357.png]]

> A nivel del `information` es igual y me sirve el **token**. En el Collect se hace una operación **checkin**.

![[Recursos/assets/Pasted image 20260805105547.png]]

![[Recursos/assets/Pasted image 20260805105717.png]]

- Va **sin CVV** y va bajo el origen de preautorización
- Con la referencia interna se realiza la reautorización y el checkout

---

## 🔗 Documentación Relacionada

| Documento | Enlace |
|-----------|--------|
| Preautorización | [[PRODUCTOS/Suscripción/Preautorización]] |
| Preautorización API | [[PRODUCTOS/PREAUTORIZACIONES/PREAUTORIZACION API]] |
| Reverso | [[PRODUCTOS/Acciones y Consultas/Reverso]] |
| Reembolso | [[PRODUCTOS/Acciones y Consultas/Reembolso]] |
| Suscripción | [[PRODUCTOS/Suscripción/Suscripción]] |
