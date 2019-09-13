---
title: Actualizar perfil de Usuario
permalink: /docs/actualizar-perfil-de-usuario/
---

**Versión documento: ** v1

**Creación: ** 19/08/2019

**Última modificación: ** 10/09/2019

### Actualizar el perfil del usuario

En el perfil del usuario podemos encontrar el consentimiento del usuario a ser buscado a traves de la aplicación y la configuración de las notificaciones del usuario.

Con respecto a las notificaciones existen dos tipos:

| Type  |
| ----- |
| PUSH  |
| EMAIL |

No todas las notificaciones pueden ser configuradas para ambos tipos, quedando las opciones de configuración de la siguiente manera:

| Notification           | PUSH   | EMAIL  |
| ---------------------- | ------ | ------ |
| Booking Updates        | Sí     | Sí     |
| ~~Booking Updates MP~~ | ~~No~~ | ~~No~~ |
| Booking Invitation     | No     | Sí     |
| Booking Expiration     | No     | Sí     |

**Importante**

Por el momento la notificación "Booking Updates MP" no se tendrá en cuenta, por tanto, no hace falta mostrarla en la vista de configuración.

#### Request

##### HTTP request

```http
PATCH /api/v1/users/me
PATCH /api/v1/users/{userId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [UserProfile](#UserProfile).

| Type                        | Description         | Required |
| --------------------------- | ------------------- | -------- |
| [UserProfile](#UserProfile) | Perfil del usuario. | true     |

#### Response

Se devuelve un código `200`.

### UserProfile

```json
{
  "canBeSearched": true,
  "bookingUpdates": "PUSH",
  "bookingUpdatesMp": "",
  "bookingInvitation": "PUSH;",
  "bookingExpiration": "PUSH;EMAIL;"
}
```
