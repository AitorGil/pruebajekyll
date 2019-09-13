---
title: Recuperar reservas del usuario
permalink: /docs/recuperar-reservas-usuario/
---

**Versión documento: ** v1

**Creación: ** 26/06/2019

**Última modificación: ** 29/07/2019

## Reservas del usuario

Se obtienen las reservas del usuario solicitado, tanto las que ha organizado como a las que ha sido invitado.

### Recuperar reservas del usuario

Intenta recuperar las reservas del usuario.

En las reservas como organizador se obtienen los datos principales de dichas reservas así como los datos del creador, recurso reservado y organizador.

En las reservas a las que ha sido invitado el usuario se obtienen los mismos datos mencionados anteriormente así como los datos del estado de la invitación.

Aspectos a tener en cuenta:

- Si la reserva esta cancelada, expirada o ha finalizado no aparecerá.
- Si la fecha de fin de reserva es anterior a la fecha actual, tampoco aparecerá.
- Si el invitado ha rechazado la reserva, no aparecerá.
- Para diferenciar si una reserva es de un puesto o de un espacio, en cada reserva existe un campo con clave "resourceType" y valor el tipo de reserva que sea, SPACE para espacios y WORKSTATION para puestos, por ejemplo.

#### Request

##### HTTP request

```http
GET /api/v1/users/me/bookings
GET /api/v1/users/{userId}/bookings
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Si se ha conseguido validar que el usuario tiene acceso para realizar la petición, se devuelve un código `200` con las reservas del usuario, en el cuerpo de la respuesta.

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "userIsInvited": [
        {
            "id": "d46309d9-f28b-4314-a543-968215113ef4",
            "recurrentId": "40fc53f1-e8d1-4524-a6e7-ec7a3f598cc2",
            "startDate": 1561644000000,
            "endDate": 1561645800000,
            "duration": 1800000,
            "status": "PENDING",
            "accessControlType": "OPTIONAL",
            "creator": {
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
            },
            "organizer": {
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
                "resourceRule": {
                    "createdBy": null,
                    "createdDate": "2019-06-24T08:40:36.000+0000",
                    "lastModifiedBy": null,
                    "lastModifiedDate": null,
                    "id": "e43209c8-f4ca-4fe6-b255-36cd6b769201",
                    "name": "Regla del recurso Despacho Principal",
                    "startTime": "06:00:00",
                    "endTime": "21:00:00",
                    "maximumDuration": 36000000,
                    "maximumAdvance": 30,
                    "accessControlType": "OPTIONAL",
                    "advanceCheckIn": 900000,
                    "expirationMargin": 1200000,
                    "requiresApproval": false,
                    "maxSpaceBooking": null,
                    "organizationId": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
                },
                "visible": true,
                "capacity": 30
            },
            "invitationInfo": {
                "id": "3c1398fc-b1d3-4274-a8eb-52bf4ebc5b69",
                "type": "OPCIONAL",
                "status": "NEEDS_ACTION",
                "bookingId": "d46309d9-f28b-4314-a543-968215113ef4",
                "user": {
                    "id": "7eccd6ed-3faf-41de-bec1-0b8501316857"
                }
            },
            "subject": "Es otra prueba",
            "body": {
                "content": "Otra prueba",
                "bodyType": "TEXT"
            },
            "importance": "NORMAL",
            "selfInvite": true,
            "attendeesCanInvite": true,
            "attendeesCanModify": true,
            "attendeesCanSeeOtherAttendees": true,
            "resourceType": "SPACE"
        }
    ],
    "userIsOrganizer": [
        {
            "id": "e2100ddd-f8a8-4f25-bb6a-2ca7a8c88d96",
            "recurrentId": "6a121e8a-1e72-42a2-9737-d60fae1b27e6",
            "startDate": 1561631400000,
            "endDate": 1561645800000,
            "duration": 14400000,
            "status": "CONFIRMED",
            "accessControlType": "OPTIONAL",
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
                "resourceRule": {
                    "createdBy": null,
                    "createdDate": "2019-06-24T08:40:36.000+0000",
                    "lastModifiedBy": null,
                    "lastModifiedDate": null,
                    "id": "e43209c8-f4ca-4fe6-b255-36cd6b769201",
                    "name": "Regla del recurso Despacho Principal",
                    "startTime": "06:00:00",
                    "endTime": "21:00:00",
                    "maximumDuration": 36000000,
                    "maximumAdvance": 30,
                    "accessControlType": "OPTIONAL",
                    "advanceCheckIn": 900000,
                    "expirationMargin": 1200000,
                    "requiresApproval": false,
                    "maxSpaceBooking": null,
                    "organizationId": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
                },
                "visible": true
            },
            "resourceType": "WORKSTATION"
        }
    ]
}
```
