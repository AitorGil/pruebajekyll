---
title: Editar reserva supervisada
permalink: /docs/edicion-reserva-supervisada/
---

**Versión documento: ** v1

**Creación: ** 30/08/2019

**Última modificación: ** 30/08/2019

### Editar reserva supervisada

Permite editar una reserva supervisada.

A tener en cuenta:

- Si la reserva supervisada es recurrente, y por ejemplo es de Lunes a Viernes, habrá que editar la reserva de cada día, es decir, no se pueden editar todas a la vez.
- Sólo el supervisor de esa reserva puede editarla.
- Al editar la reserva de un día, hay que mandar todos los recursos y usuarios que estén asignados para ese día, independientemente de que se vaya a cambiar al usuario o no.

### Request

##### HTTP Request

```http
PATCH /api/v1/users/me/bookings/supervised
PATCH /api/v1/users/{userId}/bookings/supervised
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [NewAssignationInfo](#NewAssignationInfo)

| Type                                      | Description                                                                                                                                                                               | Required |
| ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| [NewAssignationInfo](#NewAssignationInfo) | Objeto con el id de la reserva supervisada, el título (opcional), la fecha de inicio y final de la reserva que se va a editar, y una lista con cada recurso asociado al usuario asignado. | true     |

### Response

Si se han conseguido asignar los usuarios a las reservas, se devuelve un código `200`, junto con el mismo objeto que se envío.

```json
{
  "supervisedBookingId": "2ec73d2e-0960-4a1f-9102-0d8e26cc097f",
  "assignationInfoList": [
    {
      "resourceId": "50b5e144-025d-4693-8645-f8c2ae450995",
      "userEmail": "aitor.gomez@bookkercorp.com"
    },
    {
      "resourceId": "867d751d-098c-41fa-9412-0de068ef2782",
      "userEmail": "ricardo.ureta@bookkercorp.com"
    },
    {
      "resourceId": "92abb5a5-8c64-428b-8b27-332032e121cd",
      "userEmail": "aitor.gil@bookkercorp.com"
    }
  ],
  "title": "Título actualizado",
  "startDate": 1567353600000,
  "endDate": 1567360800000
}
```

### NewAssignationInfo

```json
{
  "supervisedBookingId": "2ec73d2e-0960-4a1f-9102-0d8e26cc097f",
  "title": "Título actualizado",
  "startDate": 1567353600000,
  "endDate": 1567360800000,
  "assignationInfoList": [
    {
      "resourceId": "50b5e144-025d-4693-8645-f8c2ae450995",
      "userEmail": "aitor.gomez@bookkercorp.com"
    },
    {
      "resourceId": "867d751d-098c-41fa-9412-0de068ef2782",
      "userEmail": "ricardo.ureta@bookkercorp.com"
    },
    {
      "resourceId": "92abb5a5-8c64-428b-8b27-332032e121cd",
      "userEmail": "aitor.gil@bookkercorp.com"
    }
  ]
}
```
