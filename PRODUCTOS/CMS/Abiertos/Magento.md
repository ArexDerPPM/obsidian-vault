# 🏗️ Magento — CMS Abierto

> [!IMPORTANT] Requisito: Autenticación
> La configuración del plugin requiere las credenciales **Login** y **SecretKey**. Sin autenticación no es posible transaccionar.
> → [[Autenticación|Ver documentación completa de Autenticación]]

**Magento** es un CMS abierto enfocado para desarrolladores. Todo se maneja por código mediante **Composer**.

---

## 📥 Instalación

> [!IMPORTANT]
> Se recomienda instalar desde **Git** directamente, ya que desde los componentes de descarga de PlacetoPay a veces no se descargan bien las librerías y archivos.

![[Recursos/assets/imagen-14.png]]

![[Recursos/assets/imagen-07.png]]

Proceso:
1. Clonar/descargar el plugin desde el repositorio oficial
2. Instalar mediante **Composer**
3. Configurar las credenciales desde el panel de administración

> Esto mismo se encuentra en la documentación de GIT del plugin.

---

## ⚙️ Configuración del Plugin

### Paso 1: Acceder a la configuración

![[Recursos/assets/imagen-03.png]]

### Paso 2: Ir a Stores → Configuration

![[Recursos/assets/imagen-04.png]]

### Paso 3: Store Information

![[Recursos/assets/imagen-05.png]]

### Paso 4: Configuración de PlacetoPay

![[Recursos/assets/imagen-08.png]]

Se despliegan varios apartados a modificar:

![[Recursos/assets/imagen-22.png]]

### Campos de Configuración

![[Recursos/assets/imagen-13.png]]

![[Recursos/assets/imagen-21.png]]

**Campos principales:**

| Campo | Descripción |
|-------|-------------|
| **Login** | Usuario de PlacetoPay |
| **SecretKey** | Clave secreta |
| **Número de Documento** | RUT/NIT de la empresa |
| **Tiempo de expiración** | Tiempo estimado de la transacción |

![[Recursos/assets/imagen-09.png]]

![[Recursos/assets/imagen-26.png]]
![[Recursos/assets/imagen-25.png]]
![[Recursos/assets/imagen-24.png]]

Login de producción:

![[Recursos/assets/imagen-28.png]]

### Medios de Pago

Desde la configuración se pueden controlar los medios de pago (`paymentMethod`):
- `IN_VS` — Interdin Visa
- `MT_VS` — Mastercard
- `DF_VS` — Datafast
- etc.

![[Recursos/assets/imagen-12.png]]

### Configuración de Ordenes

![[Recursos/assets/imagen-10.png]]

### Correo Electrónico de Confirmación

![[Recursos/assets/imagen-27.png]]

---

## 👁️ Visualización de Órdenes Pendientes

Por defecto, Magento no muestra las órdenes en estado **Pendiente/Pending**. Para visualizarlas se deben realizar ajustes en la ruta de procesos.

![[Recursos/assets/imagen-01.png]]

> Magento solo muestra pedidos aprobados o rechazados — por eso es necesaria esta configuración.

---

## 📋 Configuración Adicional (Producción)

Si se ejecuta Magento en **modo producción**, se debe **compilar y desplegar** los archivos:

![[Recursos/assets/imagen-23.png|528]]

---

## 🔄 Sonda en Magento

> En Magento la sonda **no tiene URL directa**. Está embebida en los **crontab** de Magento y se ejecuta automáticamente.

La sonda se encuentra en los procesos de **Job de Magento**:
1. Ir al directorio de Magento
2. Ejecutar el **CRON RUN**
3. Buscar el proceso de PlacetoPay
4. El comercio puede configurar los parámetros desde ese cron

> 🡒 [[General/Sonda|Ver documentación general de Sonda]]
