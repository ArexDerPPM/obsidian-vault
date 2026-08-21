# 🔒 VTEX — CMS Cerrado

> [!IMPORTANT] Requisito: Autenticación
> Para conectar con PlacetoPayLATAM, el comercio debe contar con **Login** y **SecretKey** válidos.
> → [[Autenticación|Ver documentación completa de Autenticación]]

**VTEX** es un CMS cerrado donde los comercios **no pueden editar** las configuraciones de componentes externos. Al seleccionar el conector **PlacetoPayLATAM**, la configuración es fija.

> *Última actualización: 2026-07-22*

---

## 📦 Características

| Característica | Descripción |
|----------------|-------------|
| **Tipo** | CMS Cerrado |
| **Conector** | `PlacetoPayLATAM` |
| **Control de doble pago** | No aplica (no existe el mensaje) |
| **Tiempo de actualización** | 5-10 minutos |

---

## ⚙️ Configuración

1. Ir al panel de administración de VTEX
2. Buscar el **proveedor** → `PlacetoPay`
3. Seleccionar el conector **PlacetoPayLATAM**
4. La configuración se aplica automáticamente — el comercio **no puede editarla**

---

## 📊 Conciliación

VTEX proporciona información para la conciliación desde el panel administrativo:

![[Recursos/assets/imagen-19.png]]

Esta información es usada para la **conciliación de los comercios**.

### Capturas del Proceso

![[Recursos/assets/imagen-11.png]]

![[Recursos/assets/imagen-06.png]]

---

## ⏱️ Tiempo de Actualización

En algunos casos de **rechazo**, VTEX puede mostrar inicialmente "**PAGO REALIZADO**", pero luego de **5 minutos** el estado se actualiza al valor correcto.

> [!NOTE]
> Este comportamiento depende de VTEX mismo, no de PlacetoPay.

---

## 🔗 Webhook

El [[General/Webhook|Webhook]] en VTEX sigue el flujo estándar.

> 🡒 [[General/Webhook|Ver documentación de Webhook]]

---

## 🔄 Sonda

La [[General/Sonda|Sonda]] en VTEX se ejecuta cada **5-10 minutos** para actualizar los estados de pago.

> 🡒 [[General/Sonda|Ver documentación de Sonda]]
