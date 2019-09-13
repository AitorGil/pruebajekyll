---
title: Recuperar contactos del usuario
permalink: /docs/recuperar-contactos-usuario/
---

**Versión documento: ** v1

**Creación: ** 24/06/2019

**Última modificación: ** 04/07/2019

## Contactos del usuario

Se obtienen los contactos del usuario solicitado, es decir, los usuarios que se encuentran en su misma organización.

También se devuelven los contactos favoritos del usuario.

### Recuperar recursos del usuario

Intenta recuperar los contactos del usuario. Se puede enviar una fecha, en milisegundos, de última actualización de los contactos para evitar descargarlos si no ha habido cambios.

También se devuelve una lista con los contactos favoritos de los usuarios. Esta lista se devuelve siempre independientemente de la fecha de versión que se envíe.

#### Request

##### HTTP request

```http
GET /api/v1/users/me/contacts
GET /api/v1/users/{userId}/contacts
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Param        | Value                                           | Required |
| ------------ | ----------------------------------------------- | -------- |
| contactsDate | Long - Fecha de última versión en milisegundos. | false    |

#### Response

Si se ha conseguido validar que el usuario tiene acceso para realizar la petición, se devuelve un código `200` con los contactos del usuario, en el cuerpo de la respuesta.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "favoriteContacts": [
        {
            "id": "0acc7e61-aff1-4463-bc93-f341e21d9499",
            "name": "Ramón",
            "surname": "Carnero",
            "alias": "RAMONC",
            "email": "ramon.carnero@bookkercorp.com",
            "phone": "667234171",
            "organization": {
                "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
            },
            "department": {
                "id": "26980ebb-0ac7-4bb0-bab1-81ed8fc07d59"
            },
            "userRule": {
                "id": "d58b188f-6ba6-48c4-9e0a-dd0ac81d4cb2"
            },
            "mobileRole": {
                "id": "5220b6a2-8920-4dae-8ff0-ba96707d439d"
            }
        },
        {
            "id": "a3bc38dc-837e-403e-8486-de523686442a",
            "name": "Javier",
            "surname": "Ureta",
            "alias": "JAVIERU",
            "email": "javier.ureta@bookkercorp.com",
            "phone": "668010812",
            "organization": {
                "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
            },
            "department": {
                "id": "26980ebb-0ac7-4bb0-bab1-81ed8fc07d59"
            },
            "userRule": {
                "id": "d58b188f-6ba6-48c4-9e0a-dd0ac81d4cb2"
            },
            "mobileRole": {
                "id": "5220b6a2-8920-4dae-8ff0-ba96707d439d"
            }
        }
    ],
    "contactsDate": 1561365646000,
    "contacts": [
        {
            "id": "0acc7e61-aff1-4463-bc93-f341e21d9499",
            "name": "Ramón",
            "surname": "Carnero",
            "alias": "RAMONC",
            "email": "ramon.carnero@bookkercorp.com",
            "phone": "667234171",
            "organization": {
                "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
            },
            "department": {
                "id": "26980ebb-0ac7-4bb0-bab1-81ed8fc07d59"
            },
            "userRule": {
                "id": "d58b188f-6ba6-48c4-9e0a-dd0ac81d4cb2"
            },
            "mobileRole": {
                "id": "5220b6a2-8920-4dae-8ff0-ba96707d439d"
            }
        },
        {
            "id": "3ed0b44e-8efd-4e35-ae17-56e80904d47d",
            "name": "Jorge",
            "surname": "Castan",
            "alias": "JORGEC",
            "email": "jorge.castan@bookkercorp.com",
            "phone": "643123151",
            "organization": {
                "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
            },
            "department": {
                "id": "26980ebb-0ac7-4bb0-bab1-81ed8fc07d59"
            },
            "userRule": {
                "id": "d58b188f-6ba6-48c4-9e0a-dd0ac81d4cb2"
            },
            "mobileRole": {
                "id": "5220b6a2-8920-4dae-8ff0-ba96707d439d"
            }
        }
    ]
}
```

### Añadir contacto a favoritos

Añade un contacto a la lista de favoritos del usuario.

#### Request

##### HTTP request

```http
POST /api/v1/users/me/contacts/{contactId}
POST /api/v1/users/{userId}/contacts/{contactId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Si se ha conseguido añadir el contacto a la lista de favoritos del usuario, se devuelve un código `201`.

```json
HTTP/1.1 201 Created
```

### Quitar contacto de favoritos

Quita un contacto a la lista de favoritos del usuario.

#### Request

##### HTTP request

```http
DELETE /api/v1/users/me/contacts/{contactId}
DELETE /api/v1/users/{userId}/contacts/{contactId}
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Si se ha conseguido quitar el contacto a la lista de favoritos del usuario, se devuelve un código `204`.

```json
HTTP/1.1 204 No Content
```
