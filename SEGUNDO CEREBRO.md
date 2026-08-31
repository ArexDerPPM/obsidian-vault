# 🧠 Segundo Cerebro — Configuración del Vault

> [!INFO] Propósito
> Este vault es mi repositorio de conocimiento operativo sobre **PlacetoPay**. Aquí documento procesos, flujos de integración, notas de llamadas y configuraciones del día a día para tener todo a la mano cuando un comercio tiene una solicitud.

---

## 📋 ¿Qué es este Segundo Cerebro?

Dentro del día a día de operaciones, tenemos varios temas y algunos de ellos son más ocupados que otros. Esta colección de información la voy realizando para que, si en algún caso algo no recuerdo o se me pasa, tenerlo a la mano y poder solventar dudas respecto a solicitudes de comercios dentro del área de operaciones.

> **Estructura:** Cada producto, acción y recurso tiene su propia nota con enlaces `[[wiki]]` que permiten navegar entre documentos.

---

## 🛠️ Pasos de Configuración

### 1. Organización de la información
Crear un conjunto de información de los procesos, segmentados y separados por carpetas:
- [[PRODUCTOS/API/API|API]] — Integraciones avanzadas
- [[PRODUCTOS/Pago Único/Pago Único|Pago Único]] — Flujos básicos
- [[PRODUCTOS/Suscripción/Suscripción|Suscripción]] — Pagos recurrentes
- [[PRODUCTOS/Dispersión/Dispersión|Dispersión]] — Split payments
- [[General/Webhook|Webhook]] y [[General/Sonda|Sonda]] — Notificaciones

### 2. Plugin de Git para sincronización
Descargar el plugin de git para hacer push todos los días con la información actualizada.

### 3. Ambiente Docker para OLLAMA

```bash
docker stop open-webui && docker rm open-webui

docker run -d -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  -v "/Users/diego.rivas/Documents/OBSIDIAN/PlacetoPay-PPM/PlacetoPay":/app/backend/data/obsidian_vault \
  --name open-webui \
  --restart always \
  [ghcr.io/open-webui/open-webui:main](http://ghcr.io/open-webui/open-webui:main)
```

### 4. Ejecutar el servicio

```bash
ollama serve > /dev/null 2>&1 &
```

### 5. Conectar el vault de Obsidian con OLLAMA

**Paso 5.1** — Ir a **Espacios de Trabajo**:
![[Pasted image 20260828110623.png]]

**Paso 5.2** — Subir el conocimiento (se actualiza una vez al día vía [[General/Sonda|Sonda]] de git):
![[Pasted image 20260828110742.png]]

**Paso 5.3** — Crear un nuevo modelo:
![[Pasted image 20260828110644.png]]

![[Pasted image 20260828110712.png]]

> [!TIP]
> Con esto, al iniciar el servicio levantado, escogemos el modelo "CHUN" y podemos acceder a toda la información configurada de Obsidian.

---

## 🗂️ Navegación Rápida

| Sección | Descripción |
|---------|-------------|
| [[📋 Índice\|📋 Índice Principal]] | Mapa completo de toda la documentación |
| [[TIPOS DE PRODUCTOS]] | Tiempos de integración por producto |
| [[General/Autenticación\|🔐 Autenticación]] | Credenciales y esquema de seguridad |
| [[Recursos/Enlaces Útiles\|🔗 Enlaces Útiles]] | URLs oficiales y herramientas |
| [[Recursos/Tarjetas de Prueba\|💳 Tarjetas de Prueba]] | Datos para testing |
