---
title: Creación de reservas
permalink: /docs/creacion-reserva/
---

**Versión documento: ** v1

**Creación: ** 24/06/2019

**Última modificación: ** 03/09/2019

## Reservas

Los usuarios de las aplicaciones móviles de **Bookker** tienen un alcance, dentro de su organización, que está limitado por los grupos a los que pertenece dicho usuario.

Siendo así, cada usuario tendrá la capacidad de reservar los diferentes recursos que estén asociados a alguno de los grupos del usuario.

### Crear reserva estándar

Intenta crear una / o varias reservas en los recursos indicados por el usuario.

Las reservas **solo** se crearán si se pueden realizar todas con éxito, en el momento en el que falle una el resto no se tendrá en cuenta.

#### Request

##### HTTP request

```http
Workstations

POST /api/v1/users/me/bookings/workstations/standard
POST /api/v1/users/{userId}/bookings/workstations/standard

Spaces
POST /api/v1/users/me/bookings/spaces/standard
POST /api/v1/users/{userId}/bookings/spaces/standard
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [StandardBooking](#StandardBooking).

| Property | Type                                      | Description                            | Required |
| -------- | ----------------------------------------- | -------------------------------------- | -------- |
| Booking  | List<[StandardBooking](#StandardBooking)> | Lista de reservas que se quieren crear | true     |

#### Response

Si se han conseguido crear las reserva, se devuelve un código `201` con la información de las mismas.

**Workstation**

```json
HTTP/1.1 200 OK
Content-type: application/json

 "bookings": [
    {
        "id": "92f3c58f-170d-4e23-aedf-c0d80bee05aa",
        "recurrentId": "9fe8e2ac-bc59-42a7-b80b-a312d0ce53a0",
        "startDate": 1561449600000,
        "endDate": 1561451400000,
        "duration": 1800000,
        "status": "PENDING",
        "accessControl": {
            "accessControlType": "OPTIONAL",
            "checkInDate": null,
            "checkOutDate": null
        },
        "creator": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "organizer": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "resource": {
            "id": "50b5e144-025d-4693-8645-f8c2ae450995",
            "name": "Puesto #1",
            "posterCode": "WS_01",
            "phone": "941576132",
            "mapCoordinates": {
                "topLeftX": 1,
                "topLeftY": 1,
                "bottomRightX": 1,
                "bottomRightY": 1
            },
            "approachable": true,
            "floor": {
                "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
            },
            "subcategory": {
                "id": "9badbe29-e0d3-4dfc-a4b0-1093066db89e"
            },
            "visible": true
        }
    },
    {
        "id": "55aca06d-ca57-4c30-80f7-87ff424be3b5",
        "recurrentId": "9fe8e2ac-bc59-42a7-b80b-a312d0ce53a0",
        "startDate": 1561537800000,
        "endDate": 1561541400000,
        "duration": 3600000,
        "status": "PENDING",
        "accessControl": {
            "accessControlType": "OPTIONAL",
            "checkInDate": null,
            "checkOutDate": null
        },
        "creator": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "organizer": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "resource": {
            "id": "01789b12-4cf5-4184-a8ce-c958f8924402",
            "name": "Puesto #2",
            "posterCode": "WS_02",
            "phone": "941987789",
            "mapCoordinates": {
                "topLeftX": 1,
                "topLeftY": 1,
                "bottomRightX": 1,
                "bottomRightY": 1
            },
            "approachable": true,
            "floor": {
                "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
            },
            "subcategory": {
                "id": "9badbe29-e0d3-4dfc-a4b0-1093066db89e"
            },
            "visible": true
        }
    }
]
```

**Space**

```json
 "bookings": [
    {
        "id": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
        "startDate": 1562230800000,
        "endDate": 1562234400000,
        "duration": 3600000,
        "status": "PENDING",
        "accessControl": {
            "accessControlType": "OPTIONAL",
            "checkInDate": null,
            "checkOutDate": null
        },
        "creator": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "organizer": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "resource": {
            "id": "b5fcf35f-bba2-4050-a246-631dac18e014",
            "name": "Despacho principal",
            "posterCode": "D01P3",
            "phone": "941827392",
            "mapCoordinates": {
                "topLeftX": 803,
                "topLeftY": 685,
                "bottomRightX": 1042,
                "bottomRightY": 894
            },
            "approachable": true,
            "floor": {
                "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
            },
            "subcategory": {
                "id": "9badbe29-e0d3-4dfc-a4b0-1093066db89e"
            },
            "visible": true,
            "capacity": 30
        },
        "subject": "El título de la reserva",
        "body": {
            "content": "La descripción de la reserva bla bla bla bla bla...",
            "tipo": "TEXT"
        },
        "importance": "LOW",
        "resourceType": "SPACE",
        "internalAttendees": [
            {
                "id": "c2e1035c-f5fc-47cd-a5e0-774113ea5868",
                "type": "REQUIRED",
                "status": "NEEDS_ACTION",
                "bookingId": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
                "user": {
                    "id": "fa9d9890-e9e7-4ad9-82fd-572ae925f905"
                }
            },
            {
                "id": "8cf55ab6-0ac5-4da9-bcd1-147226169b06",
                "type": "ORGANIZER",
                "status": "ACCEPTED",
                "bookingId": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
                "user": {
                    "id": "7eccd6ed-3faf-41de-bec1-0b8501316857"
                }
            }
        ],
        "externalAttendees": [
            {
                "id": "48621342-3e48-49bf-b246-186ec9344fc9",
                "type": "OPTIONAL",
                "status": "NEEDS_ACTION",
                "bookingId": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
                "email": "usuarioexterno2@gmail.com"
            },
            {
                "id": "0e2def5e-c3b7-4cc2-94ac-d4b7ef7aab8c",
                "type": "OPTIONAL",
                "status": "NEEDS_ACTION",
                "bookingId": "96c0bc4a-1960-4b67-8552-8a29b6bc7015",
                "email": "usuarioexterno1@gmail.com"
            }
        ]
    }
]
```

### Crear reserva por la cámara

Intenta crear una reserva en los recursos indicados por el usuario.

Las reservas **solo** se crearán si se pueden realizar todas con éxito, en el momento en el que falle una el resto no se tendrá en cuenta.

#### Request

##### HTTP request

```http
Workstations

