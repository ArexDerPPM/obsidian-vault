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

---------------------
PARA ENTRAR A MODO DEBUG  y ver la notificacion y el CRON.

https://placetopay.dev/plugins/woocommerce

https://developer.wordpress.org/advanced-administration/debug/debug-wordpress/

![[Pasted image 20260921162540.png]]

OTRAS  NOVEDADES :

Visualizadas con el comercio de JP Digital 

![[Pasted image 20261023125514.png]]
![[Pasted image 20261023125525.png]]

El problema esta dentro de woocommerce.

el archivo dentro del plugin de placetopay
![[Pasted image 20261023125602.png]]
![[Pasted image 20261023125613.png]]
En la linea 1101
esta decimal 0, ósea es una suposición que ahí esta el error
![[Pasted image 20261023125633.png]]

![[Pasted image 20261023125652.png]]


con lo cual ya me refleja el cambio de qeu no se visualizaba las decima : 
8 ----> paso a 8,43.


---------------------
solucion al pago cuando en productivo sale hubo un error 

1. Error identificado

El sistema generaba el siguiente error fatal de PHP:

PHP Fatal error: Uncaught Error: Call to a member function add() on null

Archivo afectado:
woocommerce-gateway-placetopay-ecuador/src/GatewayMethodPlacetopayEcuador.php

Línea: 1282, dentro de la función logger().

2. Causa del problema

Al revisar el código fuente, identificamos que en la función configureEnvironment() el objeto $this->logger se inicializaba únicamente cuando el plugin estaba en modo pruebas ($this->testmode === 'yes').

Sin embargo, la función logger() también permite registrar eventos de nivel warning y error en producción.

Cuando Placetopay devolvía una respuesta de pago rechazado, el plugin intentaba registrar el evento mediante $this->logger->add(), pero el objeto no había sido inicializado, provocando el error fatal y la interrupción del proceso de retorno a WooCommerce.

3. Solución implementada

Modificamos la función configureEnvironment() para inicializar el logger de WooCommerce en todos los ambientes, tanto en pruebas como en producción:

$this->logger = self::wooCommerceVersionCompare('2.1')
    ? new \WC_Logger()
    : WC()->logger();

Esta inicialización se trasladó fuera de la condición $this->testmode === 'yes'.

Por otro lado, mantuvimos la inicialización de $this->loggerAdapter exclusivamente en modo pruebas, conservando el comportamiento original de integración con el SDK de Placetopay.

4. Resultado de la corrección

Después de aplicar el cambio, realizamos nuevamente la prueba de retorno de una transacción rechazada en producción y confirmamos que el error crítico dejó de presentarse.

La modificación permite registrar los eventos de advertencia y error sin intentar ejecutar métodos sobre un objeto nulo.

5. Recomendación

CON EL SIGUIENTE CAMBIO VEMOS EL PARCHE DEL FLUJO.


private function configureEnvironment()
{
    $environments = CountryConfig::getEndpoints();

    $nonProductionModes = [Environment::TEST, Environment::DEV, Environment::UAT];

    $this->testmode = in_array($this->enviroment_mode, $nonProductionModes, true) || (defined('WP_DEBUG') && WP_DEBUG)
        ? 'yes'
        : 'no';

    // Initialize the logger in all environments.
    $this->logger = self::wooCommerceVersionCompare('2.1')
        ? new \WC_Logger()
        : WC()->logger();

    // Keep the logger adapter only in test mode.
    if ($this->testmode === 'yes') {
        $this->loggerAdapter = new WCLoggerAdapter($this->logger, CountryConfig::CLIENT_ID);
    }

    if ($this->enviroment_mode === Environment::CUSTOM) {
        $this->uri_service = empty($this->custom_connection_url) ? null : $this->custom_connection_url;
    } else {
        $mode = $this->enviroment_mode;
        $this->uri_service = $environments[$mode] ?? $environments[Environment::TEST] ?? null;
    }
}