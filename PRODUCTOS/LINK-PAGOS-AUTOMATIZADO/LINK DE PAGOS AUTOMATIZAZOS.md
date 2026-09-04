# 🔗 Link de Pagos Automatizado — Integración Bendo

> [!IMPORTANT] Requisito: Autenticación JWT
> Para esta integración se necesita crear un **token JWT** (Bearer Token) que se refresca cada **4 horas**.  Y se deben volver a logear y no expire la sesion.(refresh token)


---

## 🔑 Autenticación

| Campo | Descripción |
|-------|-------------|
| **Token JWT** | Bearer Token — se refresca cada 4 horas |
| **Cifrado** | Algoritmo que se envía en las cabeceras para tratar los datos |
| **Rol requerido** | **VENDEDOR** — el usuario comercio o super-admin tiene otros roles |

> [!WARNING]
> Para crear los links, siempre se debe ser un usuario **VENDEDOR**.



---

## 📋 Flujo General

1. El frontend/web de PlacetoPay manda los datos **cifrados**(comercio)
2. La API de Bendo procesa los datos
3. Se generan los links de pago
4. Bendo envía la información de las transacciones

### Plataforma Bendo

- Bendo Link de Pagos tiene una **plataforma** como tal — en este caso es el consumo del **API**
- Hay **históricos** en caso de querer ver información base a un cliente
- Los usuarios de P2P se deben crear en el **sistema de Bendo**
- Se puede hacer cada vez que el usuario ingrese, con proceso **M2F de doble autenticación**

---

## 📡 Endpoints

| Endpoint | Función |
|----------|---------|
| **Generar flujo** | Crea el link de pago |
| **Validar información** | Valida toda la información del pago y el flujo del proceso |

---

## 📊 Datos de Transacciones

Bendo manda como data de las transacciones varios atributos. Dentro de la documentación se envían varios datos en la trama — en función a lo enviado podemos ver varios atributos que el departamento puede mapear según lo que necesita.

---

## 🔄 Reversos

> [!WARNING]
> En **BENDO** no tenemos el endpoint de reverso. Lo que se hace es consumir el endpoint de **PlacetoPay** (o mediante el dashboard — **preguntar**).

Los reversos son por parte de PlacetoPay y son **inmediatos**.

---

## 🧪 Ambiente de Pruebas

> [!IMPORTANT]
> Para continuar con el proceso en el ambiente de prueba, es necesario que nos envíen las **IPs** para que les den acceso y realicen las pruebas en nuestro ambiente.

---

## 📚 Capacitación

> Este documento corresponde a la capacitación técnica del **Link de Pagos** (JV / JV).

---



iMPOETANTE LAS SESIONES SE LOS VALIDA POR OTP Y SON ENVIADOS POR NUESTRO PORVEEDOR DE MENSAJERIA  MAILGUN, LOS USUARIOS VENDEDORES VAN A PODER HACER LA CREACION DE LINKS


