# 🖥️ XAMPP — Entorno de Desarrollo Local

**XAMPP** es un paquete de software libre que incluye Apache, MySQL, PHP y Perl, utilizado como entorno de desarrollo local para pruebas de integración con PlacetoPay.

---

## ¿Qué es?

XAMPP permite levantar un servidor web local en tu máquina para desarrollar y probar integraciones con PlacetoPay sin necesidad de un servidor en producción.

## ¿Cómo se usa?

1. **Descargar e instalar** desde [apachefriends.org](https://www.apachefriends.org/)
2. **Iniciar los servicios:**
   - Apache (servidor web)
   - MySQL (base de datos)
3. **Ubicar los archivos del proyecto** en la carpeta `htdocs/`
4. **Acceder** desde el navegador: `http://localhost/[tu-proyecto]`

## Usos comunes con PlacetoPay

- Probar la creación de sesiones de pago en ambiente local
- Simular el flujo de [[General/Webhook|Webhook]] con herramientas como ngrok
- Configurar y probar la [[General/Sonda|Sonda]] en un entorno controlado
- Desarrollar y depurar plugins para [[PRODUCTOS/CMS/Abiertos/WordPress|WordPress]], [[PRODUCTOS/CMS/Abiertos/Magento|Magento]], etc.

> [!TIP]
> Para recibir webhooks en local, usa **ngrok** para exponer tu `localhost` a internet.
