---
title: Lista de códigos de error
permalink: /docs/codigos-error/
---

**Fecha de creación:** 09/09/2019

**Fecha de modificación:** 10/09/2019

Si el mensaje a mostrar está vacío, mostrar un mensaje genérico (o sólo el código de error numérico).

| Código de error                     | Mensaje a mostrar                                                    | Código de error numérico |
| ----------------------------------- | -------------------------------------------------------------------- | ------------------------ |
| USER_NOT_FOUND                      |                                                                      | 1000                     |
| ROLE_NOT_FOUND                      |                                                                      | 1001                     |
| RESOURCE_NOT_FOUND                  |                                                                      | 1002                     |
| WORKSTATION_NOT_FOUND               |                                                                      | 1003                     |
| SUBCATEGORY_NOT_FOUND               |                                                                      | 1004                     |
| SPACE_NOT_FOUND                     |                                                                      | 1005                     |
| ORGANIZATION_NOT_FOUND              |                                                                      | 1006                     |
| FLOOR_NOT_FOUND                     |                                                                      | 1007                     |
| DICTIONARY_NOT_FOUND                |                                                                      | 1008                     |
| DEPARTMENT_NOT_FOUND                |                                                                      | 1009                     |
| BUILDING_NOT_FOUND                  |                                                                      | 1010                     |
| BOOKING_NOT_FOUND                   | Reserva no encontrada                                                | 1011                     |
| USER_RULE_NOT_FOUND                 |                                                                      | 1012                     |
| RESOURCE_RULE_NOT_FOUND             |                                                                      | 1013                     |
| RESOURCE_GROUP_NOT_FOUND            |                                                                      | 1014                     |
| USER_GROUP_NOT_FOUND                | No tienes acceso a este recurso                                      | 1015                     |
| CANCELLATION_REASON_NOT_FOUND       |                                                                      | 1016                     |
| ATTENDEE_NOT_FOUND                  |                                                                      | 1017                     |
| ATTENDEE_STATUS_DOESNT_EXIST        |                                                                      | 1018                     |
| OUTLOOK_CREDENTIALS_NOT_FOUND       |                                                                      | 1019                     |
| GOOGLE_CREDENTIALS_NOT_FOUND        |                                                                      | 1020                     |
| GOOGLE_VERIFICATION_KEY_NOT_FOUND   |                                                                      | 1021                     |
| GOOGLE_CHANNEL_NOT_FOUND            |                                                                      | 1022                     |
| SUBSCRIPTION_NOT_FOUND              |                                                                      | 1023                     |
| DEVICE_NOT_FOUND                    |                                                                      | 1024                     |
| SUPERVISED_BOOKING_NOT_FOUND        |                                                                      | 1025                     |
| SUPERVISED_BOOKING_CONFIG_NOT_FOUND |                                                                      | 1026                     |
| INVALID_BOOKING_DATE                | Fecha inválida                                                       | 1027                     |
| INVALID_JSON                        |                                                                      | 1028                     |
| RECURRENCE_NOT_ALLOWED              |                                                                      | 1029                     |
| USER_HAS_GOT_NOT_ROLE               |                                                                      | 1030                     |
| USER_HAS_GOT_NOT_ACCESS             | No tienes acceso                                                     | 1031                     |
| USER_IS_NOT_INTERNAL                |                                                                      | 1032                     |
| USER_IS_NOT_ORGANIZER               |                                                                      | 1033                     |
| USER_IS_NOT_ATTENDEE                |                                                                      | 1034                     |
| USER_IS_NOT_SUPERVISOR              | No puedes editar / cancelar esta reserva                             | 1035                     |
| USER_IS_NOT_SUPERVISOR_OR_ORGANIZER | No puedes hacer check-in en esta reserva                             | 1036                     |
| USER_ROLE_NOT_AUTHORIZED            | No tienes los permisos necesarios                                    | 1037                     |
| PRESENCE_VALIDATION_REQUIRED        |                                                                      | 1038                     |
| WRONG_PRESENCE_VALIDATION           |                                                                      | 1039                     |
| USER_ALREADY_HAS_BOOKING            | Ya tienes una reserva en este momento                                | 1040                     |
| RESOURCE_ALREADY_HAS_BOOKING        | El recurso ya tiene una reserva para esa fecha                       | 1041                     |
| INVALID_RESOURCE_SCHEDULE           | La fecha de la reserva está fuera del rango permitido por el recurso | 1042                     |
| INVALID_ADVANCE_DAYS                | No puedes reservar este recurso con tanta antelación                 | 1043                     |
| INVALID_USER_WORKING_DAY            | La duración de tus reservas supera el tiempo de tu jornada laboral   | 1044                     |
| INVALID_SPACE_MAX_BOOKING           | La duración de tus reservas en este recurso supera el máximo         | 1045                     |
| INVALID_DURATION                    | La duración tiene que ser al menos de 15 minutos                     | 1046                     |
| RESOURCE_NOT_ACTIVATED              | Este recurso no está disponible                                      | 1047                     |
| RESOURCE_HAS_NO_RULES               |                                                                      | 1048                     |
| CHECK_IN_EXPIRED                    | El check-in ha caducado                                              | 1049                     |
| START_DATE_CAN_NOT_BE_MODIFIED      | No se puede modificar la fecha de inicio de la reserva               | 1050                     |
| BOOKING_CAN_NOT_BE_MODIFIED         | No se puede modificar la reserva                                     | 1051                     |
| CHECK_IN_NOT_ACTIVE_YET             | Todavía no puedes hacer check-in                                     | 1052                     |
| CHECK_IN_IS_NULL                    |                                                                      | 1053                     |
| CHECK_OUT_UNAVAILABLE               | El check-out no está disponible                                      | 1054                     |
| BOOKING_IS_NOT_CONFIRMED            |                                                                      | 1055                     |
| BOOKING_ALREADY_FINISHED            | La reserva ya ha acabado                                             | 1056                     |
| ATTENDEE_ALREADY_DECLINED           |                                                                      | 1057                     |
| ATTENDEE_DOESNT_NEED_ACTION         |                                                                      | 1058                     |
| CONTACT_NOT_FOUND                   |                                                                      | 1059                     |
| BOOKING_IS_NOT_SPACE                |                                                                      | 1060                     |
| USER_CAN_NOT_BE_SEARCHED            | El usuario no puede ser buscado                                      | 1061                     |
| MODULE_IS_NOT_ACTIVE                |                                                                      | 1062                     |
| MAX_USERS_SURPASSED                 |                                                                      | 1063                     |
| EMAIL_CAN_NOT_BE_DUPLICATED         | No puedes asignar el mismo usuario varias veces                      | 1064                     |
| RESOURCE_CAN_NOT_BE_DUPLICATED      |                                                                      | 1065                     |
| BOOKING_IS_ALREADY_ASSIGNED         |                                                                      | 1066                     |
| RESOURCE_IS_NOT_WORKSTATION         |                                                                      | 1067                     |
| RESOURCES_MUST_BE_IN_SAME_FLOOR     |                                                                      | 1068                     |
| RESOURCE_HAS_NO_EMAIL               |                                                                      | 1069                     |
| EMAIL_NOT_SENT                      |                                                                      | 1070                     |
| UNKNOWN_EXTERNAL_SYNC_TYPE          |                                                                      | 1071                     |
| AUTHENTICATION_ERROR                |                                                                      | 1072                     |
| EXT_SYNC_SERVICE_ERROR              |                                                                      | 1073                     |
| CANCEL_EVENT_ERROR                  |                                                                      | 1074                     |
| PATCH_EVENT_ERROR                   |                                                                      | 1075                     |
| GET_CHANGED_EVENTS_ERROR            |                                                                      | 1076                     |
| UPDATE_EVENT_ERROR                  |                                                                      | 1077                     |
| CREATE_EVENT_ERROR                  |                                                                      | 1078                     |
| LIST_EVENTS_ERROR                   |                                                                      | 1079                     |
