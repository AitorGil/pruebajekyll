---
title: Códigos de error y causas
permalink: /docs/errores/
---

**Fecha de creación:** 05/09/2019

**Fecha de última modificación:** 09/09/2019

[TOC]





### Auth

#### Refresh Authorization

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario                               |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| ROLE_NOT_FOUND          | No se ha encontrado el rol móvil del usuario                 |



### Users

#### Obtener usuario

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario                               |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| ROLE_NOT_FOUND          | No se ha encontrado el rol móvil del usuario                 |
| ORGANIZATION_NOT_FOUND  | No se ha encontrado la organización del usuario              |
| DEPARTMENT_NOT_FOUND    | No se ha encontrado el departamento del usuario              |





#### Obtener recursos del usuario

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario                               |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |



#### Obtener contactos del usuario

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario                               |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |



#### Añadir contacto a favoritos

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| CONTACT_NOT_FOUND       | No se encuentra al contacto que se quiere añadir a favoritos |



#### Eliminar contacto de favoritos

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| CONTACT_NOT_FOUND       | No se encuentra al contacto que se quiere eliminar de favoritos |



#### Buscar empleado

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| MODULE_IS_NOT_ACTIVE    | El módulo de búsqueda de empleado no está activado           |
| USER_CANT_BE_SEARCHED   | El usuario no puede ser buscado                              |



#### Actualizar perfil del usuario

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |





### Bookings



#### Crear reserva de puesto

| Código de error              | Causa(s)                                                     |
| ---------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND               | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS      | El usuario que hace la petición no tiene acceso a la organización |
| INVALID_JSON                 | El JSON enviado en la petición es inválido                   |
| RESOURCE_NOT_ACTIVATED       | El recurso no está activado                                  |
| USER_RULE_NOT_FOUND          | Regla de usuario no encontrada                               |
| WORKSTATION_NOT_FOUND        | Puesto no encontrado                                         |
| RESOURCE_RULE_NOT_FOUND      | Regla de recurso no encontrada                               |
| INVALID_BOOKING_DATE         | La fecha de inicio o fin es inválida                         |
| INVALID_ADVANCE_DAYS         | Se ha intentado reservar con una antelación superior a la establecida en la regla del recurso |
| INVALID_DURATION             | Duración invalida, es mayor que la permitida por la regla del recurso o es menor de 15 minutos |
| INVALID_RESOURCE_SCHEDULE    | La fecha de inicio o fin está fuera de la fecha de inicio o fin de la regla del recurso. |
| INVALID_USER_WORKING_DAY     | La duración supera el límite de la jornada del usuario       |
| RESOURCE_GROUP_NOT_FOUND     | No se ha encontrado el grupo del recurso                     |
| USER_GROUP_NOT_FOUND         | El usuario no tiene acceso al recurso                        |
| RESOURCE_ALREADY_HAS_BOOKING | El recurso ya tiene una reserva                              |
| USER_ALREADY_HAS_BOOKING     | El usuario ya tiene una reserva                              |



#### Crear reserva de espacio

| Código de error              | Causa(s)                                                     |
| ---------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND               | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS      | El usuario que hace la petición no tiene acceso a la organización |
| INVALID_JSON                 | El JSON enviado en la petición es inválido                   |
| RESOURCE_NOT_ACTIVATED       | El recurso no está activado                                  |
| USER_RULE_NOT_FOUND          | Regla de usuario no encontrada                               |
| SPACE_NOT_FOUND              | Espacio no encontrado                                        |
| RESOURCE_RULE_NOT_FOUND      | Regla de recurso no encontrada                               |
| INVALID_BOOKING_DATE         | La fecha de inicio o fin es inválida                         |
| INVALID_ADVANCE_DAYS         | Se ha intentado reservar con una antelación superior a la establecida en la regla del recurso |
| INVALID_DURATION             | Duración invalida, es mayor que la permitida por la regla del recurso o es menor de 15 minutos |
| INVALID_RESOURCE_SCHEDULE    | La fecha de inicio o fin está fuera de la fecha de inicio o fin de la regla del recurso. |
| INVALID_USER_WORKING_DAY     | La duración supera el límite de la jornada del usuario       |
| RESOURCE_GROUP_NOT_FOUND     | No se ha encontrado el grupo del recurso                     |
| USER_GROUP_NOT_FOUND         | El usuario no tiene acceso al recurso                        |
| RESOURCE_ALREADY_HAS_BOOKING | El recurso ya tiene una reserva                              |
| USER_ALREADY_HAS_BOOKING     | El usuario ya tiene una reserva                              |
| RECURRENCE_NOT_ALLOWED       | (Sólo aparece si la sincronización externa está activada) Recurrencia no permitida. |
| RESOURCE_HAS_NO_EMAIL        | (Sólo aparece si la sincronización externa está activada) El recurso no tiene un email de sincronización externa. |
| CREATE_EVENT_ERROR           | (Sólo aparece si la sincronización externa está activada) Ha ocurrido un error al crear la reserva en el calendario de Outlook / Google. |



