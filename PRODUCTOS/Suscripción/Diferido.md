# 📅 Diferido — Pagos Diferidos en Suscripciones

> [!IMPORTANT] Requisito: Autenticación
> Al ser una modalidad de [[PRODUCTOS/Suscripción/Suscripción|Suscripción]], requiere autenticación con **Login** y **SecretKey**.
> → [[Autenticación|Ver documentación completa de Autenticación]]

El pago **diferido** en suscripciones permite fraccionar el cobro de un producto o servicio en **cuotas periódicas** utilizando la tokenización de la tarjeta.

---

## 🔗 Relación con Suscripción

El diferido es una **modalidad de suscripción** donde los cobros se distribuyen en el tiempo. Funciona sobre la misma base de [[PRODUCTOS/Suscripción/Suscripción|Suscripción]]:

1. Se tokeniza la tarjeta del usuario
2. Se establece un plan de cuotas (monto, frecuencia, número de cuotas)
3. Se ejecutan los Collects según el plan establecido

---

## 📋 Ejemplo de Flujo

| Mes | Acción | Monto |
|-----|--------|-------|
| Mes 1 | Tokenización + 1er cobro | $25.00 |
| Mes 2 | 2do cobro (Collect) | $25.00 |
| Mes 3 | 3er cobro (Collect) | $25.00 |
| Mes 4 | 4to cobro (Collect) | $25.00 |
| **Total** | | **$100.00** |

---

## 💳 Redes Compatibles

> *Pendiente de especificar qué redes permiten suscripción diferida.*

---

## ⚙️ Configuración

1. Crear la [[PRODUCTOS/Suscripción/Suscripción|Suscripción]] con el payload estándar
2. Tokenizar la tarjeta
3. Programar los Collects según el plan de diferido
4. Monitorear con [[General/Webhook|Webhook]] y [[General/Sonda|Sonda]]
