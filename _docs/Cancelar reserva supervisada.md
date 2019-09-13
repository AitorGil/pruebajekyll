---
title: Cancelar reserva supervisada
permalink: /docs/cancelar-reserva-supervisada/
---

**Versión documento: ** v1

**Creación: ** 02/09/2019

**Última modificación: ** 02/09/2019

### Cancelar reserva supervisada

Permite cancelar una reserva supervisada por completo, es decir, cancelará todas las reservas existentes de cada usuario asignado a la reserva supervisada.

A tener en cuenta:

- Sólo se pueden cancelar las reservas que tengan estado **PENDING**.

- Sólo el supervisor de la reserva supervisada puede cancelarla.

### Request

##### HTTP Request

```http
DELETE /api/v1/users/me/bookings/supervised/{supervisedBookingId}
DELETE /api/v1/users/{userId}/bookings/supervised/{supervisedBookingId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

### Response

Si todo ha ido correctamente se devuelve un código `200`.
