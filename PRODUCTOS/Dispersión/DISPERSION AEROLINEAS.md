# ✈️ Dispersión — Aerolíneas

> [!INFO] Notas de práctica
> Guía detallada sobre la dispersión de **aerolíneas**: configuración, transacciones, adquirentes y flujos de seguridad.

> **Relacionado:** [[PRODUCTOS/Dispersión/Dispersión|Dispersión]], [[PRODUCTOS/Dispersión/DISPERSIÓN _1|Tipos de Dispersión]]

---

## 🔑 Conceptos Clave

- Podemos tener la transacción de la **aerolínea** o del **MERCH** (merchant)
- En transacciones de aerolínea, la transacción más importante es la de la **aerolínea**
- Los **filtros de seguridad** van a pertenecer al **sitio padre**
- Siempre se debe validar que los flujos van en **PIPELINE** — si una falla, se declina todo el proceso

---

## 📋 Estados Posibles

| Escenario | Resultado |
|-----------|-----------|
| Alguna falla | **Decline** — se rechaza todo |
| Unas hijas no pasaron | **Pago Parcial** |

---

## 📊 Listado de Aerolíneas Activas

![[Pasted image 20260827101521.png]]

![[Pasted image 20260827101531.png]]

> [!IMPORTANT]
> Pedir a las líderes si tienen el archivo de lo mismo.

Tenemos hojas de: **Activas**, **Inactivas**, **Pruebas**

![[Pasted image 20260827101639.png]]

Las que tienen **SI** tienen **forwarding**.

![[Pasted image 20260827101604.png]]

Al final tenemos la columna de sus **adquirentes principales**.

---

## 🔄 Ejemplo de Consumo — Sitio EGM Dispersion

![[Pasted image 20260827102551.png]]

### Sitio padre con NULL (cobra)

Cuando el `agreement` tiene **NULL** → el sitio padre va a cobrar.

![[Pasted image 20260827102859.png]]

Los sitios **1406** y **1407** son los sitios 2 y 3.

> [!WARNING]
> Si llega a existir un mal cálculo, **no nos dejará hacer la dispersión**.

![[Pasted image 20260827103024.png]]

---

## 💳 Proceso de Débitos

Cuando se va a cobrar la tarjeta, por detrás tiene el proceso de **débitos** de las transacciones dispersadas: padre, hijo, hijo.

> [!NOTE]
> No es mandatorio que estos sitios estén atados entre sí — pueden ser de **distintos comercios**.

### De cara a la transacción

![[Pasted image 20260827103222.png]]

### Información interna de las hijas

![[Pasted image 20260827103432.png]]

> Con el `RequestId` consumiendo el `GetRequestInformation`, vemos la info de la transacción.
> **SIEMPRE TOMAR EL ESTATUS INICIAL** ya que es el de la transacción al culminar el flujo de pago.

### Niveles de dispersión

Dentro de la consulta, la respuesta se subdivide en los niveles: **PADRE → HIJO → HIJO**.

La transacción padre es quien agrupa a las demás:
![[Pasted image 20260827103825.png]]

> [!TIP]
> En transacciones de dispersión, si uno busca por la referencia puede ver más referencias. Lo que debemos hacer es que sea **dentro de dispersión**.

![[Pasted image 20260827103930.png]]

---

## 🔄 Flujo sin Cobro del Padre

El otro escenario es donde el sitio padre **no cobra** — solo es un paso a los hijos.

![[Pasted image 20260827104448.png]]

Ya no va `null` — se mandan los ID de los hijos. El sitio padre no cobra.

![[Pasted image 20260827104617.png]]

> Al buscar la transacción, se ve el campo **sitio PADRE** y el **sitio principal** por el que se transaccionó pero **no se cobró**.

---

## ✈️ Transacción de Aerolínea

### Requisitos
Los comercios deben tener **IATA** en sus configuraciones.

### Pasos

1. Seleccionar la aerolínea del Excel:
![[Pasted image 20260827104818.png]]

2. Configurar:
![[Pasted image 20260827105036.png]]

3. Generar el flujo y pagar la dispersión
4. **Revisar bien los montos** en caso de errores para que se genere correctamente

### Configuración de 3DS en Aerolíneas

El 3DS se levanta directamente en la configuración de aerolíneas.

En el dashboard → **CONFIGURACIONES** → campo **AEROLINEAS**:

![[Pasted image 20260827105245.png]]

![[Pasted image 20260827105206.png]]

Ejemplo: aerolínea **33** → **COPA IATA** → método de pago Visa → adquirente Visa con token de 3DS:

![[Pasted image 20260827105331.png]]

---

## 🔗 Documentación Relacionada

| Documento | Enlace |
|-----------|--------|
| Dispersión principal | [[PRODUCTOS/Dispersión/Dispersión]] |
| Tipos de dispersión | [[PRODUCTOS/Dispersión/DISPERSIÓN _1]] |
| Modificadores de pago | [[PRODUCTOS/Dispersión/DISPERSION MODIFICADORES DE PAGO]] |
| Autenticación | [[Autenticación]] |
