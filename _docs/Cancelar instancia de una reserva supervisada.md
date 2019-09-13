---
title: Cancelar instancia de una reserva supervisada
permalink: /docs/cancelar-instancia-reserva-supervisada/
---

**Versión documento: ** v1

**Creación: ** 02/09/2019

**Última modificación: ** 05/09/2019

### Cancelar una instancia

Permite cancelar una instancia de una reserva supervisada, es decir, cancelará todas las reservas de un día concreto, y si se especifíca el organizador, las reservas de ese día en las que organizador sea el indicado en la llamada.

A tener en cuenta:

- Sólo se pueden cancelar las reservas que tengan estado **PENDING**.

- Sólo el supervisor de la reserva supervisada puede cancelarla.

- Solo se pueden cancelar las reservas de un día, no de varios a la vez, si se quiere realizar esta última acción, se tendrá que utilizar varias veces esta llamada.

### Request

##### HTTP Request

```http
DELETE /api/v1/users/me/bookings/supervised/{supervisedBookingId}/instances
DELETE /api/v1/users/{userId}/bookings/supervised/{supervisedBookingId}/instances
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Param       | Value                                              | Required |
| ----------- | -------------------------------------------------- | -------- |
| startDate   | Long - La fecha de inicio                          | true     |
| endDate     | Long - La fecha de fin                             | true     |
| organizerId | El organizador de la reserva (el usuario asignado) | false    |

### Response

Si todo ha ido correctamente se devuelve un código `200`.
