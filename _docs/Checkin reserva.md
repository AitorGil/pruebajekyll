---
title: Check-In reserva
permalink: /docs/check-in-reserva/
---

**Versión documento: ** v1

**Creación: ** 02/07/2019

**Última modificación: ** 04/09/2019

## Check-in reserva

Permite realizar el check-in sobre una reserva.

Aspectos a tener en cuenta:

- Tipos de control de acceso:
  - ORGANIZER: Sólo el organizador de la reserva puede realizar el check-in.
  - OPTIONAL: Cualquier usuario invitado a la reserva y que haya confirmado su asistencia puede realizar check-in, pero si no se realiza la reserva no expirará.
  - ANY: Cualquier usuario invitado a la reserva y que haya confirmado su asistencia puede realizar check-in, pero si no se realiza la reserva expirará.
- Para realizar el check-in la reserva tiene que estar con estado PENDING.
- Si la reserva es supervisada, tanto el organizador (el usuario asignado), como el supervisor, pueden hacer check-in
- Para realizar el check-in la fecha actual tiene que estar en el intervalo en el que se puede realizar dicho check-in.

#### Request

##### HTTP request

```http
PATCH /api/v1/users/me/bookings/checkin/{bookingId}
PATCH /api/v1/users/{userId}/bookings/checkin/{bookingId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Header             | Value             | Required |
| ------------------ | ----------------- | -------- |
| presenceValidation | d8:c7:c8:cc:43:25 | false    |

#####

Ejemplo:

```http
PATCH /api/v1/users/me/bookings/checkin/96c0bc4a-1960-4b67-8552-8a29b6bc7015?presenceValidation=d8:c7:c8:cc:43:25
```

#### Response

Si se ha conseguido realizar el check-in, se devuelve un código `200` con los datos de la reserva en la que se realizó el check-in, en el cuerpo de la respuesta.

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "id": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
    "startDate": 1562053500000,
    "endDate": 1562062800000,
    "duration": 9300000,
    "status": "CONFIRMED",
    "accessControl": {
        "accessControlType": "OPTIONAL",
        "checkInDate": "2019-07-02T07:53:09.126+0000",
        "checkOutDate": null
    },
    "creator": {
        "id": "7eccd6ed-3faf-41de-bec1-0b8501316857"
    },
    "organizer": {
        "id": "7eccd6ed-3faf-41de-bec1-0b8501316857"
    },
    "resource": {
        "id": "b5fcf35f-bba2-4050-a246-631dac18e014",
        "approachable": false,
        "visible": true
    },
    "subject": "El título de la reserva",
    "body": {
        "content": "La descripción de la reserva bla bla bla bla bla...",
        "tipo": "TEXT"
    },
    "importance": "LOW",
    "resourceType": "SPACE"
}
```
