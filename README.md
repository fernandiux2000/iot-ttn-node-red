# iot-ttn-node-red
Proyecto IoT: Monitor de Clima Simulado y Real usando Node-RED, MySQL y OpenWeather API

Este proyecto fue desarrollado como parte de la Especialización en IoT (UBA), dentro de la asignatura Principios y Aplicaciones para dispositivos LoRa/LoRaWAN.

🎯 Descripción general del proyecto:

El proyecto implementa una solución de monitoreo de clima simulando un sistema IoT basado en tecnología LoRa/LoRaWAN, donde:

Se generan datos simulados de sensores de temperatura y humedad, como si provinieran de dispositivos LoRa.

Se adquieren datos reales de clima utilizando la API pública de OpenWeather.

Los datos son almacenados en una base de datos MySQL.

Los resultados son visualizados en tiempo real en el Dashboard de Node-RED.

Toda la arquitectura es fácilmente desplegable mediante Docker.

🧱 Tecnologías utilizadas

Node-RED:
Plataforma de desarrollo visual para orquestación de flujos IoT.

MySQL:
Base de datos relacional para almacenamiento persistente de registros históricos.

phpMyAdmin:
Interfaz web para administración de la base de datos.

OpenWeather API:
Servicio web global de datos meteorológicos actualizados en tiempo real.
Sitio web oficial: https://openweathermap.org/

Docker:
Contenerización completa del sistema para simplificar su despliegue multiplataforma.

📂 Estructura del repositorio
docker-compose.yml → Despliegue automatizado de todo el sistema.

flujos-node-red.json → Exportación completa de los flujos de Node-RED para simulado y API.

🚀 Instrucciones de despliegue:

1️⃣ Clonar el repositorio:

git clone https://github.com/TU_USUARIO/iot-ttn-node-red.git

cd iot-ttn-node-red

2️⃣ Crear la base de datos y usuario MySQL manualmente

Nombre de la base de datos: lorawan_data
Usuario: iotuser
Contraseña: iotpass

Sentencias SQL para crear la base de datos y tabla:

CREATE DATABASE lorawan_data;

CREATE USER 'iotuser'@'%' IDENTIFIED BY 'iotpass';
GRANT ALL PRIVILEGES ON lorawan_data.* TO 'iotuser'@'%';
FLUSH PRIVILEGES;

USE lorawan_data;

CREATE TABLE sensor_data (
  id INT AUTO_INCREMENT PRIMARY KEY,
  dev_id VARCHAR(50),
  temperature FLOAT,
  humidity INT,
  timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

3️⃣ Levantar los contenedores con Docker

Una vez creada la base de datos, ejecutar:

docker-compose up -d

Los servicios estarán disponibles en:

Node-RED: http://localhost:1880

phpMyAdmin: http://localhost:8080

4️⃣ Importar los flujos en Node-RED:

Ingresar a Node-RED.

Menú → Import → Seleccionar el archivo flujos-node-red.json.

Los flujos quedarán operativos sin modificaciones adicionales.

5️⃣ Configurar la API Key de OpenWeather:

Registrarse gratuitamente en https://openweathermap.org/api para obtener una clave personal.

Dentro de Node-RED, editar el nodo Preparar solicitud HTTP (en el flujo Datos Clima API) y colocar su clave en el campo appid= de la URL.

🗄 Modelo de la base de datos
Se utiliza una única tabla sensor_data:

id	Clave primaria (autoincremental)
dev_id	Fuente del dato (simulado o openweather)
temperature	Temperatura en grados Celsius
humidity	Humedad relativa (%)
timestamp	Fecha y hora del registro

🎓 Objetivos pedagógicos alcanzados
Simulación de sensores LoRa.

Consumo de API REST pública externa (OpenWeather).

Persistencia de datos relacional en MySQL.

Visualización en tiempo real mediante Dashboard de Node-RED.

Contenerización completa en Docker para despliegue portable.

Separación de flujos por origen de datos: simulado vs real.

📚 Asignatura
Principios y Aplicaciones para dispositivos LoRa/LoRaWAN — Especialización en IoT — Universidad de Buenos Aires

👨‍🎓 Autor
Rodrigo Morocho Román
