---
title: Cambio de estado de asistencia
permalink: /docs/cambio-de-estado-de-asistencia/
---

**Versión documento: ** v1

**Creación: ** 03/07/2019

**Última modificación: ** 04/07/2019

## Cambio de estado de asistencia

Permite editar el estado de asistencia del usuario invitado a una reserva usando el ID de asistente envíado y el nuevo estado.

Aspectos a tener en cuenta:

- Si el asistente no existe, no se podrá editar.

- Si el asistente ya ha rechazado la invitación (su estado es DECLINED) no se podrá editar.

- Si el estado no es NEEDS_ACTION no se puede volver a poner éste.

- Si la reserva está cancelada, expirada, ya ha acabado o no existe no se podrá editar.

- Si el usuario con el que se intenta realizar la petición no es el asistente no se podrá editar.

- Si el nuevo estado no coincide 100% con los estados disponibles no se podrá editar. Los estados de asistencia disponibles actualmente son:

  - NEEDS_ACTION
  - ACCEPTED
  - DECLINED
  - TENTATIVE

- Si la fecha de fin de la reserva es menor a la fecha actual, no se podrá editar.

#### Request

##### HTTP request

```http
PATCH /api/v1/users/bookings/attendees/{attendeeId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Param          | Value                                                 | Required |
| -------------- | ----------------------------------------------------- | -------- |
| attendeeStatus | String - El nuevo estado de asistencia (Ej: ACCEPTED) | true     |

#### Response

Si se ha conseguido editar el estado de asistencia del invitado, se envía un body vacío.
