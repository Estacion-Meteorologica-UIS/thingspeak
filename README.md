# ThingSpeak

Este proyecto se ha logrado llevar a cabo con el soporte de [ThingSpeak](https://thingspeak.com/), un servicio de IoT que permite almacenar y analiar datos en vivo en la nube de manera rápida y sencilla. Los datos de las estaciones meteorológicas son enviados a ThingSpeak para luego hacer la lectura de estos en la [página web](https://estacion-meteorologica-uis.github.io/) del proyecto donde se muestra el estado de las estaciones en tiempo real e histórico.

## Configuración ThingSpeak

Guia para configurar los canales de ThingSpeak. Se debe configurar un canal específico para cada estación meteorológica. Por favor mantener el orden de los campos (Fields) para poder ser analizados correctamente.
- Name: Estación Meteorológica UIS - <ejem: 1,2,3,4>
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

## Credenciales Canales

Las credenciales públicas de los canales de ThingSpeak de cada estación meteorológica son almacenados en este repositorio en el archivo `stations.json`. Un archivo que puede ser leido fácilmente para obtener la información de ThingSpeak.

Si desea añadir nuevas estaciones a la lista, realice un pull request e inserte al final del archivo la información del canal de ThingSpeak usando la siguiente estructura.

```
{
  "stations": [
      ...
      {
          "name": "<insert name>",
          "channelID": <insert channerid>,
          "readAPIKey": "<insert readapikey>"
      },
  ]
}
```
