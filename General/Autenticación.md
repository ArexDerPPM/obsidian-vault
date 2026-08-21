# 🔐 Autenticación API

Para transaccionar con PlacetoPay es necesario autenticarse mediante las credenciales **Login** y **SecretKey**.

> 📖 Documentación oficial: [https://docs.placetopay.dev/checkout/authentication/](https://docs.placetopay.dev/checkout/authentication/)

---

## 🔑 Esquema de Autenticación

### Script Postman / Pre-request

```javascript
var login = "LOGIN-COMERCIO";
var secretKey = "PASS-COMERCIO";
var date = new Date();
var seed = date.toISOString();
var nonce = btoa(seed);
var cadena = seed + seed + secretKey;

const tranKey = CryptoJS.SHA256(cadena).toString(CryptoJS.enc.Base64);

pm.collectionVariables.set("login", login);
pm.collectionVariables.set("seed", seed);
pm.collectionVariables.set("nonce", nonce);
pm.collectionVariables.set("tranKey", tranKey);
```

### Body de Autenticación

```json
{
  "auth": {
    "login": "{{login}}",
    "tranKey": "{{tranKey}}",
    "nonce": "{{nonce}}",
    "seed": "{{seed}}"
  },
  "locale": "es_EC",
  ...
}
```

> ⚠️ **Importante:** El `seed` no debe tener una diferencia mayor a **5 minutos** con la hora del servidor.

---

## 3D Secure (3DS)

**3DS** (3-Domain Secure) es un protocolo de autenticación que agrega una capa extra de seguridad a las transacciones con tarjeta de crédito/débito.

### Consideraciones

- Se evalúa **en la primera transacción** (tokenización en suscripciones).
- En ambiente de pruebas se puede validar si la política del comercio genera fricción.
- Si aplica, el 3DS puede no levantarse por conflictos de configuración.
- No es una responsabilidad a futuro, es un valor adicional en la transacción.
- Aplica políticas **CSP** (Content Security Policy) — se deben habilitar los dominios del país:
  - `placetopay.com`
  - `placetopay.ec`

### Habilitación en Pruebas

![[Recursos/assets/imagen-17.png]]

---

## OTP (One-Time Password)

**OTP** es un código de un solo uso enviado al usuario para validar transacciones de alto valor o sensibles.

> ⚠️ *Secciòn en construcción — documentación pendiente de integrar.*

---

## Consideraciones Técnicas

| Campo | Descripción |
|-------|-------------|
| `ipAddress` | Usada por la pasarela para procesos de pago, vinculada a la transacción para brindar confidencialidad |
| `userAgent` | Valor de confidencialidad asociado al dispositivo desde el que el usuario realiza la transacción |
| `locale` | Define el idioma y formato regional (`es_EC`, `en_US`, etc.) |
