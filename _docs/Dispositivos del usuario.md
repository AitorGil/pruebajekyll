---
title: Dispositivos del usuario
permalink: /docs/dispositivos-del-usuario/
---

**Versión documento: ** v1

**Creación: ** 30/08/2019

**Última modificación: ** 30/08/2019

## Dispositivos

Los usuarios de las aplicaciones móviles de **Bookker** tienen la posibilidad de registrar diferentes dispositivos móviles a los cuales les llegarán las diferentes notificaciones push que se generan.

Es importante tener en cuenta que un dispositivo que esté inactivo más de 7 días dejará de recibir notificaciones.

### Registrar dispositivo

Intenga registrar un dispositivo para un usuario. En caso de que el dispositivo ya existiese, solo se actualizaría su información de último uso.

#### Request

##### HTTP request

```http
POST /api/v1/users/me/devices
POST /api/v1/users/{userId}/devices
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [Device](#Device).

| Type              | Description                        | Required |
| ----------------- | ---------------------------------- | -------- |
| [Device](#Device) | Dispositivo que quieres registrar. | true     |

#### Response

Si se han conseguido registrar el dispositivo, se devuelve un código `201`.

### Eliminar dispositivo

Intenga eliminar un dispositivo de un usuario.

#### Request

##### HTTP request

```http
DELETE /api/v1/users/me/devices/{token}
DELETE /api/v1/users/{userId}/{token}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Si se han conseguido registrar el dispositivo, se devuelve un código `204`.

### Device

```json
{
  "token": "TOKENDELDISPOSITIVO",
  "platform": "APNS"
}
```

| Type         | Description                                                   |
| ------------ | ------------------------------------------------------------- |
| APNS         | Servicio de notificaciones push de Apple.                     |
| APNS_SANDBOX | Versión Sandbox del servicio de notificaciones push de Apple. |
| GCM          | Servicio de notificaciones push de Google.                    |
