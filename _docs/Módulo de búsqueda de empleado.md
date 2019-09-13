---
title: Módulo de búsqueda de empleado
permalink: /docs/busqueda-empleado/
---

**Versión documento: ** v1

**Creación: ** 08/07/2019

**Última modificación: ** 23/08/2019

## Módulo de búsqueda de empleado

- **Búsqueda de empleado**: Localización de los empleados mediante el sistema de reservas de Bookker.

| Value | Descriptión                                                 |
| ----- | ----------------------------------------------------------- |
| true  | La organización tiene activada la búsqueda de empleados.    |
| false | La organización no tiene activada la búsqueda de empleados. |

### Búsqueda de empleado

La búsqueda de empleado se realiza, siempre y cuando el usuario haya dado su consentimiento previo, mediante las reservas que tiene organizadas.

Se realiza una búsqueda de las reservas que ha creado el usuario para saber en que ubicación se encontrará.
En caso de no tener reservas, no se podrá localizar al usuario mediante este sistema.

La búsqueda se realiza con fecha y hora del momento en el que se realiza la petición con una amplitud de 1 hora, es decir, si la petición de busqueda se realiza a las 12:30 se buscará al usuario dentro del rango 12:30 - 13:30.s

La petición devolverá un código `200 OK` siempre que el usuario pueda ser buscado, independientemente de que se pueda localizar o no.

#### Request

##### HTTP request

```http
GET /api/v1/users/{userId}/search
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Se devuelve un código `200` con las ubicaciones donde el usuario tiene reservas, así como la fecha de inicio y fin de éstas en UTC.

```json
HTTP/1.1 200 OK
Content-type: application/json

[
    {
        "resource": {
            "id": "902895dd-72eb-4abb-a11f-c4164ec9f72f",
            "name": "Puesto 3 P3",
            "posterCode": "A03P3",
            "phone": "989731231",
            "mapCoordinates": {
                "topLeftX": 292,
                "topLeftY": 3226,
                "bottomRightX": 340,
                "bottomRightY": 3274
            },
            "approachable": true,
            "floor": {
                "id": "1ed6c4c3-a6c1-415b-bee4-0ca3323c51f7",
                "name": "P3",
                "floorNumber": 3,
                "image": "https://admin.bookkercorp.com:8443/529b2ca3-41e0-4900-b108-96f83c0b5cc0/maps/c27af665-b24d-409b-a703-dbd546a7332f.png",
                "building": {
                    "id": "1c5239ea-9c42-47ac-81a0-d344e489ee56",
                    "name": "Oficina Albacete",
                    "address": {
                        "country": "España",
                        "city": "Albacete",
                        "address": "C/ Albacete 20",
                        "coordinates": {
                            "longitude": 432.0,
                            "latitude": 183.0
                        }
                    },
                    "organization": {
                        "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
                    }
                }
            },
            "subcategory": {
                "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c",
                "name": "Puesto de trabajo",
                "category": "WORKSTATION",
                "organization": {
                    "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
                }
            },
            "visible": true
        },
        "bookingStartDate": 1566561947000,
        "bookingEndDate": 1566565547000
    }
]
```