#### Crear reserva de puesto por la cámara

| Código de error              | Causa(s)                                                     |
| ---------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND               | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS      | El usuario que hace la petición no tiene acceso a la organización |
| PRESENCE_VALIDATION_REQUIRED | Validación de presencia necesaria                            |
| RESOURCE_NOT_FOUND           | Recurso no encontrado                                        |
| WRONG_PRESENCE_VALIDATION    | Se ha enviado una clave de validación incorrecta             |
| INVALID_JSON                 | El JSON enviado en la petición es inválido                   |
| RESOURCE_NOT_ACTIVATED       | El recurso no está activado                                  |
| USER_RULE_NOT_FOUND          | Regla de usuario no encontrada                               |
| WORKSTATION_NOT_FOUND        | Puesto no encontrado                                         |
| RESOURCE_RULE_NOT_FOUND      | Regla de recurso no encontrada                               |
| INVALID_BOOKING_DATE         | La fecha de inicio o fin es inválida                         |
| INVALID_ADVANCE_DAYS         | Se ha intentado reservar con una antelación superior a la establecida en la regla del recurso |
| INVALID_DURATION             | Duración invalida, es mayor que la permitida por la regla del recurso o es menor de 15 minutos |
| INVALID_RESOURCE_SCHEDULE    | La fecha de inicio o fin está fuera de la fecha de inicio o fin de la regla del recurso. |
| INVALID_USER_WORKING_DAY     | La duración supera el límite de la jornada del usuario       |
| RESOURCE_GROUP_NOT_FOUND     | No se ha encontrado el grupo del recurso                     |
| USER_GROUP_NOT_FOUND         | El usuario no tiene acceso al recurso                        |
| RESOURCE_ALREADY_HAS_BOOKING | El recurso ya tiene una reserva                              |
| USER_ALREADY_HAS_BOOKING     | El usuario ya tiene una reserva                              |



#### Crear reserva de espacio por la cámara

| Código de error              | Causa(s)                                                     |
| ---------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND               | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS      | El usuario que hace la petición no tiene acceso a la organización |
| PRESENCE_VALIDATION_REQUIRED | Validación de presencia necesaria                            |
| RESOURCE_NOT_FOUND           | Recurso no encontrado                                        |
| WRONG_PRESENCE_VALIDATION    | Se ha enviado una clave de validación incorrecta             |
| INVALID_JSON                 | El JSON enviado en la petición es inválido                   |
| RESOURCE_NOT_ACTIVATED       | El recurso no está activado                                  |
| USER_RULE_NOT_FOUND          | Regla de usuario no encontrada                               |
| SPACE_NOT_FOUND              | Espacio no encontrado                                        |
| RESOURCE_RULE_NOT_FOUND      | Regla de recurso no encontrada                               |
| INVALID_BOOKING_DATE         | La fecha de inicio o fin es inválida                         |
| INVALID_ADVANCE_DAYS         | Se ha intentado reservar con una antelación superior a la establecida en la regla del recurso |
| INVALID_DURATION             | Duración invalida, es mayor que la permitida por la regla del recurso o es menor de 15 minutos |
| INVALID_RESOURCE_SCHEDULE    | La fecha de inicio o fin está fuera de la fecha de inicio o fin de la regla del recurso. |
| INVALID_USER_WORKING_DAY     | La duración supera el límite de la jornada del usuario       |
| RESOURCE_GROUP_NOT_FOUND     | No se ha encontrado el grupo del recurso                     |
| USER_GROUP_NOT_FOUND         | El usuario no tiene acceso al recurso                        |
| RESOURCE_ALREADY_HAS_BOOKING | El recurso ya tiene una reserva                              |
| USER_ALREADY_HAS_BOOKING     | El usuario ya tiene una reserva                              |
| RESOURCE_HAS_NO_EMAIL        | (Sólo aparece si la sincronización externa está activada) El recurso no tiene un email de sincronización externa. |
| CREATE_EVENT_ERROR           | (Sólo aparece si la sincronización externa está activada) Ha ocurrido un error al crear la reserva en el calendario de Outlook / Google. |



