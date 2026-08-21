
5 DE AGOSTO DEL 2026

Lo unico que viaja son los incrementos

Vamos a simular un flujo de pago

El flujo es el normal y finalmente reservamos un monto pero ese monto puede verse afectado por la variación.

Quedaria cubierta la tarifa inicial, aunque la versión actual unicamente la transaccion se verifica pra saber si es quien es el tarjetaviente.

Solo puedo hacer hasta 7  reautorizaciones 

Si vamos al panel vamos a ver 
![[Recursos/assets/Pasted image 20260805102010.png]]
En placetopay tenemos la preautrizacion, credito, dispersion, ente otras, se muentras por lo general las preautorizaciones, reverso, credito.

Siempre va a estar en estado PENDIENTE pese a qeu en el flujo dice Aprobada

![[Recursos/assets/Pasted image 20260805102137.png]]

Puedo tener muchas reautorizaciones, el comercio implemente un control y se superen 30 dias se libera el monto.

Para liberarlo tenemos que hacer un control en donde el comercio libera el cupo de la tarjeta mandando un monto con valor 0.

Lo que importa es el manejo de la red, es principalmente
![[Recursos/assets/Pasted image 20260805102735.png]]

que es el CAO en los flujos transaccionales?
Son 




IMPORTANTE , la transaccion inicial de preautorizacion debe pasar por  OTP o 3DS y el cvv
![[Recursos/assets/Pasted image 20260805102824.png]]

-.---- ahora hacemos ese incremento lo hacemos en LINEA van a la red ,

los decremos no va hacia la red.

![[Recursos/assets/Pasted image 20260805103026.png]]

![[Recursos/assets/Pasted image 20260805103033.png]]

Siempre seria en la posicion 0.  y si yo recargo me va a salir lo de la reautorizacion 
y luego solo tengo hastael 5 intento , el 6 intento no permite 
![[Recursos/assets/Pasted image 20260805103236.png]]

tambien es potestad  del comercio si maneja aumentos o decrementos o los dos.

aumento --> va a la red.
decrementos no va a la red.
![[Recursos/assets/Pasted image 20260805103550.png]]

Los decrementos no se tienen en cuenta, solo los incrementos ya qeu estos van a la red.

Si el comercio supera los intentos  debo ahcer un checkpout, ya es una definicion muy propia del comercio.
y lo debo hacer por el ultimo valor 


yo puedo hacer un flujo donde  va desde checkin  hasta checkout
10 ------> 15
alli puuede que se pierda, puede que se decline, siempre que hay un incremento debe hacer una reautorizacion y despues el checkout por el valor

para liberarlo hacemos el flujo normal y como vimos lo mandamos en 0 y asi se libera.



Solo se pueden reuatorizaciones mayores a cero, sino debo hacerlo el checkout en 0 
![[Recursos/assets/Pasted image 20260805104726.png]]  aqui no me deja sino lo debo hacer mediante postman.
![[Recursos/assets/Pasted image 20260805104928.png]]

![[Recursos/assets/Pasted image 20260805105116.png]]

ahora si la liberacion 
![[Recursos/assets/Pasted image 20260805105217.png]]
![[Recursos/assets/Pasted image 20260805105254.png]]

queda declina bajo el motivo 

![[Recursos/assets/Pasted image 20260805105306.png]]


ahora vamos a hacer una suscripcion con  preautorizacion

es tal cual al flujo de suscribirse:
![[Recursos/assets/Pasted image 20260805105436.png]]

 ![[Recursos/assets/Pasted image 20260805105357.png]]


A nivel del informacion es igual Y ME SIRVE EL TOKEN y en el Collect
vamos a haer una operacion checkin
![[Recursos/assets/Pasted image 20260805105547.png]]

![[Recursos/assets/Pasted image 20260805105717.png]]
va sin CVV y va bajo el origen de preautorizacion y de alli es lo mismo  con la referencia interna realizo la reautorizaicon y el checkout.

