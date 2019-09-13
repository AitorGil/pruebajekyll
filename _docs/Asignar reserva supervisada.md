---
title: Asignar reserva supervisada
permalink: /docs/asignar-reserva-supervisada/
---

**Versión documento: ** v1

**Creación: ** 27/08/2019

**Última modificación: ** 30/08/2019

### Asignar usuarios

Permite asignar usuarios a los recursos de una reserva supervisada, tanto externos como internos.

A tener en cuenta:

- Solo el supervisor de la reserva puede realizar esta acción.
- El organizador será el usuario asignado, aunque este no podrá ni editar ni cancelar la reserva.

### Request

##### HTTP Request

```http
PATCH /api/v1/users/me/bookings/supervised/assign
PATCH /api/v1/users/{userId}/bookings/supervised/assign
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [AssignationInfoWrapper](#AssignationInfoWrapper)

| Type                                              | Description                                                                                      | Required |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------ | -------- |
| [AssignationInfoWrapper](#AssignationInfoWrapper) | Objeto con el id de la reserva supervisada, los ids de los recursos y los emails de los usuarios | true     |

### Response

Si se han conseguido asignar los usuarios a las reservas, se devuelve un código `200`, con el id de la reserva supervisada, el título, y la lista de las reservas (para cada día), con su fecha y la lista de usuarios asignados a cada recurso, asi como la información de check-in para cada usuario asignado.

```json
{
  "supervisedBookingId": "d6495b17-b418-486f-b705-e19d605bb713",
  "title": "Primera prueba de reserva supervisada!",
  "floorId": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95",
  "bookingList": [
    {
      "startDate": 1567612800000,
      "endDate": 1567620000000,
      "assignationInfoList": [
        {
          "userEmail": "aitor.gomez@bookkercorp.com",
          "resource": {
            "id": "50b5e144-025d-4693-8645-f8c2ae450995",
            "name": "A01PB",
            "posterCode": "A01PB",
            "externalSyncEmail": "puesto1@resource.com",
            "phone": "941576132",
            "mapCoordinates": {
              "topLeftX": 692,
              "topLeftY": 3209,
              "bottomRightX": 742,
              "bottomRightY": 3259
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
          "userCheckInInfo": {
            "checkedIn": false,
            "checkedOut": false
          }
        }
      ]
    }
  ]
}
```

### AssignationInfoWrapper

```json
{
  "supervisedBookingId": "3a2b3854-d41b-4d44-a696-c258e8f2470a",
  "assignationInfoList": [
    {
      "resourceId": "50b5e144-025d-4693-8645-f8c2ae450995",
      "userEmail": "aitor.gomez@bookkercorp.com"
    }
  ]
}
```