POST /api/v1/users/me/bookings/workstations/camera
POST /api/v1/users/{userId}/bookings/workstations/camera

Spaces
POST /api/v1/users/me/bookings/spaces/camera
POST /api/v1/users/{userId}/bookings/spaces/camera
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Header             | Value             | Required |
| ------------------ | ----------------- | -------- |
| presenceValidation | d8:c7:c8:cc:43:25 | false    |

Ejemplo:

```html
POST
/api/v1/users/me/bookings/workstations/camera?presenceValidation=d8:c7:c8:cc:43:25
```

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [CameraBooking](#CameraBooking).

| Property | Type                            | Description                 | Required |
| -------- | ------------------------------- | --------------------------- | -------- |
| Booking  | [CameraBooking](#CameraBooking) | Reserva que se quiere crear | true     |

#### Response

Si se han conseguido crear las reserva, se devuelve un código `201` con la información de las mismas.

**Workstation**

```json
HTTP/1.1 200 OK
Content-type: application/json

 "bookings": [
    {
        "id": "04f89698-ec5e-4753-b672-9887ebc0ffd3",
        "startDate": 1561982202536,
        "endDate": 1561986000000,
        "duration": 3797464,
        "status": "CONFIRMED",
        "accessControl": {
            "accessControlType": "OPTIONAL",
            "checkInDate": "2019-07-01T11:56:42.536+0000",
            "checkOutDate": null
        },
        "creator": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "organizer": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "resource": {
            "id": "01789b12-4cf5-4184-a8ce-c958f8924402",
            "name": "Puesto #2",
            "posterCode": "C07P2",
            "phone": "941987789",
            "mapCoordinates": {
                "topLeftX": 441,
                "topLeftY": 3226,
                "bottomRightX": 489,
                "bottomRightY": 3274
            },
            "approachable": true,
            "floor": {
                "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
            },
            "subcategory": {
                "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
            },
            "visible": true
        },
        "resourceType": "WORKSTATION"
    }
]
```

**Space**

```json
 "bookings": [
    {
        "id": "28f1ac76-cff5-438c-b8c4-1bd7ec1d9f55",
        "startDate": 1561980464713,
        "endDate": 1561986000000,
        "duration": 5535287,
        "status": "CONFIRMED",
        "accessControl": {
            "accessControlType": "OPTIONAL",
            "checkInDate": "2019-07-01T11:27:44.713+0000",
            "checkOutDate": null
        },
        "creator": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "organizer": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "resource": {
            "id": "b5fcf35f-bba2-4050-a246-631dac18e014",
            "name": "Despacho principal",
            "posterCode": "D01P3",
            "phone": "941827392",
            "mapCoordinates": {
                "topLeftX": 803,
                "topLeftY": 685,
                "bottomRightX": 1042,
                "bottomRightY": 894
            },
            "approachable": true,
            "floor": {
                "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
            },
            "subcategory": {
                "id": "9badbe29-e0d3-4dfc-a4b0-1093066db89e"
            },
            "visible": true,
            "capacity": 30
        },
        "subject": "El título de la reserva",
        "body": {
            "content": "La descripción de la reserva bla bla bla bla bla...",
            "tipo": "TEXT"
        },
        "importance": "LOW",
        "resourceType": "SPACE",
        "internalAttendees": [
            {
                "id": "7295f3c6-abee-4c28-8292-1ac200ce79c2",
                "type": "REQUIRED",
                "status": "NEEDS_ACTION",
                "bookingId": "28f1ac76-cff5-438c-b8c4-1bd7ec1d9f55",
                "user": {
                    "id": "fa9d9890-e9e7-4ad9-82fd-572ae925f905"
                }
            },
            {
                "id": "15731533-b82c-4149-9eb2-23117711fac0",
                "type": "ORGANIZER",
                "status": "ACCEPTED",
                "bookingId": "28f1ac76-cff5-438c-b8c4-1bd7ec1d9f55",
                "user": {
                    "id": "7eccd6ed-3faf-41de-bec1-0b8501316857"
                }
            }
        ],
        "externalAttendees": [
            {
                "id": "b87a8696-bab9-4752-a637-2d4f7a0182ee",
                "type": "OPTIONAL",
                "status": "NEEDS_ACTION",
                "bookingId": "28f1ac76-cff5-438c-b8c4-1bd7ec1d9f55",
                "email": "usuarioexterno2@gmail.com"
            },
            {
                "id": "26591a9d-ec90-4be7-bb6e-1fe68a939c4e",
                "type": "OPTIONAL",
                "status": "NEEDS_ACTION",
                "bookingId": "28f1ac76-cff5-438c-b8c4-1bd7ec1d9f55",
                "email": "usuarioexterno1@gmail.com"
            }
        ]
    }
]
```

### Crear reserva en un click

Intenta crear una reserva en el piso / edificio elegido por el usuario.

#### Request

##### HTTP request

```http
Workstations

POST /api/v1/users/me/bookings/workstations/oneclick
POST /api/v1/users/{userId}/bookings/workstations/oneclick
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [StandardBooking](#StandardBooking).

| Property | Type                                | Description                 | Required |
| -------- | ----------------------------------- | --------------------------- | -------- |
| Booking  | [OneClickBooking](#OneClickBooking) | Reserva que se quiere crear | true     |

#### Response

Si se ha conseguido crear la reserva, se devuelve un código `201` con la información de las misma.

**Workstation**

```json
HTTP/1.1 200 OK
Content-type: application/json

 "bookings": [
    {
        "id": "92f3c58f-170d-4e23-aedf-c0d80bee05aa",
        "recurrentId": "9fe8e2ac-bc59-42a7-b80b-a312d0ce53a0",
        "startDate": 1561449600000,
        "endDate": 1561451400000,
        "duration": 1800000,
        "status": "PENDING",
        "accessControl": {
            "accessControlType": "OPTIONAL",
            "checkInDate": null,
            "checkOutDate": null
        },
        "creator": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "organizer": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "resource": {
            "id": "50b5e144-025d-4693-8645-f8c2ae450995",
            "name": "Puesto #1",
            "posterCode": "WS_01",
            "phone": "941576132",
            "mapCoordinates": {
                "topLeftX": 1,
                "topLeftY": 1,
                "bottomRightX": 1,
                "bottomRightY": 1
            },
            "approachable": true,
            "floor": {
                "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
            },
            "subcategory": {
                "id": "9badbe29-e0d3-4dfc-a4b0-1093066db89e"
            },
            "visible": true
        }
    },
    {
        "id": "55aca06d-ca57-4c30-80f7-87ff424be3b5",
        "recurrentId": "9fe8e2ac-bc59-42a7-b80b-a312d0ce53a0",
        "startDate": 1561537800000,
        "endDate": 1561541400000,
        "duration": 3600000,
        "status": "PENDING",
        "accessControl": {
            "accessControlType": "OPTIONAL",
            "checkInDate": null,
            "checkOutDate": null
        },
        "creator": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "organizer": {
            "id": "7eccd6ed-3faf-41de-bec1-0b8501316857",
            "name": "Aitor",
            "surname": "Gil",
            "alias": "AITORGC",
            "email": "aitor.gil@bookkercorp.com",
            "phone": "631256311",
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
        "resource": {
            "id": "01789b12-4cf5-4184-a8ce-c958f8924402",
            "name": "Puesto #2",
            "posterCode": "WS_02",
            "phone": "941987789",
            "mapCoordinates": {
                "topLeftX": 1,
                "topLeftY": 1,
                "bottomRightX": 1,
                "bottomRightY": 1
            },
            "approachable": true,
            "floor": {
                "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
            },
            "subcategory": {
                "id": "9badbe29-e0d3-4dfc-a4b0-1093066db89e"
            },
            "visible": true
        }
    }
]
```

### StandardBooking

**Workstation**

```json
{
  "resource": {
    "id": "50b5e144-025d-4693-8645-f8c2ae450995"
  },
  "startDate": 1561557600000,
  "endDate": 1561559400000
}
```

**Space**

```json
[
  {
    "resource": {
      "id": "b5fcf35f-bba2-4050-a246-631dac18e014"
    },
    "startDate": 1562230800000,
    "endDate": 1562234400000,
    "importance": "LOW",
    "subject": "El título de la reserva",
    "body": {
      "content": "La descripción de la reserva bla bla bla bla bla...",
      "bodyType": "TEXT"
    },
    "internalAttendees": [
      {
        "type": "REQUIRED",
        "user": {
          "id": "fa9d9890-e9e7-4ad9-82fd-572ae925f905"
        }
      }
    ],
    "externalAttendees": [
      {
        "type": "OPTIONAL",
        "email": "usuarioexterno1@gmail.com"
      },
      {
        "type": "OPTIONAL",
        "email": "usuarioexterno2@gmail.com"
      }
    ]
  }
]
```

### CameraBooking

**Workstation**

```json
[
  {
    "resource": {
      "posterCode": "C07P2"
    },
    "endDate": 1561986000000
  }
]
```

**Space**

```json
[
  {
    "resource": {
      "posterCode": "D01P3"
    },
    "endDate": 1561986000000,
    "importance": "LOW",
    "subject": "El título de la reserva",
    "body": {
      "content": "La descripción de la reserva bla bla bla bla bla...",
      "bodyType": "TEXT"
    },
    "internalAttendees": [
      {
        "type": "REQUIRED",
        "user": {
          "id": "fa9d9890-e9e7-4ad9-82fd-572ae925f905"
        }
      }
    ],
    "externalAttendees": [
      {
        "type": "OPTIONAL",
        "email": "usuarioexterno1@gmail.com"
      },
      {
        "type": "OPTIONAL",
        "email": "usuarioexterno2@gmail.com"
      }
    ]
  }
]
```

### OneClickBooking

**Workstation**

```json
{
  "resource": {
    "floor": {
      "building": {
        "id": "5068c634-064d-4e15-b17f-1a420c68f051"
      }
    },
    "subcategory": {
      "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
    }
  },
  "startDate": 1566565200000,
  "endDate": 1566568800000
}
```