#### Crear reserva de puesto 1 click

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| INVALID_JSON            | El JSON enviado en la petición es inválido. Puede ocurrir si no se envía un ID de subcategoría o de edificio |
| BUILDING_NOT_FOUND      | Edificio no encontrado                                       |
| RESOURCE_RULE_NOT_FOUND | Regla de recurso no encontrada                               |



#### Recuperar reservas del usuario

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| RESOURCE_RULE_NOT_FOUND | Regla de recurso no encontrada                               |



#### Check-in

| Código de error                     | Causa(s)                                                     |
| ----------------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND                      | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS             | El usuario que hace la petición no tiene acceso a la organización |
| BOOKING_NOT_FOUND                   | Reserva no encontrada                                        |
| PRESENCE_VALIDATION_REQUIRED        | Validación de presencia necesaria                            |
| RESOURCE_NOT_FOUND                  | Recurso no encontrado                                        |
| WRONG_PRESENCE_VALIDATION           | Se ha enviado una clave de validación incorrecta             |
| USER_HAS_GOT_NOT_ACCESS             | Es una reserva supervisada y el usuario intentando hacer check-in no es ni el supervisor ni el organizador |
| USER_IS_NOT_SUPERVISOR_OR_ORGANIZER | El usuario no es el organizador de la reserva y el control de acceso de ésta es ORGANIZER (Sólo el organizador puede hacer check-in) |
| USER_IS_NOT_ATTENDEE                | Es una reserva de espacio en la que los asistentes pueden hacer check-in, pero el usuario intentándolo no lo es |
| RESOURCE_HAS_NO_RULES               | El recurso no tiene regla                                    |
| CHECK_IN_NOT_ACTIVE_YET             | Es demasiado pronto para hacer check-in                      |
| CHECK_IN_EXPIRED                    | Es demasiado tarde para hacer check-in                       |



#### Check-out

| Código de error                     | Causa(s)                                                     |
| ----------------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND                      | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS             | El usuario que hace la petición no tiene acceso a la organización |
| BOOKING_NOT_FOUND                   | Reserva no encontrada                                        |
| USER_IS_NOT_SUPERVISOR_OR_ORGANIZER | Es una reserva supervisada y el usuario intentando hacer check-in no es ni el supervisor ni el organizador |
| USER_IS_NOT_ORGANIZER               | El usuario no es el organizador de la reserva y el control de acceso de ésta es ORGANIZER (Sólo el organizador puede hacer check-in) |
| USER_IS_NOT_ATTENDEE                | Es una reserva de espacio en la que los asistentes pueden hacer check-in, pero el usuario intentándolo no lo es |
| CHECK_IN_IS_NULL                    | La reserva no es OPTIONAL por lo que es necesario que exista un check-in |
| BOOKING_IS_NOT_CONFIRMED            | La reserva no es OPTIONAL y no está confirmada (no se ha realizado el check-in), no se puede hacer check-out |
| CHECK_OUT_UNAVAILABLE               | La reserva ya ha acabado, no se puede hacer check-out        |
| RESOURCE_NOT_FOUND                  | Recurso de la reserva no encontrado                          |
| CANCEL_EVENT_ERROR                  | (Sólo si la sincronización externa está activada) Ha ocurrido un error al hacer check-out (cancelar) la reserva en el calendario de Google / Outlook |



