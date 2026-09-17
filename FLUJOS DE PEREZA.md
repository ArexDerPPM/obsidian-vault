
MICROSITIO CREACION 
![[Pasted image 20260914102646.png]]

Hat 3 tipos de micrositio:
1.-cerrado: Se le da al usuario la opcion de funcionar con orden de pago /donde el usuario puede pagar mediante una orden de pago de cierta forma el sitio personalizado es lo mismo. como cuando pagamos la matricula vehicualr en eCUADRO(TURNO DE LICENCIA)
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

---------



