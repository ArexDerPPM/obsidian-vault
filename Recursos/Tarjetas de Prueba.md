# 💳 Tarjetas de Prueba

Tarjetas de prueba oficiales para simular transacciones en el ambiente de **test** de PlacetoPay.

> 📖 Documentación oficial: [https://docs.placetopay.dev/gateway/testing-card/](https://docs.placetopay.dev/gateway/testing-card/)

---

## 🏦 Tarjetas Visa

| Marca | Número | Estado |
|-------|--------|--------|
| Visa | `4111111111111111` | Aprobada |
| Visa | `4012001037141112` | Aprobada |
| Visa | `4012001038443335` | Rechazada |

## 🏦 Tarjetas Mastercard

| Marca | Número | Estado |
|-------|--------|--------|
| Mastercard | `5555555555554444` | Aprobada |
| Mastercard | `5200828282828210` | Aprobada |

## 🏦 Tarjetas American Express

| Marca | Número | Estado |
|-------|--------|--------|
| American Express | `378282246310005` | Aprobada |

---

## ℹ️ Uso

1. Configurar el plugin en modo **Test**
2. Usar los números de tarjeta en el checkout
3. Verificar el resultado según el estado esperado

> [!TIP]
> Los CVV y fechas de expiración pueden ser cualquier valor válido (ej: CVV `123`, fecha futura).
