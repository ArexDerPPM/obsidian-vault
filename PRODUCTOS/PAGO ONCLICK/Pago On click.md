# ⚡ Pago On Click — Pago Rápido con Tarjeta Guardada

> [!IMPORTANT] Requisito: Autenticación
> Para implementar Pago On Click es **obligatorio** autenticarse con **Login** y **SecretKey**.
> → [[Autenticación|Ver documentación completa de Autenticación]]

> **Relacionado:** [[PRODUCTOS/Suscripción/Suscripción|Suscripción]], [[PRODUCTOS/Pago Único/Pago Único|Pago Único]]

---

## 🔑 Concepto

El **Pago On Click** es un pago rápido similar a **Rappi**, **Amazon** o la **wallet de PlacetoPay**. El usuario tiene su tarjeta guardada y puede pagar en un solo clic.

> [!NOTE]
> Se debe habilitar el **WALLET** dentro del dashboard de PlacetoPay.

---

## 📋 Diferencia: Pago On Click vs Recurrencia

| Aspecto | Pago On Click | Recurrencia |
|---------|---------------|-------------|
| **Usuario** | **Presente** | No presente |
| **Modelo** | Pago rápido | Cargo consecutivo |
| **Concurrencia** | No hay | Sí hay |
| **Ejemplo** | Rappi, Amazon | Netflix, membresías |

Dentro de modelos de recurrencia: Netflix, Rappi, membresías — se cobra mensualmente y el usuario no está presente. En Pago On Click, el usuario **sí está presente**.

---

## 📦 Modelo SUBSCRIBE: TRUE

> [!WARNING] Modelo flexible (no disponible en Ecuador aún)
> Este modelo da la posibilidad de que, al momento de pagar, también se **suscriba** esa tarjeta.

### Características

| Aspecto | Detalle |
|---------|---------|
| **Flexibilidad** | Depende del usuario si guarda o no la tarjeta |
| **Validación** | No permite validar modelo de membresía |
| **Flujo** | Si el usuario no guarda, solo se realiza un cobro |
| **Tokenización** | Se debe habilitar el proceso para guardar como token |

### Flujo

1. Cobro inicial (`collect`)
2. En el `information` se trae el **token** para hacer los otros collects

> [!TIP]
> Es para comercios que ofrezcan un plus para guardar la tarjeta. En el flujo de [[PRODUCTOS/Suscripción/Suscripción|Suscripción]] es más controlado.

---

## 📋 Consideraciones

- Es un modelo aplicado a un **pago onclick** pero también como recurrencia, siempre y cuando el comercio de la claridad o administre bien
- Algunos comercios requieren hacer el tema de **cuotas**
- Revisar la información para ver las cuotas de una tarjeta ingresada

---

## 🔗 Documentación Relacionada

| Documento | Enlace |
|-----------|--------|
| Suscripción | [[PRODUCTOS/Suscripción/Suscripción]] |
| Pago Único | [[PRODUCTOS/Pago Único/Pago Único]] |
| API | [[PRODUCTOS/API/API]] |
| Webhook | [[General/Webhook]] |
| Sonda | [[General/Sonda]] |
