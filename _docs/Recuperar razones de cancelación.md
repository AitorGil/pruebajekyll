---
title: Recuperar razones de cancelación
permalink: /docs/razones-cancelacion/
---

**Versión documento: ** v1

**Creación: ** 05/07/2019

**Última modificación: ** 05/07/2019

## Razones de cancelación

Se obtienen las razones de cancelación de una organización.

### Recuperar razones de cancelación

Si el usuario no tiene acceso a dicha organización o ésta no existe, no se podran recuperar.

Sólo se recuperan las que estan activadas.

#### Request

##### HTTP request

```http
GET /api/v1/organizations/{organizationId}/cancellation
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Si se ha conseguido validar que el usuario tiene acceso a la organización, se devuelve un código `200` con las razones de cancelación, en el cuerpo de la respuesta.

```json
HTTP/1.1 200 OK
Content-type: application/json
[
    {
        "createdBy": null,
        "createdDate": null,
        "lastModifiedBy": null,
        "lastModifiedDate": null,
        "id": "aafb269b-9c8b-4e6a-8f6b-506f50e09dbc",
        "reason": "Cita médica",
        "status": "ACTIVATED",
        "organizationId": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
    }
]
```
