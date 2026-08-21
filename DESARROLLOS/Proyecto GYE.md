# 🏙️ Proyecto GYE — Landing de Pagos SEP / Prediales

> [!INFO] Contexto
> Notas del proyecto de pagos del **municipio de Guayaquil (GYE)**: landing para pagos de **prediales** y **SEP**.

---

## 🧭 Resumen

- Aplicativo desarrollado hace años en **Pagos Digitales** por **Jaime Mejía**; está desplegado en los servidores mediante **Bitbucket**.
- Empezó como una **landing page** que permite a los usuarios hacer sus pagos.
- El **CÓDIGO SEP** se genera como una orden de pago de los usuarios.
- Tiene dos raíces: **prediales** o **SEP**, que van casi a lo mismo; en el SEP se consulta el código SEP.

---

## 🔄 Flujo de pago

### 🏛️ Integración con el municipio

- Se cuenta con un **web service tipo SOAP** de servicios.
- Cualquier cambio que va a hacer el municipio nos informa y ellos hacen los cambios.
- El municipio devuelve los **valores a pagar** y el usuario decide si paga o no.
- El pago se redirige a **PlacetoPay** en los diferentes estados: notificación, sonda, lightbox (las políticas van en los iframes del lightbox).

### ✅ Asentamiento (settlement)

1. Una vez que el pago es **aprobado**, se informa a GYE mediante un **servicio de asentamiento** y se espera una respuesta del municipio.
2. Cualquier respuesta **distinta a `00`** significa que no se pudo hacer la transacción.
3. A los **6 minutos** se vuelve a consumir el método de asentamiento y se espera una respuesta: a veces devuelve `OK`, en otros casos regresa un error.
4. Como se hizo un reintento y no se asentó la transacción, se consume el **reverso** para **reversar la transacción**: de cara a P2P tiene el pago y el cliente tiene la afectación; por eso se reversa y finaliza el proceso.

Aplica igual para **SEP** como para **prediales**.

| Respuesta del municipio | Significado |
|-------------------------|-------------|
| `00` | `OK` — transacción asentada |
| Distinto de `00` | No se pudo realizar la transacción |

### ⏱️ Ventana de reverso

- P2P indica que cuando una transacción se autoriza y se queda bloqueada un tiempo, dentro de esos minutos **no puede ser reversada**.
- Por eso se realizó un desarrollo para **aumentar el tiempo a 6 minutos** (se aumentó el passkey) y se pasó a producción con pruebas y monitoreo; todo funciona correctamente.
- **Antecedente:** no estaba claro si P2P hizo algo en sus reversos; devolvió `REJECTED` y, al no ser reversada, al usuario le quedaba como **aprobada**, pero en el municipio no se asentaba.

---

## 📅 Fechas de compensación

| Momento | Fecha de compensación |
|---------|-----------------------|
| Transacciones antes de las **4:00 pm** | Mismo día |
| Posterior a las **4:00 pm** | Día siguiente |
| Viernes (posterior a las 4:00 pm) | Lunes de la siguiente semana |
| Con feriado (ej: 10 de agosto) | Se corre al siguiente día hábil (ej: martes) |

---

## 👤 Administración

- La parte administrativa está llevada por **Diners**: registran los **feriados** (ej: 10 de agosto) y sirve para que el municipio de GYE maneje sus horas de cierre.
- Se entrega usuario y contraseña a **Diners** para que ellos hagan la administración, incluidos los procesos de la landing.

---

## 📊 Monitoreo e incidentes

- Con acceso a la BD **MG PAGOS** se ven los pagos entrantes, los asentamientos, etc., para monitoreo; Diners también lo hace a nivel de requerimientos.
- **Diagnóstico:** si una transacción no se realizó o no se reversó, entrar a **AWS CloudWatch** y revisar los **logs** de las transacciones para ver el viaje de la transacción y verificar el error existente.
- Si hay un **error grave**: toca un **desarrollo** (brief → desarrollo → planificar el paso a **staging** y **producción**), lo cual lleva su tiempo.
  - **Preguntar a James (Jaime)** en caso de que sea algo grande.

---

## 🚀 Despliegue

- El repositorio en PPM tiene **3 ramas**: `produ`, `staging` y `master` (todo se trabaja en staging y luego el PR a master siempre son iguales).
- Con un **requerimiento nuevo**:
  1. Generar una rama con el **nombre del ticket** (clon de master)
  2. Hacer PR a **staging**
  3. El equipo ayuda a hacer el **pull**
  4. Con PPM se sube el cambio
  5. Validar con el cliente que todo esté bien
  6. Pasar a **producción**

---

## 🛠️ Arquitectura

- **Symfony** está en desarrollo en toda la arquitectura.
- Dentro del código hay un **command que se ejecuta cada minuto**: si un asentamiento falló, lo vuelve a ejecutar a los **6 minutos**.

---

> [!NOTE] Pendiente
> Validar si el flujo está correcto y, si se da el incidente, identificar qué está pasando.
