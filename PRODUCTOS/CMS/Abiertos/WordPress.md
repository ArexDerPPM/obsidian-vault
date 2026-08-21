# 📖 WordPress + WooCommerce — CMS Abierto

> [!IMPORTANT] Requisito: Autenticación
> Para que el plugin funcione, el comercio debe configurar las credenciales **Login** y **SecretKey** en el panel de administración. Sin esto, no opera ningún producto.
> → [[Autenticación|Ver documentación completa de Autenticación]]

Dentro de la configuración de **WooCommerce** con PlacetoPay, tenemos el plugin oficial que permite integrar la pasarela de pagos.

> 📥 **Descarga:** [Plugin PlacetoPay para WooCommerce](https://docs.placetopay.dev/checkout/plugins/)

---

## 📦 Instalación

1. Descargar el plugin desde el enlace oficial
2. Verificar la **versión de WordPress** (7 u 8) para elegir la distribución correcta
3. Instalar el plugin en WordPress
4. Configurar las credenciales

---

## ⚙️ Configuración

### Credenciales
- **Login** — Usuario de PlacetoPay
- **SecretKey** — Clave secreta de PlacetoPay
- **País** — Seleccionar el país del comercio
- **Tiempo de sesión** — Duración de la sesión de pago
- **Ambiente** — `Test` o `Producción`

### Configuración de Impuestos (IVA Ecuador)
1. Ir a **WooCommerce → Impuestos**
2. Crear un impuesto **Estándar** con **15%**
3. Marcar la sección de **Envío**
4. Asignar el impuesto a los productos correspondientes

---

## 🔧 Personalización (CMS Abierto)

Al ser un **CMS abierto**, se pueden generar cambios a nivel de código:

- Modificar el template del checkout
- Agregar campos personalizados
- Cambiar estilos del formulario de pago
- Personalizar la respuesta post-pago

---

## 🔗 Webhook

El [[General/Webhook|Webhook]] ya viene desarrollado en el plugin. Se puede visualizar mediante:

1. Activar el **modo debug** en WordPress
2. Revisar los logs para identificar el endpoint del webhook

> 🡒 [[General/Webhook|Ver documentación de Webhook]]

---

## 🔄 Sonda

La [[General/Sonda|Sonda]] es una **tarea programada** que se debe configurar a nivel de hosting:

- Buscar **"Schedulers"** o **"Cron Jobs"** en el panel de hosting
- Configurar el intervalo (en test: cada **5-10 minutos**)
- Apuntar al script de la sonda del plugin

> 🡒 [[General/Sonda|Ver documentación de Sonda]]

---

## ⚠️ Incompatibilidades Conocidas

Al trabajar con múltiples plugins, pueden existir conflictos:

| Plugin | Conflicto |
|--------|-----------|
| **Elementor** | Permite modificar el checkout — puede romper el flujo de pago |
| **Wompi** | Realiza conversión de monedas — puede interferir con montos |
| **WP Builder (WPBakery)** | Modifica el checkout — puede ocasionar incompatibilidad |

> [!TIP]
> El comercio debe hacer los ajustes necesarios para que los plugins funcionen en armonía, o desactivar el que cause conflicto con la pasarela.


---------
## 🔧 PROCESO DE LLENADO DE IVA

Se habilita el proceso del IVA dentro de las configuraciones del administrador del sitio de Wordpress

WooCommerce --> Ajustes --> check en Activar Impuestos

![[Recursos/assets/Pasted image 20260729123134.png]] 

Luego nos dirigimos a la seccion de Impuestos para la configuracion respectiva
![[Recursos/assets/Pasted image 20260729123411.png]]

![[Recursos/assets/Pasted image 20260729123649.png]]

Posteriormente vamos a configurar el valor del 15% a ser usado en el impuesto del producto.

Tenemos tarifa estandar
Tarifa Cero: Es para casos donde no se aplica impuestos a algun producto
Tarifa reducida

Tarifa estandar  y su configuración
![[Recursos/assets/Pasted image 20260729123954.png|1204]]

