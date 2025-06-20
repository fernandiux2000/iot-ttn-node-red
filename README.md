# iot-ttn-node-red
Proyecto IoT: Monitor de Clima Simulado y Real usando Node-RED, MySQL y OpenWeather API

Este proyecto fue desarrollado como parte de la Especialización en IoT (UBA), para la asignatura Principios y Aplicaciones para dispositivos LoRa/LoRaWAN.

Descripción general del proyecto

El objetivo es simular un escenario real de monitoreo IoT basado en tecnologías LoRa/LoRaWAN, donde dispositivos remotos envían datos ambientales al backend de procesamiento, almacenamiento y visualización de datos.

Este sistema integra:

Simulación de dispositivos LoRa generando datos aleatorios de temperatura y humedad.

Adquisición de datos reales a través de la API pública del proveedor meteorológico OpenWeather.

Almacenamiento centralizado en base de datos MySQL.

Visualización en tiempo real mediante el dashboard de Node-RED.

Arquitectura completamente contenerizada mediante Docker.

Componentes principales

Node-RED

Plataforma de desarrollo visual basada en flujos.

Orquestación de adquisición, procesamiento y almacenamiento de datos.

Visualización en tiempo real de los datos adquiridos.

MySQL

Motor de base de datos relacional.

Almacena los registros históricos de temperatura y humedad.

phpMyAdmin

Interfaz gráfica de administración de la base de datos MySQL.

OpenWeather API

OpenWeather (https://openweathermap.org/) es un servicio web global que proporciona datos meteorológicos actualizados en tiempo real.

Ofrece una amplia gama de parámetros climáticos: temperatura, humedad, presión, velocidad del viento, nubosidad, pronóstico, etc.

Se utilizó su API REST pública para obtener los datos de temperatura y humedad de la ciudad configurada (ejemplo: Quito, Ecuador).

La API se consume mediante solicitudes HTTP desde Node-RED, y devuelve respuestas en formato JSON.

El acceso requiere registrarse gratuitamente en el sitio web de OpenWeather para obtener una clave de API personal.

Estructura de archivos del repositorio

docker-compose.yml — Archivo para desplegar el sistema completo usando Docker.

flujos-node-red.json — Exportación de los flujos de Node-RED (tanto simulados como datos reales desde OpenWeather).

Instrucciones de despliegue

1️⃣ Clonar el repositorio:

git clone https://github.com/TU_USUARIO/iot-ttn-node-red.git
cd iot-ttn-node-red

2️⃣ Levantar los contenedores Docker:

docker-compose up -d

3️⃣ Acceder a los servicios:

Node-RED: http://localhost:1880

phpMyAdmin: http://localhost:8080

4️⃣ Importar los flujos en Node-RED:

Ingresar a Node-RED.

Importar el archivo flujos-node-red.json para cargar el proyecto.

5️⃣ Configurar la API Key de OpenWeather:

En el flujo Datos Clima API, editar el nodo que prepara la URL de la solicitud HTTP.

Reemplazar el marcador TU_API_KEY por la clave personal obtenida al registrarse en OpenWeather (https://openweathermap.org/api).

Modelo de la base de datos MySQL

Tabla única: sensor_data

Campos:

id: Clave primaria (autoincremental)

dev_id: Origen del dato (simulado o openweather)

temperature: Temperatura medida (°C)

humidity: Humedad relativa (%)

timestamp: Fecha y hora de la medición

Objetivos pedagógicos alcanzados

Integración de múltiples tecnologías IoT.

Simulación realista de sensores LoRa.

Consumo de APIs REST públicas externas.

Persistencia de datos en almacenamiento relacional.

Desarrollo de dashboards visuales para monitoreo en tiempo real.

Implementación de arquitectura contenerizada y portátil.

Asignatura

Principios y Aplicaciones para dispositivos LoRa/LoRaWAN — Especialización en IoT — Universidad de Buenos Aires

Autor

Rodrigo Morocho
