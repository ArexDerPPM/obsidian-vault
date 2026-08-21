
Una sesión de dispersión es una sesión en la cual el monto total del pago será dividido en diferentes destinos.

Para usar este tipo de sesión, debes enviar la propiedad `payment.dispersion` que contiene un arreglo de `DispersionRequests`


![[Recursos/assets/Pasted image 20260812101939.png]]

Tenemos 3 tipos de dispersion en Ecuador

1.- PVA --> a aerolineas
2.-  Comercio --> van a poder cobrar, se distribuye el monto entre diferentes cuentas
3.- Modificador de Pago (Dispersión de merchans) --> misma particularidad pero aqui se controlada directamente desde el panel
 - - - - -
Al momnto de crear la sesion se crea la sesion padre de tipo **DISPERSION** que contiene el valor total de la transaccion y el estado general del proceso y tambien por sesiones hijas de tipo  **AUTH_ONLY** que contiene la informacion de cada ua de las partes de dispersadas. Los datosde autorizacion y recibo de transaccion padre seran los mismos que la promera transaccion procesada

INICIA EL FLUJO ---> Filtro de seguridad  (Del sitio padre)
                    Datos de Control (sitio hijo)
	                    Datos de control (sitio hijo)
		                    Datos de control (sitio hijo)

Se pueden realizar hasta máximo 3 dispersiones contando al sitio padre para cualquiera de los tres tipos de dispersiones.

Tambien tenemos que la dispersión puede darse de dos flujos:

1.- En el que el sitio padre cobra
2.- El sitio padre o cobra

Dentro de una tienda grande tenemos tiendas internas entonces modelo aplica a la dispersion de merchans, yo como tienda tengo interno 3 sitioscomercios, falavela, marathon, totto cada una de estas va a recibir lo que el usuario compro en cada una, el sitio padre aqui es el encargado de dispersar pero no cobrar 

![[Pasted image 20260819093148.png]]

 // particularidades en aerolinas :Depende de como esta configurado esa aeroline
En este caso cuando pasa por 3DS con el del sitio padre
							OTP con el del padre

Las hijas no tiene interaccion directa con n filtro de seguridad, ya que todo pasa por el inicial MerchanID 0, el del padre.
A nivel de seguridad bajo este modelo cuando cobra se asegura el monto de comision que cobra el sitio padre, cuando no se cobra y hay un fraude no se asegura ningun cobro.

Las transacciones entran en contracargo y no hay responsabilidad como tal.

TEMAS DE FRAUDE:, (PREGUNTAR)
![[Pasted image 20260819093754.png]]

Lo que hace 3DS es una autentificacion mas no un traslado de responsabilidad.

Que ocurre si una de las transacciones se rechaza las demas  se rechazan porque si la primera declino entonces las posteriores no van a la red ya que se cierra.

Otro caso cuando  pasa la primera transaccion y la seguda se rechaza entocnes tenemos un aprobado parcial y por consiguiente declina la tercera.

Igual cuando la 1ra y 2da se aprueba y la tercera se rechaza es un aprobado parcial.

Si esta se queda pendiente siempre se queda esperando a la red, si la primera se resuelve pero la segunda en pendiente ---> esto a nivel de Dispersion se genera un pago parcial y otro estado que puede tener Pending Process entonces si la primera queda pendiente las otras quedan con este estado transitorio

El comercio decide como lo va a manejar, si los refersos quedan fallidos deben revisarlos, y los aprobados parciales ponerlo como rechazado., y las de pending process tarde o temprano se deben resolver.


---------------
## DISPERSIONES DE AEROLINEA

Quien maneja la seguridad es siempre la aerolinea, estas tienen su particularidad en donde las transacciones quedan de cra a la aerolinea la transacción mas cara o de mayor valor.

Tenemos una transacción de cara : AEROLINEA  y MERCHANT  son transacciones de transacciones aisladas, dentro del as mismas solo puedo cobrar una o solo cobrar otra.

Algunas agencias de viaje haen su propio flujo interno, en donde existe alguna tarifa administrativa en donde gana la agencia de viaje.
En este modelo va a existir un sitio padre pero no es dueño de los filtros de seguridad sino es propio de la aerolina y es quien levanta el 3DS, el sitio (DASHboard) sirve de intercomunicación para asociar la transaccion padre a la aerolinea y cobrar mi monto de trnasaccion (MERCHANT)

pueden ser solo la Aerolinea  o el merchant o ambas, nunca puede ser la transaccion mayor a 2, 

Si AIR prueba -- Merch aprueba
Si Air Rechaza -- Merch rechaza
Si Air aprueba --- Merch Rechaza  ---> aqui tengo un Pago parcial

(AL INICIO ALGO CONFUSO PERO CON LA PRACTICA YA QUEDA MAS CLARO EL PROCESO)

![[Pasted image 20260819095440.png]]

Un caso particular es que a nivel de las aerolineas quien levanta los tipos de credito tambien son las aerolineas.

Quien levantaba el 3DS la aerolina.
Quien levanta los tipos de credito de la Aerolineas los levanta ellos mismos.

Yo para ver los tipos de credito tengo  hacer una solicitud de dispersion de la aerolinea, a ivel de mERCHAN   aveces no asoman estos tipos de credito

Aqui en estem odelo de Aerolinea se preoriza los mismos medios de pago. diners, Amex, discover, visa, mastercard , estas deben estar tanto en el AIR --MERCH sino no va a funcionar , lo mismo para los tipos de credito, o el Merchan no tener tipos de credito para no tener friccion.

Del sitio padre se muestran los tipos de credito (todo es con la aerolinea)



