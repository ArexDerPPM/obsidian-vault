En este caso vemos de manera el fljo de este comercio.

Hay un nuevo protocolo 3RI, se esta haciendo al validacionde seguridadl la cual es transparente de cara al usuario .

Este metodo funciona bajo el flujo donde agrega una tarjeta o solo cuando el comercio quiere tener la tarjeta alli para una recurencia, (puede ser a mes vencido o cobro inmediato, depende del comercio)
hay comercios que dan meses de cortesia eso aplicaria a mes vencido yo tokenizo el dia de hoy pero el cobro empieza luego de la cortesia pero ya existio una validacion de tarjeta--> BAJO EL MES VENCIDO

COBRO INMEDIARO --> Es mas claro tipo polizas seguros, aplica desde que yo me suscribo, enotnces a nivel de tokenizciones 
PAGO ON CLICK y Recurrecnias ( en este es a caso recurrente periodico, loque camvia es la periocidad del pago)


EN ESTE CASO. tiene dos distinciones 
![[Pasted image 20260821101701.png]]

![[Pasted image 20260821101706.png]]

Aqui vemos  para hacer el flujo 
![[Pasted image 20260821101721.png]]

-------

1RO FLUJO :
 A nivel del checkout puedo guardar la tarjeta 
 Aqui hay que modificar la trama para que me muestre las cuotas, el comuercio en el information debe enviarle un payment para que me muestre los creditos 
 ![[Pasted image 20260821102229.png]]
 En este caso es un  si yo cambio a suscription 
 No nos va a mostrar uuna informacion de cuotas: 
 ![[Pasted image 20260821102251.png]]
cuando pongo payment alli si tengo cuetoas.

CUANDO ES OTP lo puedo hacer de cualquier de las dos formas.
es necesario qeu se envie el payment para mostrar los tipos de credito.
y corrsponderia el interescalculation

generamos el OTP ---> luego mandamos el objeto otp generate en la validacion(pero enel diagrma yo no valido9 rompe los flujos, siempre en los fjos de pago de suscripcion nunca se valdia por el OTP validate, se hace en el mismo tkenaicen del 3DS, ese endpoint cumple la funcion de validad la seguridad de la tarjeta si hubo 3ds u otp, aqui nos dice si la tarjeta es correcta o no )

muy importante que a la generacion del OTP antener la misma referencia
![[Pasted image 20260821102948.png]]
error da cuando mando mal el otp 
![[Pasted image 20260821103001.png]]

aqui es donde se rompe el codigo del comercio, dado el nivel de mensajeria ya que no revisan este escenario, y si el comercio restringe  ya qeu no tengo un intrment, esto lo verificamos a nivel de certigficacioN.


----------

2DO FLUJO: desde mis tarjetas tengo la posubuilicsd de agregar nuevas tarjetas
Aqui es necesrio un cobro minimo de 1$ y se reversa.
![[Pasted image 20260821102040.png]]

Se hace la validación por el otp o 3ds, este seria el flujo ideal para una tokenizacion.

Aqui todo lo valida desde la suscripcion sin el monto: 
![[Pasted image 20260824084735.png]]

aqui en donde el objeto suscription sellava toda la trazabilidad

--------
Otro flujo es  mostrar las cuotas: 
![[Pasted image 20260824084815.png]]

Si o si debo enviar el payment y usar el information 
![[Pasted image 20260824084927.png]]

Eso lo hago para ver las cuota, aqui lo puedo hacer mediante  una suscripcion  (MANTENER LA MISMA REFERENCIA)
![[Pasted image 20260824085106.png]]

Resulta que a nivel de flujo  tenemos varias formas de ocuparlo Con el otp generado -(lo estamos haciendo como suscripcion)

otp generate (simpre en los flujos de pago de suscripción el otp nunca se valida bajo el OTP validate, sino bajo el tokenize de 3ds, cumple la funcion de validar la seguridad de la tarjeta), esto nos va decir si es correcta o no .

 -----------
Como identificamos una transaccion de tokenizacion 
![[Pasted image 20260824092659.png]]
Este atributo a nivel de pago es un tokenizationID con la cual podemos ver su se envio el cvv o no 
como se envio me da una Y 

CON CVV
![[Pasted image 20260824092821.png]]


SIN CVV
![[Pasted image 20260824092808.png]]

------
AHORA PARA UN FLUJO DE 3DS en el caso de FYBECCA lo podemos hacer con el information con el payment, o si no es necesario als cuotas las hacemos solo con el suscripcion.

Desde P2P recomendamos que el flujo de pago se haga con una transaccion de 3DS NPA (No payment  Autenticacion)

importante: esto tiene un gran indice de DECLINACION, dado que los bancos  restringen esto.
Lo que debemos hacer es enviar como un flujo normal con un monto.
![[Pasted image 20260824093145.png]]


luego que el usuario se autentica seguimos la trasabilidad y srguimos el flujo 

![[Pasted image 20260824093938.png]]


en el payment debemos enviar el dispersión para ver quien es el responsable de la autenticación de 3DS.

.... RECOMENDACION LOS EJEMPLOS DE LA COLECCION DE POSTMAN  estan mas centralizados para un mejor entendimiento de los comercios.





