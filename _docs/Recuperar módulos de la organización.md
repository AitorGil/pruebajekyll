---
title: Recuperar módulos de la organización
permalink: /docs/modulos-organizacion/
---

**Versión documento: ** v1

**Creación: ** 04/07/2019

**Última modificación: ** 04/07/2019

## Módulos de la organización

Los módulos de la organización, son las funcionalidades "extra" que pueden estar activadas o no.

Podemos encontrar los siguientes módulos:

- **Sincronización externa**: Sincronización de las reservas con plataformas de terceros como Outlook o Google.

  Hay dos tipos de sincronización:

  - **Unidireccional**: La sincronización solo funciona en el sentido (Bookker -> Plataforma Externa), es decir, los eventos creados en Bookker son reflejados en los calendarios de los usuarios en la plataforma elegida.
  - **Bidireccional**: La sincronización funciona en ambos sentidos (Bookker <-> Plataforma Externa), es decir, los eventos creados en Bookker son reflejados en los calendarios de los recursos y usuarios en la plataforma elegida y los eventos creados en la plataforma externa son reflejados en el sistema de Bookker.

| Value                  | Description                                     |
| ---------------------- | ----------------------------------------------- |
| NONE                   | No tiene sincronziación externa.                |
| OUTLOOK_UNIDIRECTIONAL | Tiene sincronización unidirecional con Outlook. |
| OUTLOOK_BIDIRECTIONAL  | Tiene sincronización bidirecional con Outlook.  |
| GOOGLE_UNIDIRECTIONAL  | Tiene sincronización unidirecional con Google.  |
| GOOGLE_BIDIRECTIONAL   | Tiene sincronización bidirecional con Google.   |

- **Búsqueda de empleado**: Localización de los empleados mediante el sistema de reservas de Bookker.

| Value | Descriptión                                                 |
| ----- | ----------------------------------------------------------- |
| true  | La organización tiene activada la búsqueda de empleados.    |
| false | La organización no tiene activada la búsqueda de empleados. |

- **Validación de presencia**: Control de la presencia obligatorio para ciertas acciones dentro del sistema, por ejemplo el Check-In.

| Value       | Description                                            |
| ----------- | ------------------------------------------------------ |
| NONE        | No tiene validación de presencia.                      |
| WIFI        | Tiene validación de presencia mediante wifi.           |
| BEACON      | Tiene validación de presencia mediante beacons.        |
| WIFI_BEACON | Tiene validación de presencia mediante wifi y beacons. |
| SITUM       | Tiene validación de presencia mediante Situm.          |

### Recuperar módulos de la organización

Intenta recuperar la configuración de los módulos que tiene la organización.

#### Request

##### HTTP request

```http
GET /api/v1/users/me/organizations/{organizationId}
GET /api/v1/users/{userId}/organizations/{organizationId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Se devuelve un código `200` con la información de los módulos de la organización.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "organizationId": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba",
    "externalSynchronization": "NONE",
    "employeeSearch": false,
    "presenceValidation": "NONE"
}
```
