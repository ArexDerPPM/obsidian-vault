
![[Pasted image 20260824102528.png]]

Este diagrama nos funciona mas como un flujo de diagrama 

una API PREAUTORIZACION -> Nos permite retener o reservar dinero y siempre va a tener una fecha de corte. Pero es mas una fecha en donde se libera el cupo, suele durar entre 30 días y si se supera este plazo se libera el cupo.


Preautorizacion se aplica bajo lo mismo 

CASO DE LA RED INTERDIN
Incrementos en INTERDIN. tenemos hasta 6 veces de aumento.
En Decrementos son N- a infinitos 

Una reautorizacion de monto CERO (0) no se puede.


VAMOS A HACER EJERCICIOS DE FLUJO 

![[Pasted image 20260824103646.png]]

![[Pasted image 20260824103832.png]]

Todas las transaccion des  reautorizacion quedan en pendente hasta que se temrine el flujo o expire los 30 dias y se cancela 

![[Pasted image 20260824103858.png]]

En las preautorizacion de 3ds tiene cobertura solo al monto inicial y si se aumenta el valor ya no tiene cobertura el excedente.

es decri : INICIAL : 100 
reautorizacion : 130. --> los 30$ ya no tiene cobertura de un contracargo.

una variacion de los montos de CAVV --> Es un dato sensible hace relacion directa a 3DS. 

y el CVV -> hace relacion al plastico mismo de la tarjeta.
![[Pasted image 20260824104602.png]]

![[Pasted image 20260824104835.png]]

Para las validaciones de contrato se valide la referencia, referencia interna que sea justamente del pago, y en dispersion o recurrencia.

 EN OTP funciona igual 
 y vemos el flujo de postman 
 ![[Pasted image 20260824105431.png]]


SOLO PREAUTORIZACION POR INTERDIN,  MEDIANET esta por desarrollo... tenerlo en cuenta.

Importante cuando ya van a salir a producción, las nicas tarjetas que estan habilitadas en red INTERDIN para PREAUTORIZACIONS son las TARJETAS DE CREDITO y el banco esta en gestión de validar las de debito.


!!IMPORTANTE!!
en 3DS  no soportan contracargos 
cuando es OTP  es mas que si acepten contracargos en caso de fraudes.


----- 
Funciona si en el CHECKOUT sin pasar  la reautorizacion pero no todos los bancos lo soportan , otros si o si necesitan pasar por la reautorizacion  y luego el checkout





