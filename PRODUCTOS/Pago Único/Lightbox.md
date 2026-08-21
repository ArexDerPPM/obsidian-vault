# 💡 Lightbox — Pago sin Redirección

**Lightbox** es una forma de integrar el Checkout que permite a los usuarios completar el pago **sin salir de la página del comercio**. Aparece de forma dinámica en el centro de la pantalla.

> 📖 Documentación oficial: [https://docs.placetopay.dev/checkout/lightbox/](https://docs.placetopay.dev/checkout/lightbox/)

---

## ⚙️ Funcionamiento

![[Recursos/assets/imagen-15.png|847]]

1. Se crea la sesión de pago normalmente
2. Se abre el checkout en modal **Lightbox**
3. El usuario completa el pago sin salir del sitio

---

## 🔙 Backup Target (Fallback)

Si el navegador no es compatible con Lightbox, se puede configurar una acción de respaldo:

![[Recursos/assets/imagen-16.png]]

Configuración de **backupTarget**:

![[Recursos/assets/imagen-18.png]]

### Tipos de apertura

| Tipo | Comportamiento |
|------|----------------|
| **Lightbox** | Modal centrado en la misma página |
| **Popup** | Abre una nueva pestaña/ventana (depende del navegador). Mismo comportamiento que Lightbox |
| **Self** | Redirección en la misma ventana |
| **Blank** | Similar a Self, pero el navegador lo asocia al mismo proceso anterior — al cerrar obtiene una respuesta |

---

## ⚠️ Safari y Compatibilidad

En **Safari** pueden ocurrir errores y Lightbox no se abre, cayendo en una redirección normal.

> [!TIP]
> La extensión **UserAgent Switch** permite cambiar el user-agent del navegador para probar distintos escenarios.

---

## 🔐 3DS y CSP

### 3D Secure
Al habilitar **3DS** en ambiente de prueba, se puede validar si la política del comercio genera fricción. Si aplica, el 3DS puede no levantarse.

### Content Security Policy (CSP)
Si el comercio aplica políticas CSP, debe habilitar los dominios del país:

- `placetopay.com`
- `placetopay.ec`

![[Recursos/assets/imagen-17.png]]

Esto permite utilizar los recursos y scripts desde los dominios de PlacetoPay.

---

## 🔗 Notificación

> ⚠️ La notificación debe estar en **SHA-256**.

El `returnUrl` debe capturarse correctamente para identificar el resultado de la transacción al cerrar el Lightbox.

---

## 🆚 Comparación: Lightbox vs Redirección

| Aspecto | Lightbox | Redirección |
|---------|----------|-------------|
| Experiencia | El usuario no sale del sitio | El usuario es redirigido a PlacetoPay |
| Compatibilidad | Puede fallar en Safari | Funciona en todos los navegadores |
| Return | Callback automático | Redirección a `returnUrl` |
| Implementación | Requiere widget JS | Solo URL |

## ℹ️ Checklist_ 2026

[[Checklist_WC_pago_basico_2026.pdf| Ver Checklist]]