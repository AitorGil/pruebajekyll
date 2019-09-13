---
title: Check-Out reserva
permalink: /docs/check-out-reserva/
---

**Versión documento: ** v1

**Creación: ** 02/07/2019

**Última modificación: ** 05/09/2019

## Check-out reserva

Permite realizar el check-out sobre una reserva.

Aspectos a tener en cuenta:

- Tipos de control de acceso:
  - ORGANIZER: Sólo el organizador de la reserva puede realizar el check-out.
  - OPTIONAL: Cualquier usuario invitado a la reserva y que haya confirmado su asistencia puede realizar check-out.
  - ANY: Cualquier usuario invitado a la reserva y que haya confirmado su asistencia puede realizar check-out.
- En el momento en el que se hace check-in, el check-out está disponible, menos cuando la reserva ya haya terminado.
- En las reservas supervisadas tanto el supervisor como el organizador (usuario asignado) pueden hacer check-out
- Para realizar el check-out si el control de acceso de la reserva no es OPTIONAL se tiene que haber realizado el check-in y que el estado de la reserva sea CONFIRMED.

#### Request

##### HTTP request

```http
PATCH /api/v1/users/me/bookings/checkout/{bookingId}
PATCH /api/v1/users/{userId}/bookings/checkout/{bookingId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Si se ha conseguido realizar el check-out, se devuelve un código `200` con el body de la respuesta vacío.
