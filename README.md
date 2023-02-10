# ThingSpeak

Este proyecto se ha logrado llevar a cabo con el soporte de [ThingSpeak](https://thingspeak.com/), un servicio de IoT que permite almacenar y analiar datos en vivo en la nube de manera rápida y sencilla. Los datos de las estaciones meteorológicas son enviados a ThingSpeak para luego hacer la lectura de estos en la [página web](https://estacion-meteorologica-uis.github.io/) del proyecto donde se muestra el estado de las estaciones en tiempo real e histórico.

## Guía de Configuración Canales de ThingSpeak

Guia para configurar los canales de ThingSpeak. Se deben configurar tres canales específicos para cada estación meteorológica. Se usaran los 3 canales para generar reportes cada hora y diariamente. Por favor mantener el orden de los campos (Fields) para poder ser analizados correctamente.

### Canal Live
Este es el canal principal donde cada estación meteorológica envia los datos. En este canal se almacena el registro de todos los datos enviados.
- Name: Estación Meteorológica UIS - <ejem: 1,2,3,4> (Live)
- Fields
  - [x] Field 1: Temperatura
  - [x] Field 2: Humedad
  - [x] Field 3: Material Particulado
  - [x] Field 4: UV
  - [x] Field 5: CO2
- Link to External Site: https://estacion-meteorologica-uis.github.io/
- Link to GitHub: https://github.com/Estacion-Meteorologica-UIS
- [x] Show Channel Location:
  - Latitude: <insert location.lat>
  - Longitude: <insert location.lon>
- [x] Show Status

### Reportes cada Hora
En este canal se registra un promedio y valores pico de las variables medidas cada hora. 
- Name: Estación Meteorológica UIS - <ejem: 1,2,3,4> (por Hora)
- Fields
  - [x] Field 1: Temperatura Promedio hora
  - [x] Field 2: Humedad Promedio hora
  - [x] Field 3: Material Particulado Promedio hora
  - [x] Field 4: UV Promedio hora
  - [x] Field 5: CO2 Promedio hora
  - [x] Field 6: Max temperatura en la hora
  - [x] Field 7: Min temperatura en la hora
  - [x] Field 8: Max UV Hora

### Reportes Diarios
En este canal se registra un promedio y valores pico de las variables medidas cada día. 
- Name: Estación Meteorológica UIS - <ejem: 1,2,3,4> (Diario)
- Fields
  - [x] Field 1: Temperatura Promedio diario
  - [x] Field 2: Humedad Promedio diario
  - [x] Field 3: Material Particulado Promedio diario
  - [x] Field 4: UV Promedio diario
  - [x] Field 5: CO2 Promedio diario
  - [x] Field 6: Max temperatura en el dia
  - [x] Field 7: Min temperatura en el dia
  - [x] Field 8: Max UV en el dia

## Guía Configuración Apps de ThingSpeak

Para generar los reportes de cada hora y diarios de forma automática se usan las Apps de ThingSpeak que permiten automatizar tareas. Para esto se usan las apps de MATLAB Analysis y TimeControl. MATLAB Analysis permite trabajar con los datos de los canales, se usa para generar promedios y calcular valores picos en las medidas. Por su lado, TimeControl permite automatizar tareas y ejecutarlas repetidamente con un intervalo de tiempo.

### Reportes cada Hora
- MATLAB Analysis: El código de MATLAB se encuentra en `hourly_analysis.m`
- TimeControl: <intert img>
  
### Reportes Diarios
- MATLAB Analysis: El código de MATLAB se encuentra en `daily_analysis.m`
- TimeControl: <intert img>
  

## Credenciales Canales

Las credenciales públicas de los canales de ThingSpeak de cada estación meteorológica son almacenados en este repositorio en el archivo `stations.json`. Un archivo que puede ser leido fácilmente para obtener la información de ThingSpeak.

Si desea añadir nuevas estaciones a la lista, realice un pull request e inserte al final del archivo la información del canal de ThingSpeak usando la siguiente estructura.

```
{
  "stations": [
      ...
      {
          "name": "<insert name>",
          "live": {
              "channelID": <insert channerid>,
              "readAPIKey": "<insert readapikey>",
          },
          "hourly": {
              "channelID": <insert channerid>,
              "readAPIKey": "<insert readapikey>",
          },
          "daily": {
              "channelID": <insert channerid>,
              "readAPIKey": "<insert readapikey>",
          },
      },
  ]
}
```
