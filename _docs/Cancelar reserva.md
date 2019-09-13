---
title: Cancelar reserva
permalink: /docs/cancelar-reserva/
---

**Versión documento: ** v1

**Creación: ** 01/07/2019

**Última modificación: ** 03/07/2019

## Cancelar reserva

Permite cancelar una reserva.

### Cancelar una reserva

Permite cancelar la reserva asociada al ID que se envía, si el usuario que solicita cancelarla es el organizador, la reserva no está expirada, cancelada o confirmada y la fecha actual es anterior a la fecha de fin de la reserva..

Se puede asignar el ID de una razón de cancelación si así se desea.

#### Request

##### HTTP request

```http
DELETE /api/v1/users/me/bookings/{bookingId}
DELETE /api/v1/users/{userId}/bookings/{bookingId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Param                | Value                                                                                       | Required |
| -------------------- | ------------------------------------------------------------------------------------------- | -------- |
| cancellationReasonId | String - Identificador del motivo de cancelación (Ej: 65c0eb54-5da2-4540-b7ef-1cd9126038ff) | false    |

#### Response

Si se ha conseguido validar que el usuario tiene acceso y se consigue cancelar la reserva correctamente, se envía un body vacío.

## Cancelar reserva recurrente

### Cancelar una reserva recurrente

Permite cancelar las reservas asociadas al ID de recurrencia que se envía, si el usuario que solicita cancelarla es el organizador, la reserva no está expirada, cancelada o confirmada y la fecha actual es anterior a la fecha de fin de la reserva.

Se puede asignar el ID de una razón de cancelación si así se desea.

#### Request

##### HTTP request

```http
DELETE /api/v1/users/me/bookings/recurrent/{recurrentId}
DELETE /api/v1/users/{userId}/bookings/recurrent/{recurrentId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Param                | Value                                                                                       | Required |
| -------------------- | ------------------------------------------------------------------------------------------- | -------- |
| cancellationReasonId | String - Identificador del motivo de cancelación (Ej: 65c0eb54-5da2-4540-b7ef-1cd9126038ff) | false    |

#### Response

Si se ha conseguido validar que el usuario tiene acceso y se consigue cancelar las reservas correctamente, se envía un body vacío.
