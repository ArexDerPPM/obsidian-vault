
Todos los comercios de PVA si solicitan  van a tener el card-return

les va a agregar en el response un campo que se marca como PAN que es un cifrado a nivel de sitio, ningun otro comercio lo puede solicitar, solo PVA com otal, aunq existen excepciones

En general este flujo vamos a tener que en las transacciones de PVA hay dos particularidad.

GDS --> Administran los portales de vuelo 

el numero de la tarjeta va asociada  a la emision de un vuelo, en estos flujos se ve la necesidad de ver la tarjeta para atar el TICKET

DIRECTO: En el caso de tarjeta de tercero: la tarjeta del usuario es basicamente cuando va a realizar un proceso de pago normalito. CUnado es con la informacion del usuario

INDIRECTO:  Tendriamos que es con una tarjeta corporativa no es necesaria este metodo.

ESTO. esim portante para los flujos de dispersion, se lo habilita de la siguiente forma 

![[Pasted image 20260911101538.png]]

UN  campo que dice retorno de tarjeta
![[Pasted image 20260911101553.png]]

y se genera el cifrado 
![[Pasted image 20260911101600.png]]

aqui lo que tendriamos  ahora con el pan desiframos 
![[Pasted image 20260911101640.png]]


CREAMOS UNA TRANSACCION DE AEROLINEA dentro de PVA de usuarios y corporativo y ver el flujo de dispersion.

![[Pasted image 20260911101841.png]]
![[Pasted image 20260911101933.png]]

la base no  imponible no graba impuestos y es un FEE .... IMPORTANTE ESTE DETALLE

![[Pasted image 20260911102242.png]]

si solo hubiese hcho la de ticket aero solo tendria dos, la dispersion me indica que agrupa las transacciones de dispersion.
estas son las originales, es decir transacciones padre y agrupan el flujo por quie transacciono, y  la base no imponible la aeroportuaria va dentro de base no imponible, lo importante de dispersion es que se garantice que el iva y la base imponible coincidan.


ESTA DOCUMENTACION VAMOS A VER TICKETES. y es obligatorio para todas las integraciones de dispersion en Ecuador, con esto se van a hacer los procesos buscar, crear, remover.

![[Pasted image 20260911102718.png]]

-----
el prefijo IATA DE CADA AEROLINA ES :
![[Pasted image 20260911102832.png]]

son generalmente los primeros caracteres
lo unico que hace el comercio es ingresar el ticket, el cual tiene 10 digitos y le da la fecha de emision de hoy 
![[Pasted image 20260911102914.png]]

y consume el endpoint de consumir el iata 
![[Pasted image 20260911102927.png]]
lo que hizo es consumir el endpoitn de 
![[Pasted image 20260911102948.png]]
![[Pasted image 20260911102952.png]]


Dependiendo de la cantidad de transacciones con el endpoint de reporteria sin la  necesidad del panel admiistrativo



NOTIFIYER: Entrega mas informacion, y tiene un contato establecido, entrega mas info pero el tema es que cambia la respuesta, si el comercio maneja una url de notificacion debe hacer un cambio en su endpoint para recibir esta informacion.
