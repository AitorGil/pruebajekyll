---
title: Edición de reservas
permalink: /docs/edicion-reserva/
---

**Versión documento: ** v1

**Creación: ** 03/07/2019

**Última modificación: ** 03/07/2019

### Editar reserva de puesto

Intenta actualizar la reserva de puesto del usuario con los nuevos datos.

Campos que se pueden modificar:

- **startDate**: Fecha de inicio.
- **endDate**: Fecha de fin.

#### Request

##### HTTP request

```http
PUT /api/v1/users/me/bookings/workstations/{bookingId}
PUT /api/v1/users/{userId}/bookings/workstations/{bookingId}

```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [WorkstationBooking](#WorkstationBooking).

| Property | Type                                      | Description                                   | Required |
| -------- | ----------------------------------------- | --------------------------------------------- | -------- |
| Booking  | [WorkstationBooking](#WorkstationBooking) | Datos que se quieren modificar de la reserva. | true     |

#### Response

Si se han conseguido editar la reserva, se devuelve un código `200` con la información de las misma.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "f515be12-e9b7-4415-9c11-a6cd6ab02cd4",
    "recurrentId": "bb1f051e-cf23-4d0d-ae4a-d95814efc43d",
    "startDate": 1562144400000,
    "endDate": 1562148000000,
    "duration": 3600000,
    "status": "PENDING",
    "accessControl": {
        "accessControlType": "OPTIONAL",
        "checkInDate": null,
        "checkOutDate": null
    },
    "creator": {
        "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
        "name": "Aitor",
        "surname": "Gil",
        "alias": "AITORGC",
        "email": "aitor.gil@bookkercorp.com",
        "phone": "631256311",
        "organization": {
            "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
        },
        "department": {
            "id": "26980ebb-0ac7-4bb0-bab1-81ed8fc07d59"
        },
        "userRule": {
            "id": "d58b188f-6ba6-48c4-9e0a-dd0ac81d4cb2"
        },
        "mobileRole": {
            "id": "5220b6a2-8920-4dae-8ff0-ba96707d439d"
        }
    },
    "organizer": {
        "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
        "name": "Aitor",
        "surname": "Gil",
        "alias": "AITORGC",
        "email": "aitor.gil@bookkercorp.com",
        "phone": "631256311",
        "organization": {
            "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
        },
        "department": {
            "id": "26980ebb-0ac7-4bb0-bab1-81ed8fc07d59"
        },
        "userRule": {
            "id": "d58b188f-6ba6-48c4-9e0a-dd0ac81d4cb2"
        },
        "mobileRole": {
            "id": "5220b6a2-8920-4dae-8ff0-ba96707d439d"
        }
    },
    "resource": {
        "id": "01789b12-4cf5-4184-a8ce-c958f8924402",
        "name": "Puesto #2",
        "posterCode": "C07P2",
        "phone": "941987789",
        "mapCoordinates": {
            "topLeftX": 441,
            "topLeftY": 3226,
            "bottomRightX": 489,
            "bottomRightY": 3274
        },
        "approachable": true,
        "floor": {
            "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
        },
        "subcategory": {
            "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
        },
        "visible": true
    },
    "resourceType": "WORKSTATION"
}
```

### Editar reserva de espacio

Intenta actualizar la reserva de espacio del usuario con los nuevos datos.

Hay dos tipos de edición de reserva de espacio:

- **PUT**: Actualiza la reserva completamente lo que obliga a recalcular las reglas del usuario y del recurso.
- **PATCH**: Actualiza parcialmente la reserva no siendo necesario recalcular las reglas del usuario ni del recurso.

Campos que se pueden modificar:

| Campo             | Descripción                                              | PUT | PATCH |
| ----------------- | -------------------------------------------------------- | --- | ----- |
| startDate         | Fecha de incio en milisegundos.                          | Sí  | No    |
| endDate           | Fecha de fin en milisegundos.                            | Sí  | No    |
| importance        | Importancia de la reserva (LOW, NORMAL, HIGH).           | Sí  | Sí    |
| subject           | Título o asunto de la reserva.                           | Sí  | Sí    |
| bodyType          | Tipo del cuerpoo descripción de la reserva (TEXT, HTML). | Sí  | Sí    |
| content           | Cuerpo o descripción de la reserva.                      | Sí  | Sí    |
| internalAttendees | Invitados internos.                                      | Sí  | Sí    |
| externalAttendees | Invitados externos a la plataforma Bookker.              | Sí  | Sí    |

#### Request

##### HTTP request

```http
PUT /api/v1/users/me/bookings/spaces/{bookingId}
PUT /api/v1/users/{userId}/bookings/spaces/{bookingId}
PATCH /api/v1/users/me/bookings/spaces/{bookingId}
PATCH /api/v1/users/{userId}/bookings/spaces/{bookingId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [SpaceBooking](#SpaceBooking).

| Property | Type                          | Description                                   | Required |
| -------- | ----------------------------- | --------------------------------------------- | -------- |
| Booking  | [SpaceBooking](#SpaceBooking) | Datos que se quieren modificar de la reserva. | true     |

#### Response

Si se han conseguido editar la reserva, se devuelve un código `200` con la información de las misma.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "30b234c0-c148-4673-9a08-179eacf5db40",
    "startDate": 1562835600000,
    "endDate": 1562837400000,
    "duration": 1800000,
    "status": "PENDING",
    "accessControl": {
        "accessControlType": "OPTIONAL",
        "checkInDate": null,
        "checkOutDate": null
    },
    "creator": {
        "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
        "name": "Aitor",
        "surname": "Gil",
        "alias": "AITORGC",
        "email": "aitor.gil@bookkercorp.com",
        "phone": "631256311",
        "organization": {
            "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
        },
        "department": {
            "id": "26980ebb-0ac7-4bb0-bab1-81ed8fc07d59"
        },
        "userRule": {
            "id": "d58b188f-6ba6-48c4-9e0a-dd0ac81d4cb2"
        },
        "mobileRole": {
            "id": "5220b6a2-8920-4dae-8ff0-ba96707d439d"
        }
    },
    "organizer": {
        "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
        "name": "Aitor",
        "surname": "Gil",
        "alias": "AITORGC",
        "email": "aitor.gil@bookkercorp.com",
        "phone": "631256311",
        "organization": {
            "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
        },
        "department": {
            "id": "26980ebb-0ac7-4bb0-bab1-81ed8fc07d59"
        },
        "userRule": {
            "id": "d58b188f-6ba6-48c4-9e0a-dd0ac81d4cb2"
        },
        "mobileRole": {
            "id": "5220b6a2-8920-4dae-8ff0-ba96707d439d"
        }
    },
    "resource": {
        "id": "b5fcf35f-bba2-4050-a246-631dac18e014",
        "name": "Despacho principal",
        "posterCode": "D01P3",
        "phone": "941827392",
        "mapCoordinates": {
            "topLeftX": 803,
            "topLeftY": 685,
            "bottomRightX": 1042,
            "bottomRightY": 894
        },
        "approachable": true,
        "floor": {
            "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
        },
        "subcategory": {
            "id": "9badbe29-e0d3-4dfc-a4b0-1093066db89e"
        },
        "visible": true,
        "capacity": 30
    },
    "resourceType": "SPACE",
    "internalAttendees": [
            {
                "id": "efa8083b-cf9b-42a4-bbe3-81cc7d56613b",
                "type": "REQUIRED",
                "status": "NEEDS_ACTION",
                "bookingId": "d2a00b25-e4da-456a-ab8e-8c04aa201161",
                "user": {
                    "id": "fa9d9890-e9e7-4ad9-82fd-572ae925f905"
                }
            },
            {
                "id": "a4c17da1-efb3-49cc-8293-0f1888ae663a",
                "type": "ORGANIZER",
                "status": "ACCEPTED",
                "bookingId": "d2a00b25-e4da-456a-ab8e-8c04aa201161",
                "user": {
                    "id": "7eccd6ed-3faf-41de-bec1-0b8501316857"
                }
            }
        ],
        "externalAttendees": [
            {
                "id": "936a425f-1649-4b24-9c8e-191adbe4accf",
                "type": "OPTIONAL",
                "status": "NEEDS_ACTION",
                "bookingId": "d2a00b25-e4da-456a-ab8e-8c04aa201161",
                "email": "usuarioexterno2@gmail.com"
            },
            {
                "id": "c92f7a1e-e392-4bdf-9267-46ad7c42d570",
                "type": "OPTIONAL",
                "status": "NEEDS_ACTION",
                "bookingId": "d2a00b25-e4da-456a-ab8e-8c04aa201161",
                "email": "usuarioexterno1@gmail.com"
            }
        ]
}
```

### WorkstationBooking

```json
{
  "startDate": 1562407200000,
  "endDate": 1762409000000
}
```

### SpaceBooking

```json
{
  "startDate": 1562067600000,
  "endDate": 1562070010000,
  "importance": "NORMAL",
  "subject": "TITULO ACTUALIZADO",
  "body": {
    "content": "Uy esto no parece HTML",
    "bodyType": "HTML"
  },
  "internalAttendees": [
    {
      "type": "REQUIRED",
      "user": {
        "id": "fa9d9890-e9e7-4ad9-82fd-572ae925f905"
      }
    }
  ],
  "externalAttendees": [
    {
      "type": "OPTIONAL",
      "email": "usuarioexterno1@gmail.com"
    },
    {
      "type": "OPTIONAL",
      "email": "usuarioexterno2@gmail.com"
    }
  ]
}
```
