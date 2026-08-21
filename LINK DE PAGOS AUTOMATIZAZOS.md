CASABACA --> INICIO

Para la parte de integración la documentación la tenemos:

1ro  vamos a revisar la 
La autenticacion
debemos crear un token de JWT  -- un BEAR token , este token se refresca  cada 4 horas. Y se necesita volver a loger y asi volver a generar los links de pago, ya qeu de la parte del front o web P2P manda esto de manera cifrada, con esto la  API la debe procesar.

El cifrado mencionado es mediante un algoritmo el cual se envia en las cabeceras los datos para tratar.

Lo que hacen es mandar cifrado y el comercio en este caso ustedes mandan los datos cifrados.

Deben tener en cuenta que para crear los LINKs siempre deben ser un usuario VENDEDOR. ya que el usuario comercio O SUPER-ADMIN  tiene otros roles.

VENDEDOR --> Quien crea los links de pago.

En la documentación esta  esta el proceso del flujo.

De lado de P2P se puede hablar con seguridad para ver si se puede ampliar los tiempos como tal de las sesiones.

	Bendo Link de pagos tiene una plataforma como tal, en este caso es el consumo del API

Aqui tambien tenemos historicos en caso desen ver en base a un cliente.

Los usuarios de P2P debemos crear en el sistema de BENDO.
Se lo puede hacer cada que el usuario ingtrese y se lo puede hacer y cada vez que realicen pues  el proceso de M2F de doble autenticación.

Dentro de las APIS esta una para generar el flujo y otra para  validar toda la informacion del pago el flujo del proceso

En bendo llega todo el flujo y si quieren mas informacion del pago pueden revisar mediante el consumo del API del historico.

CASABACA--> Toda la informacion del cliente  puedan alimentar en base a los campos que les llega de parte de Bendo.


BENDO MANDA COMO DATA DE LAS TRANSACCIONES -->  Dentro de la documentación se envia varios datos en la trama en funcion a lo enviado podemos ver varios atriburtos de la transaccion y su deartamentio puede mapearlo en base a lo que necesita.

Los reversos son por parte de placetopay y son inmediatos
En BENDO. no tenemos el endpoint de reverso, lo que se hace es consumir el endpoint de placetopay (o mediante el dashboard PREGUNTAR)

Para continuar con el proceso, como se van a hacer en el ambiento de prueba, es necesario que nos envien las ip para que les den acceso para que realicen las pruebas en nuestro ambiente.






