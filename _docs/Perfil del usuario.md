---
title: Perfil del usuario
permalink: /docs/perfil-usuario/
---

**Versión documento: ** v1

**Creación: ** 03/09/2019

**Última modificación: ** 03/09/2019

## Recuperar el perfil de un usuario

Recupera la información del perfil de un usuario, así como información sobre su configuración.

### Request

##### HTTP request

```http
GET /api/v1/users/me
GET /api/v1/users/{userId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

### Response

Se devuelve un código `200` con la información básica del usuario.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
    "name": "Aitor",
    "surname": "Gil",
    "alias": "AITORGC",
    "email": "aitor.gil@bookkercorp.com",
    "phone": "631256311",
    "organization": {
        "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba",
        "name": "Bookker",
        "type": "BUSINESS",
        "email": "prueba@prueba.es",
        "phone": "941789172"
    },
    "department": {
        "id": "26980ebb-0ac7-4bb0-bab1-81ed8fc07d59",
        "name": "Departamento de Desarrollo",
        "organization": {
            "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
        }
    },
    "userRule": {
        "id": "d58b188f-6ba6-48c4-9e0a-dd0ac81d4cb2"
    },
    "mobileRole": {
        "id": "1dfde059-da65-49c9-8db3-dccc4f3292e4",
        "name": "TEAM_MANAGER"
    },
    "canBeSearched": true,
    "notificationConfig": {
        "createdBy": null,
        "createdDate": "2019-09-02T08:36:59.000+0000",
        "lastModifiedBy": null,
        "lastModifiedDate": "2019-09-02T08:37:13.000+0000",
        "id": "7f320947-adb0-4c6c-8c6d-d238b9e49c88",
        "bookingUpdates": "PUSH;",
        "bookingUpdatesMp": "",
        "bookingInvitation": "PUSH;",
        "bookingExpiration": "EMAIL;PUSH;",
        "userId": "7eccd6ed-3faf-41de-bec1-0b8501316857"
    }
}
```
