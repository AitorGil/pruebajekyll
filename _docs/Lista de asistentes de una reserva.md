---
title: Lista de asistentes de una reserva
permalink: /docs/recuperar-asistentes/
---

**Versión documento: ** v1

**Creación: ** 04/07/2019

**Última modificación: ** 04/07/2019

## Lista de asistentes de una reserva

Se obtiene la lista de asistentes (internos y externos) de una reserva.

### Recuperar asistentes

Intenta recuperar los asistentes de una reserva.

Esta llamada no devolverá dicha lista de asistentes:

- Si el usuario no es ni organizador ni asistente.
- Si el usuario que solicita la lista es asistente pero ha rechazado la invitación.
- Si la reserva no existe, está cancelada, expirada o ha acabado.
- Si la reserva no es un espacio.
- Si la fecha de finalización de la reserva es menor que la fecha actual.

Para diferenciar entre asistentes internos y externos se usan dos listas diferentes, una denominada"internalAttendees" y otra denominada "externalAttendees".

#### Request

##### HTTP request

```http
GET /api/v1/users/bookings/{bookingId}/attendees
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Si se han conseguido validar las diferentes condiciones para obtener la lista de asistentes, se devuelve un código `200` con dicha lista, en el cuerpo de la respuesta.

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "internalAttendees": [
        {
            "id": "8cf55ab6-0ac5-4da9-bcd1-147226169b06",
            "type": "ORGANIZER",
            "status": "ACCEPTED",
            "bookingId": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
            "user": {
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
            }
        },
        {
            "id": "8fcbfb10-2330-426e-8907-ee489529a92e",
            "type": "OPTIONAL",
            "status": "DECLINED",
            "bookingId": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
            "user": {
                "id": "8c0fa5d8-0d25-4c31-bead-c279de53d8a6",
                "name": "Aitor",
                "surname": "Gomez",
                "alias": "AITORGA",
                "email": "aitor.gomez@bookkercorp.com",
                "phone": "676283181",
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
            }
        }
    ],
    "externalAttendees": [
        {
            "id": "0e2def5e-c3b7-4cc2-94ac-d4b7ef7aab8c",
            "type": "OPTIONAL",
            "status": "ACCEPTED",
            "bookingId": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
            "email": "usuarioexterno1@gmail.com"
        },
        {
            "id": "48621342-3e48-49bf-b246-186ec9344fc9",
            "type": "OPTIONAL",
            "status": "NEEDS_ACTION",
            "bookingId": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
            "email": "usuarioexterno2@gmail.com"
        }
    ]
}
```