#### Cancelar reserva

| Código de error               | Causa(s)                                                     |
| ----------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND                | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS       | El usuario que hace la petición no tiene acceso a la organización |
| BOOKING_NOT_FOUND             | Reserva no encontrada, puede ocurrir si no se ha encontrado la reserva o si se ha encontrado pero ya ha acabado |
| USER_IS_NOT_ORGANIZER         | El usuario que intenta cancelar la reserva no es el organizador de ésta |
| CANCELLATION_REASON_NOT_FOUND | Razón de cancelación no encontrada                           |
| CANCEL_EVENT_ERROR            | (Sólo si la sincronización externa está activada) Ha ocurrido un error al cancelar la reserva en el calendario de Google / Outlook |



#### Cancelar reserva recurrente

| Código de error               | Causa(s)                                                     |
| ----------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND                | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS       | El usuario que hace la petición no tiene acceso a la organización |
| BOOKING_NOT_FOUND             | Reserva no encontrada                                        |
| USER_IS_NOT_ORGANIZER         | El usuario que intenta cancelar la reserva no es el organizador de ésta |
| CANCELLATION_REASON_NOT_FOUND | Razón de cancelación no encontrada                           |





#### Editar reserva de puesto

| Código de error                | Causa(s)                                                     |
| ------------------------------ | ------------------------------------------------------------ |
| USER_NOT_FOUND                 | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS        | El usuario que hace la petición no tiene acceso a la organización |
| BOOKING_NOT_FOUND              | Reserva no encontrada                                        |
| BOOKING_CAN_NOT_BE_MODIFIED    | La reserva no puede ser modificada, puede ocurrir si la reserva está expirada, cancelada o confirmada, o si ya ha acabado |
| START_DATE_CAN_NOT_BE_MODIFIED | La hora de inicio solo se puede modificar si el estado de la reserva es PENDING o PENDING_APPROVAL |

- Al editar una reserva de puesto se usa el método para crear una reserva de puesto, por lo que pueden ocurrir los mismos errores.



#### Editar reserva de espacio (PUT)

| Código de error                | Causa(s)                                                     |
| ------------------------------ | ------------------------------------------------------------ |
| USER_NOT_FOUND                 | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS        | El usuario que hace la petición no tiene acceso a la organización |
| BOOKING_NOT_FOUND              | Reserva no encontrada                                        |
| BOOKING_CAN_NOT_BE_MODIFIED    | La reserva no puede ser modificada, puede ocurrir si la reserva está expirada, cancelada o confirmada, o si ya ha acabado |
| START_DATE_CAN_NOT_BE_MODIFIED | La hora de inicio solo se puede modificar si el estado de la reserva es PENDING o PENDING_APPROVAL |
| CANCEL_EVENT_ERROR             | (Sólo si la sincronización externa está activada) Ha ocurrido un error al cancelar la reserva en el calendario de Google / Outlook |

- Al editar una reserva de espacio se usa el método para crear una reserva de espacio, por lo que pueden ocurrir los mismos errores.



#### Editar reserva de espacio (PATCH)

| Código de error                | Causa(s)                                                     |
| ------------------------------ | ------------------------------------------------------------ |
| USER_NOT_FOUND                 | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS        | El usuario que hace la petición no tiene acceso a la organización |
| BOOKING_NOT_FOUND              | Reserva no encontrada                                        |
| BOOKING_CAN_NOT_BE_MODIFIED    | La reserva no puede ser modificada, puede ocurrir si la reserva está expirada, cancelada o confirmada, o si ya ha acabado |
| START_DATE_CAN_NOT_BE_MODIFIED | La hora de inicio solo se puede modificar si el estado de la reserva es PENDING o PENDING_APPROVAL |
| PATCH_EVENT_ERROR              | (Sólo si la sincronización externa está activada) Ha ocurrido un error al actualizar la reserva en el calendario de Google / Outlook |



