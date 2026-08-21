Reuqest ID
sino por Internal Refernce
3DS y OTP de forma asilada

------ proceso de ejemplosa de API

Cuando no requiere OTP y no 3ds
![[Pasted image 20260820101559.png]]

alli va solo el information  xq todo esta en false como en la imagen : 
![[Pasted image 20260820101627.png]]

medianet, datafast, austro --> no consumen Interdin

apartr del otp validate no debe cambiar

y en el process se envia en ves del otp , debemos enviar la firma al process transaccion, sino se envia eso  es una transaccion no segura y se declina

la imofrmacion del pagador debe estar en el mpi/lookup
mpi/query  solo es de consulta, consultar la sesion que si sea, ya que consulto otra y si existe me va a salir. Aqui es importante que veamos la trazabilidad en ese caso 

en transacciones de dispersion es fundamental mandar el payment, porque es necesario este dato.

-----
![[Pasted image 20260820102621.png]]

Si no se va a guardar solo es un pago unico, se hace un onformation, tipos de credito, otp/3ds, calculodeintereses, process.

-----
el comercio tiene su wallet 
guardan las tarjetas esta opcion va a ser un information , pero no hay monto pero no es necesario que se muetre el monto, poruqe la estructura de suscripción modifica su estructura 
![[Pasted image 20260820103033.png]]

![[Pasted image 20260820103044.png]]

aqui el monto es cero y entiende el sistema que no van a existir cuotas,  pero con payment si muestra cuotas 

![[Pasted image 20260820103128.png]]

----
el usuaior maneja la wallet desde el perfil va mas acoplada en donde se envia suscripcion solamente ya que la cuota es solo una.

en el que se va a cobrar y toqquenizar
REVISAR SOBRE TOQUENIZAR Y COBRAR MINUTO 35 de la grbcion

-------
Es importante validar con el comercio, el 3ds hace solo validar al usuario en suscripcion en pago unico es distinto, Los procesos de 3ds es validar que el usuario sea quien dice ser, en  suscripcion NPA .. no paymentamount en este sentido tenemos PA paymentautenticacion cunado si tiene moto y en NPA no tienen monto, 
es decir validar el valor de 1$ que se reversa

Puede haber un reclamo de la red, decirle al comercio que la seguridad va en la tokenizacion en los cobros recurrentes ya no hay una responsabilidad, es importante ver si es NPA o PA, por temas regulatorios de ppm SE. solicita que siempre sea un cobro minimo, cuando es npa levanta el challenge par que se ingrese el otp, SI ES PA no me va a solicitar para la toquenizacion lo que vendria siendo el challenge esm inimo de 1$ coo no existe challegne puede existir un tema cronstractual cargos.

De nuestro lado es importante si se deberia de cobrar el monto minimo o ellos podian hacer la auntenticacion normal, NPA siempre va a haber un challenge por la marca, si el flujo va sin monto el consumo como lo estariamos haciendo 

en todos los flujos de pago 3DS siempre debe estar en "payer"

----
![[Pasted image 20260820104558.png]]

siemroe que/lookup sea asi no es creditos
luego el mpi

estoy en este sitio
![[Pasted image 20260820104827.png]]

![[Pasted image 20260820104834.png]]

como es de no pago el usuario ingresa la info  

![[Pasted image 20260820104912.png]]

esta info yo me llevo para la tokenizacion 
![[Pasted image 20260820105024.png]]

--------

PAgo on clic es pago rapido como rappi

.... ENTONCES EN ESTE MOMENTO PARA EL FLUJO DE PAGO  (revisar poruqe vuelve a hacer el information minuto 57)

![[Pasted image 20260820105703.png]]