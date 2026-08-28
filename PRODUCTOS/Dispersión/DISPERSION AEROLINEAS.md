
Podemos tener la transaccion de la aerolina o del MERCH
puede ir una u otra, en las transacciones de aerolina  la transaccion mas importante es la de la aerolinea.

Los filtros de seguridad van a pertenecer al sitio padre.

Siempre se debe validar que los flujos van en PIPELINE y si una falla, se declina todo el proceso de pago.

Nos puede dar un declino y si alguna falla y nos da un Pago Parcial  dado que unas hijas no pasaron 

LISTADO DE AEROLINAS ACTIVAS
![[Pasted image 20260827101521.png]]

![[Pasted image 20260827101531.png]]

pedir a las lideres si tienen el archivo de lo mismo
(IMPORTANTEEEE)
_sdsd_

![[Pasted image 20260827101604.png]]
al final tenemoss la columna de sus adquirentes principales

tenemos HOJAS DE: Activas, Inactivas, Pruebas

![[Pasted image 20260827101639.png]]

Estas dos que tienen SI, tienen forwarding

_Pruebas de cONSUMOS DE CONSUMO AEROLINEA_


EJEMPLO DE SITIO:  egm disper

![[Pasted image 20260827102551.png]]

Cuando el agremmet tiene NULL quiere decir que el sitio padre va a cobrar
![[Pasted image 20260827102859.png]]

de alli vienen los otros sitio 
1406 y 1407 que son los sitio 2 y 3 

si hacemos el calculo vemos que nos debe dar el valor total 
![[Pasted image 20260827103024.png]]

Si llega a existir un mal calculo no nos dejara hacer la disperison

Cuando se va a cobrar la tarjeta por detras tiene el proceso de debitos  de las transacciones dispersadas, padre, hijo, hijo.

Importante no es Mandatorio que estos sitios esten atados entre si, pueden ser de distintos comercios

De cara a transaccion se ve asi:
![[Pasted image 20260827103222.png]]

podemos ver nterna de las hijas informacion de las transaccion padre: 
![[Pasted image 20260827103432.png]]

con el RequestId  consumiendo el GetRequestInformation, vemos la info de la transaccion 
SIEMRE TOMAR EL ESTATUS INICIAL YA QUE ES EL DE LA TRANSACCION AL CULMINAR el flujo de apgo

dentro de la misma consulta tenemos la respuesta y se va a subdividir en los niveles de las dispersiones, en este caso hay 3 niveles de dispersión porque es PADRE, HIJO, HIJO

tenemos una particularidad, al entrar a la transaccion padre es quien agrupa a las demas dentro del dash podemos ver esa informacion 

![[Pasted image 20260827103825.png]]

En las transaccion de dispersion si uno busca por la referencia puede ver mas referencias.
Lo que debemos hacer es que sea dentro de dispersion 
![[Pasted image 20260827103930.png]]


Ahora un flujo con el que no cobra el padre, solo es un paso a los hijos.

El otro escenario es donde el sitio padre no cobra, y mandamos los id de los hijos , es decri ya no va null

![[Pasted image 20260827104448.png]]
Y el flujo es el mismo  pero el sitio padre el que colocamos las credenciales pues no cobra.
solo tenemos 2,3,4 y deja de exisitir el cobro del sitio padre

![[Pasted image 20260827104617.png]]

Si entro en las transacciones yo busco su sitio padre, y tengo el campo sitio PADRE Y TENGO EL SITIO PRINCIPAL POR EL QUE SE TRANSACCIONO PERO NO SE COBRO.

--------------
UNA TRANSACCION DE AEROLINEA HACEMOS DE LA SIGUIENTE MANERA: 

Es necesario que los comercios tengan IATA en sus configuraciones

![[Pasted image 20260827104753.png]]

![[Pasted image 20260827104808.png]]

seleccionamos la aerolina del excel 
![[Pasted image 20260827104818.png]]

![[Pasted image 20260827105036.png]]

genero mi flujo y pago mi dispersion de aerolineas, revisar bien los montos en caso de errores. para que se genere correctamente el flujo de transaccion

a nivel de qeu se levnate 3DS en aerolineas directamente en la configuracion de aerolineas

En el dash arte izquierda vamos a CONFIGURACIONES y al campo AEROLINEAS
![[Pasted image 20260827105245.png]]

![[Pasted image 20260827105206.png]]


en este caso la 33 vemos que COPA IATA, y abrimos el metodo de pago visa, el adquitente visa vemos que tiene token de 3ds

![[Pasted image 20260827105331.png]]

.-------
