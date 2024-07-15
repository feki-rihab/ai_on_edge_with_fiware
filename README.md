# ai_on_edge_with_fiware
This is a project to implement an AI on Edge application with FIWARE. 

## Environment Setup
### Architecture
![Architecture](/docs/architecture.png)

### Smart Data Model

This project utilizes the [WeatherObserved](https://fiware-datamodels.readthedocs.io/en/stable/Weather/WeatherObserved/doc/spec/index.html) smart data model. This standardized schema enables structured representation of weather observations, including key meteorological parameters (temperature, humidity, wind speed, atmospheric pressure) and geospatial-temporal data. 

### Prerequisites
- Docker
- Docker Compose
- Alternatively, Podman and Podman Compose

## Context Broker environment setup

[**Orion Context Broker**](https://fiware-orion.readthedocs.io/en/latest/) is used to manages context information.

[**MongoDB**](https://www.mongodb.com/) is used by the Orion Context Broker to hold context data information such as data entities, subscriptions and registrations.

- To test if the Context Broker service is running correctly, send a POST request to the Context Broker to create a new entity of the WeatherObserved data model:

```bash 
curl -iX POST 'localhost:1026/ngsi-ld/v1/entities' \
  --header 'Content-Type: application/json' \
  --data-raw '{
    "id": "urn:ngsi-ld:WeatherObserved:Berlin-2024-07-15T06:26:00",
    "type": "WeatherObserved",
    "dateObserved": {
      "type": "Property",
      "value": "2024-07-15T06:26:00Z"
    },
    "location": {
      "type": "GeoProperty",
      "value": {
        "type": "Point",
        "coordinates": [13.41053, 52.52437]
      }
    },
    "address": {
      "type": "Property",
      "value": {
        "addressCountry": "DE",
        "addressLocality": "Berlin"
      }
    },
    "temperature": {
      "type": "Property",
      "value": 18
    },
    "relativeHumidity": {
      "type": "Property",
      "value": 0.80
    },
    "precipitation": {
      "type": "Property",
      "value": 0.1
    },
    "windSpeed": {
      "type": "Property",
      "value": 3.5
    },
    "windDirection": {
      "type": "Property",
      "value": 150
    },
    "atmosphericPressure": {
      "type": "Property",
      "value": 1015
    },
    "weatherType": {
      "type": "Property",
      "value": "Partly cloudy"
    },
    "source": {
      "type": "Property",
      "value": "https://www.weatherapi.com"
    }
  }'
```
- Query the Context Broker:
```bash
curl -iX GET 'localhost:1026/ngsi-ld/v1/entities/urn:ngsi-ld:WeatherObserved:Berlin-2024-07-15T06:26:00'
```
If the entity is correctly created, you should have as a result an entity of type WeatherObserved created in the Context Broker.



