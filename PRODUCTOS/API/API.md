# 🔌 API — Integración Avanzada

> [!IMPORTANT] Requisito: Autenticación
> Para consumir la API es **obligatorio** autenticarse con **Login** y **SecretKey**.
> → [[Autenticación|Ver documentación completa de Autenticación]]

> [!WARNING] Integración más compleja
> La integración por **API** es la más compleja en Ecuador dado que se consumen una gran cantidad de métodos y se debe seguir una línea de puntos que deben cumplirse, sino la integración queda mal.

---

## 📋 Características Principales

- **Certificación del banco**: Se pasan por dos revisiones
- **PCI obligatorio**: Todos los comercios certificados por API deben ser PCI (cualquier nivel es aceptado)
- **Costos altos**: Algunos comercios no quieren realizar esta integración por el costo
- **Trazabilidad**: Los request deben tener la misma trazabilidad a nivel de consumos
- **Responsabilidad del flujo**: El comercio hace el recaudo y tiene la responsabilidad del flujo

> [!WARNING] Referencia constante
> Si en el `information` se mantiene una referencia, esa se debe mantener en el resto de consumos. **NO** se debe cambiar el monto (ej: de $10 a $50) porque da un mal servicio al comercio.

---

## 🔑 Conceptos Clave

| Concepto | Descripción |
|----------|-------------|
| **Payer** | El pagador, dueño de la tarjeta |
| **Buyer** | El dueño de la cuenta |
| **Information** | Primer paso: consulta de tipos de crédito, 3DS, OTP, intereses, CVV |
| **Process** | Proceso de la transacción |
| **OTP** | One-Time Password para validación |
| **3DS** | 3-Domain Secure para autenticación |
| **Luhn** | Algoritmo para validar si una tarjeta es verdadera (booleano) |

---

## 🔄 Flujo Básico de API

### 1. Information Request
Consulta los tipos de crédito y si se requiere:
- 3DS / OTP
- Intereses
- CVV (siempre requerido en Ecuador)

### 2. Proceso según resultado

| Requiere | Acción |
|----------|--------|
| **3DS** | Se levanta el desafío de autenticación |
| **OTP** | Se genera el OTP para validación |
| **Intereses** | Se calculan los intereses (solo Diners) |
| **Ninguno** | Se procede directo al process |

> [!NOTE]
> Si requiere **3DS**, no va a requerir **OTP** — es una u otra.

### 3. Process
Se envía la firma al `process` para completar la transacción. Sin la firma es una transacción no segura y se declina.

---

## 📸 Ejemplo Visual — Flujo Completo

### Flujo con 3DS
![[Pasted image 20260819103439.png]]

### Cálculo de intereses
![[Pasted image 20260819103903.png]]

### OTP Generate → Process
![[Pasted image 20260819104149.png]]

![[Pasted image 20260819104245.png]]

![[Pasted image 20260819104252.png]]

### Transacción completada
Verificar en dashboard → Reglas Hours para confirmar que la validación fue exitosa.

---

## ⚠️ Casos Especiales

### DEUNA
- DEUNA es un medio de pago que **no funciona sin la descripción de pago**
- La información del **payer** es esencial porque es quien va al final de cuentas (dueño de la tarjeta)
- Se debe enviar la **IP del tarjetahabiente** y el **userAgent** según documentación

### Intereses (Diners)
- Solo aplica para tarjetas **Diners**
- En otras redes **NO** se habilitan
- A nivel **Interdin** sí está habilitado
- Al tercer intento el banco bloquea y se debe hacer el flujo nuevamente

### IFRAME
- Si se levanta en un IFRAME, verificar las políticas de **CSP** (Content Security Policy)
- No deben ser tan deliberadamente bloqueantes
- Compartir la documentación de [[PRODUCTOS/Pago Único/Lightbox|Lightbox]]

---

## 🔗 Trazabilidad

> [!WARNING] MUY IMPORTANTE
> Un solo cambio de un número genera un **signature** muy distinto. La transacción declina porque se vincula a la referencia de pago, y si es distinto falla.

![[Pasted image 20260819104616.png]]

---

## 📚 Documentación Relacionada

| Documento | Enlace |
|-----------|--------|
| Consumo de API (ejemplos) | [[PRODUCTOS/API/Consumo API]] |
| Caso Fybecca | [[PRODUCTOS/API/API Consumo caso Fybecca]] |
| Autenticación | [[Autenticación]] |
| Webhook | [[General/Webhook]] |
| Sonda | [[General/Sonda]] |
| Documentación oficial | [docs.placetopay.dev](https://docs.placetopay.dev/) |