#### Obtener asistentes de una reserva

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización / El usuario intentando obtener los asistentes de la reserva no es ni el organizador ni asistente |
| BOOKING_IS_NOT_SPACE    | La reserva no es un espacio                                  |
| ATTENDEE_NOT_FOUND      | Asistente no encontrado                                      |
| BOOKING_NOT_FOUND       | Reserva no encontrada                                        |



#### Editar estado de asistente

| Código de error             | Causa(s)                                                     |
| --------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND              | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS     | El usuario que hace la petición no tiene acceso a la organización |
| ATTENDEE_NOT_FOUND          | Asistente no encontrado                                      |
| USER_IS_NOT_ATTENDEE        | El usuario al que se está intentado editar el estado no es asistente de la reserva |
| ATTENDEE_ALREADY_DECLINED   | El asistente ya ha rechazado, no se puede editar su estado   |
| ATTENDEE_DOESNT_NEED_ACTION | Si el asistente ya no necesita responder a la invitación, no se puede volver a poner ese estado |
| BOOKING_NOT_FOUND           | Reserva no encontrada                                        |



#### Crear reserva supervisada

| Código de error                     | Causa(s)                                                     |
| ----------------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND                      | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS             | El usuario que hace la petición no tiene acceso a la organización / El usuario no tiene acceso a alguno de los recursos enviados |
| INVALID_JSON                        | El JSON enviado en la petición es inválido, ocurre si la lista de recursos está vacía o directamente no se ha mandado |
| SUPERVISED_BOOKING_CONFIG_NOT_FOUND | Configuración de las reservas supervisadas no encontrada     |
| MAX_USERS_SURPASSED                 | Se ha superado la cantidad de recursos a reservar simultáneamente |
| ROLE_NOT_FOUND                      | El usuario no tiene rol móvil                                |
| USER_ROLE_NOT_AUTHORIZED            | El usuario intentando hacer la reserva no tiene el rol de gestor de equipos |
| RESOURCE_CAN_NOT_BE_DUPLICATED      | Se han enviado IDs de recursos duplicados                    |
| RESOURCE_NOT_FOUND                  | Recurso no encontrado                                        |
| RESOURCES_MUST_BE_IN_SAME_FLOOR     | Los recursos deben de estar en la misma planta               |
| INVALID_BOOKING_DATE                | La fecha de inicio o de fin no pueden ser anteriores a la actual |
| INVALID_DURATION                    | La duración no puede ser menor a 15 minutos                  |
| RESOURCE_IS_NOT_WORKSTATION         | El recurso no es un puesto                                   |
| RESOURCE_ALREADY_HAS_BOOKING        | El recurso ya está reservado                                 |



#### Asignar reserva supervisada

| Código de error                | Causa(s)                                                     |
| ------------------------------ | ------------------------------------------------------------ |
| USER_NOT_FOUND                 | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS        | El usuario que hace la petición no tiene acceso a la organización |
| INVALID_JSON                   | El JSON enviado en la petición es inválido                   |
| ROLE_NOT_FOUND                 | El usuario no tiene rol móvil                                |
| USER_ROLE_NOT_AUTHORIZED       | El usuario intentando hacer la reserva no tiene el rol de gestor de equipos |
| RESOURCE_RULE_NOT_FOUND        | Regla de recurso no encontrada                               |
| SUPERVISED_BOOKING_NOT_FOUND   | No se ha encontrado la reserva supervisada                   |
| USER_IS_NOT_SUPERVISOR         | El usuario que hace la petición no es el supervisor de la reserva |
| BOOKING_NOT_FOUND              | Reserva no encontrada                                        |
| EMAIL_CAN_NOT_BE_DUPLICATED    | Se han enviado emails duplicados                             |
| RESOURCE_CAN_NOT_BE_DUPLICATED | Se han enviado IDs de recursos duplicados                    |
| BOOKING_IS_ALREADY_ASSIGNED    | La reserva ya está asignada                                  |



#### Editar reserva supervisada

