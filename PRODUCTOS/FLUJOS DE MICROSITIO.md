
MICROSITIO CREACION 
![[Pasted image 20260914102646.png]]

HaY 3 tipos de micrositio:
1.-cerrado: Se le da al usuario la opcion de funcionar con orden de pago /donde el usuario puede pagar mediante una orden de pago de cierta forma el sitio personalizado es lo mismo. como cuando pagamos la matricula vehicualr en ecuador(TURNO DE LICENCIA)
2.-abierto: Aquí el usuario entra a seleccionar lo que va a comprar y va a pagar.
3.-personalizado (1 o 2 campos)

Esto en Ecuador no hay en ambiente de test. Solo el flujo de micrositio esta dado en producción.

Click to Pay es un flujo que esta atado a un token request (esto no hay en Ecuadro importante)


-------
aqui hay un contrato y unas conecciones , desarrollo, smtp. Para el sitio cerrado crea las ordenes mediante una API a placetopay pra que hagan los pagos, o automatizan el proceso de excel para enviar al micrositio y enviara aPlacetopay.

Personalizado tiene la adaptabilidad de un contrato, cada que el usuario ingresa el nombre de referencia

![[Pasted image 20260914103435.png]]

aqui se puede dar por JWT o oauth para el acceso del mismo, y con este token tiene la info par las autenticaciones.


CERRADO: CONSUME API DE PLACETOPAY
ABIERTO: LA CONECCION SE DA POR UN CONTRATO QUE ESTABLECE COMO TAL .(min 23)
PERSONALIZADO: 1 O 2 CAMPOS de lo que vendria siendo datos del comercio.


---------



En ECUADOR los sitios de micrositio estan dados en producción.
![[Pasted image 20261012091301.png]]

los dos checkboxs aun no estan en Ecuador, el logo alado de VISA es el de Clock to Pay, el cual depende de que el adquirente soporte el flujo de pago.
En Ecuador no hay token request.

------
MICROSITIO CERRADO
Es en el cual el usuario pueda pagar mendiente este flujo es con una orden de pago. haciendo un simil es similar a uno personalizado. (Documento, referencia)

El comercio va a crear unas ordenes de pago mediante una API, o mediente un excel tienen todas las facturas y automatizan el flujo hacia PlacetoPay.

Tiene la adaptabilidad de un contrato, cada qeu el usuario ingresa la referencia/orden/factura ,

Comsume api de PlacetoPay.


---
MICROSITIO PERSONALIZADO
Solo es por uno o dos campos en donde puedo agregar varios sitios,
(Aqui se agregarian los campos) y se hace la creación de un contrato por parte de EVERTEC y llevan unas conecciones SFTP para conecciones personalizdas

Esta dado por un contrato en este contrato básicamente consume una API, los campos de respuesta del api de comercio son los que PlacetoPay les pidio implementar.

Como es por un contrato en el personalizado, se da la conexión por dos tipos de autenticacion (JWT o Oauth)

Consume un contrato con el comercio deacuerdo lo que requiera PlacetoPay.


------
Por debajo placetopay tiene anexado un sitio, en la documentación tenemos esta información (ordenes de pago)

Básicamente esta API por debajo viene a ser lo mismo que desde el panel podemos crear las ordenes de  pago.

es decir 
API (consumo )

y Desde el Dashboard
![[Pasted image 20261012092935.png]]

Los estados de las ordenes de pago son : 
![[Pasted image 20261012093010.png]]

Esta intentandp pagar y queda pendiente el estado HOLD.
