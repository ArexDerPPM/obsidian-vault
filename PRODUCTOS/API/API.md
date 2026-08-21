Dentro del contexto de esta integracion es la mas compleja en Ecuador dado qeu se consumen una gran cantidad de metodos, y se debe seguir una linea de puntos se deben cumplir sino la integración queda mal.

A si nivel exisite tambien una certificación del banco, ya que se pasan por dos revisiones

Todos los comercios certificados por API , deben ser PCI sino no se pueden certificar. (cualquier nivel es aceptado)

Los costos de esta integración son muy altos y algunos comercios ya no o quieren realizar aveces

Importnate que los request tengan la misma trazabilidad, a nivel de los consumos.

PEDIR EL DIAGRAMA DE API 
Mpi/lookup el query, process , entre otros como reversos.

Esta integracion permite que el comercio haga el recaudo y el comercio tiene la responsabilidad del flujo.

Que si en el information mande una referencia esa la debo mantener en el resto de consumos 

ejemplo de 10$ en el otro paso a 50$ ESO NO SE DEBE HACER porque da un mal servicio a nivel del comercio.

Toda ese flujo desde el information hasta el process sea un flujo correcto y no existan cambios en las tramas

Debemos decirle a los comercios que se verificaran los logs de su flujo

Si hace mal un flujo de OTP, es decir  no va a funcionar en producción, todo afecta al flujo transaccional

![[Pasted image 20260819102237.png]]

EJEMPLO ALGUNOS COMERCIOS COMO FYBECCA
en el mismo boton tienen la opcion de guardar la tarjeta para que e mantenga la misma experienca de usuario y se identificara los flujos que se pueden dar.



SI ES POR PAGO BASICO
Entonces vamos a tener todos los metodos de api, PERO NO TENEMOS EL TOKENAIS
	Usuario llena la info de la tarjeta
		El usurio debe tener su validación de la tarjeta, implementanto el algoritmo de LUM el cual permite validar si la tarjeta es verdadera o no .
		Fubnciona como un booleano
		Se debe hacer una validacion de la tarjeta (dado que el CVV en amex 4 digitos, minimo 3 digitos)

Lo mas importante aqui en API, es el "pagador" --> PAYER  
Buyer : dueño de la cuenta
Payer: el pagador dueño de la tarjeta

1.- Vamos a hacer un informationRequest vamos a ver los tipos de credito y si se requiere 3ds, otp, intereses y se requiere el CVV, es rara la tarjeta que no. (en eCUADOR TODAS REQUEREN CVV)


Todas las tarjetas propias de dINERS ESAS PIDEN INTERESES, EL OTP es de Dinners y van a solicitar OTP, para 3ds es un servicio mas general (es global)

el flujo de3DS
el OTP: 
intereses
cvv siempre true
![[Pasted image 20260819103439.png]]

en esta foto es y pasa por 3DS
Si requiere 3DS no va  requerir OTP , o es una  u Otra
A continuacion otro ejemplo: 
![[Pasted image 20260819103726.png]]
y ahora vamos al siguiente paso que es intereses seria el segundo metodo
![[Pasted image 20260819103903.png]]

luego ya pasamos al OTP generate
Y en forwardin8LUEGO LO VEMOS 
![[Pasted image 20260819104149.png]]

![[Pasted image 20260819104245.png]]
![[Pasted image 20260819104252.png]]

Y SE COMPLETA LA TRANSACCION

a nivel de dash debemos ver en Reglas hours podemos ver si la validacion fue exitosa 


Muy imprtante la trasabilidad, solo un cambio de un numero tengo un signature muy distinto al , la transaccion declina por que la transaccion se vincula a la referencia de pago, y si es distinto falla 
![[Pasted image 20260819104616.png]]

Lo mismo va a nivel de 3DS 

	.... PEDIR DOCUMNTACION DE API por el tema del comercio de DLOCAL necesitan ver temas de sus transacciones y ams info del proceso api


DEUNA es un medio de pago que no funciona sin la descripcion de pago para este caso, 
la informacion del payer ES ESCENCIAL porque es quien aoga al final de cuntas , es el dueño de la tarjeta

Se debe mandar la IP del tarjetaviente y del userAgent y se debe enviar lo que esta en la documentación.

En el interes es importante para hacer el cobro 
![[Pasted image 20260819105233.png]]

este solo para diners,  
EN  CAMBIO EN LAS OTRAS REDES NO SE VAN A HABILITAR, pero a ivel interdin si esta habilitado

al tercer intento el banco me bloquea y debo hacer el flujo nuevamente.
Aqui descripcion es opcional en API

Si se levanta en un IFRAME ver el tema de las politicas de CSP, no deben de ser tan deliberadamente bloqueantes y compartir la documentacion de ligthbox


/// revisar 
cuando es query 
debo enviar el query, debo redireccionar revisar lo final

![[Pasted image 20260819110653.png]]

DE QUI EL INTERES ES LO MISMO QUE OTP,