| Código de error                | Causa(s)                                                     |
| ------------------------------ | ------------------------------------------------------------ |
| USER_NOT_FOUND                 | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS        | El usuario que hace la petición no tiene acceso a la organización |
| INVALID_JSON                   | El JSON enviado en la petición es inválido                   |
| ROLE_NOT_FOUND                 | El usuario no tiene rol móvil                                |
| USER_ROLE_NOT_AUTHORIZED       | El usuario intentando hacer la reserva no tiene el rol de gestor de equipos |
| RESOURCE_RULE_NOT_FOUND        | Regla de recurso no encontrada                               |
| SUPERVISED_BOOKING_NOT_FOUND   | No se ha encontrado la reserva supervisada                   |
| USER_IS_NOT_SUPERVISOR         | El usuario que hace la petición no es el supervisor de la reserva |
| BOOKING_NOT_FOUND              | Reserva no encontrada                                        |
| EMAIL_CAN_NOT_BE_DUPLICATED    | Se han enviado emails duplicados                             |
| RESOURCE_CAN_NOT_BE_DUPLICATED | Se han enviado IDs de recursos duplicados                    |



#### Recuperar reservas supervisadas

| Código de error          | Causa(s)                                                     |
| ------------------------ | ------------------------------------------------------------ |
| USER_NOT_FOUND           | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS  | El usuario que hace la petición no tiene acceso a la organización |
| ROLE_NOT_FOUND           | El usuario no tiene rol móvil                                |
| USER_ROLE_NOT_AUTHORIZED | El usuario intentando hacer la reserva no tiene el rol de gestor de equipos |



#### Cancelar reserva supervisada

| Código de error              | Causa(s)                                                     |
| ---------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND               | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS      | El usuario que hace la petición no tiene acceso a la organización |
| ROLE_NOT_FOUND               | El usuario no tiene rol móvil                                |
| USER_ROLE_NOT_AUTHORIZED     | El usuario intentando hacer la reserva no tiene el rol de gestor de equipos |
| SUPERVISED_BOOKING_NOT_FOUND | No se ha encontrado la reserva supervisada                   |
| USER_IS_NOT_SUPERVISOR       | El usuario que hace la petición no es el supervisor de la reserva |
| BOOKING_NOT_FOUND            | Reserva no encontrada, puede ocurrir si la reserva no existe si está confirmada, expirada, cancelada o ha acabado |



#### Cancelar instancia de reserva supervisada

| Código de error              | Causa(s)                                                     |
| ---------------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND               | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS      | El usuario que hace la petición no tiene acceso a la organización |
| ROLE_NOT_FOUND               | El usuario no tiene rol móvil                                |
| USER_ROLE_NOT_AUTHORIZED     | El usuario intentando hacer la reserva no tiene el rol de gestor de equipos |
| SUPERVISED_BOOKING_NOT_FOUND | No se ha encontrado la reserva supervisada                   |
| USER_IS_NOT_SUPERVISOR       | El usuario que hace la petición no es el supervisor de la reserva |
| BOOKING_NOT_FOUND            | Reserva no encontrada, puede ocurrir si la reserva no existe si está confirmada, expirada, cancelada, ha acabado o no se ha encontrado con los criterios solicitados |





### Recursos

#### Recuperar puestos libres

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| BUILDING_NOT_FOUND      | Edificio no encontrado                                       |
| SUBCATEGORY_NOT_FOUND   | Subcategoría no encontrada                                   |





#### Recuperar espacios libres

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| BUILDING_NOT_FOUND      | Edificio no encontrado                                       |
| SUBCATEGORY_NOT_FOUND   | Subcategoría no encontrada                                   |



#### Recuperar módulos de la organización

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| ORGANIZATION_NOT_FOUND  | Organización no encontrada                                   |



#### Recuperar motivos de cancelación

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |





### Notificaciones

#### Registrar dispositivo del usuario

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| INVALID_JSON            | Petición inválida                                            |



#### Eliminar dispositivo del usuario

| Código de error         | Causa(s)                                                     |
| ----------------------- | ------------------------------------------------------------ |
| USER_NOT_FOUND          | No se ha encontrado al usuario que intenta hacer la petición |
| USER_HAS_GOT_NOT_ACCESS | El usuario que hace la petición no tiene acceso a la organización |
| INVALID_JSON            | Petición inválida                                            |
| DEVICE_NOT_FOUND        | Dispositivo no encontrado                                    |

