---
title: Recuperar reservas supervisadas
permalink: /docs/recuperar-reservas-supervisadas/
---

**Versión documento: ** v1

**Creación: ** 02/09/2019

**Última modificación: ** 05/09/2019

### Recuperar reservas

Permite recuperar las reservas supervisadas de un usuario supervisor

A tener en cuenta:

- Sólo se obtendrán las reservas que tengan estado **PENDING** o **CONFIRMED**.

- Sólo se obtendrán las reservas cuya fecha de fin no sea mayor que la fecha actual

### Request

##### HTTP Request

```http
GET /api/v1/users/me/bookings/supervised
GET /api/v1/users/{userId}/bookings/supervised
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

### Response

Si todo ha ido correctamente se devuelve un código `200`, con las reservas supervisadas del usuario.

```json
[
  {
    "supervisedBookingId": "175edf83-df85-41b9-b3ab-8e516e039448",
    "title": "varios",
    "floorId": "1ed6c4c3-a6c1-415b-bee4-0ca3323c51f7",
    "bookingList": [
      {
        "startDate": 1567746000000,
        "endDate": 1567746900000,
        "assignationInfoList": [
          {
            "userEmail": "david.navarro@bookkercorp.com",
            "resource": {
              "id": "fa6bb859-575e-4771-a03b-fafbc9935d6a",
              "name": "Puesto 5 P3",
              "posterCode": "A05P3",
              "externalSyncEmail": "sala.negro@kabel.es",
              "phone": "967432831",
              "mapCoordinates": {
                "topLeftX": 144,
                "topLeftY": 3000,
                "bottomRightX": 194,
                "bottomRightY": 3048
              },
              "approachable": true,
              "floor": {
                "id": "1ed6c4c3-a6c1-415b-bee4-0ca3323c51f7"
              },
              "subcategory": {
                "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
              },
              "visible": true
            },
            "bookingId": "29ac4185-b955-4c1a-b823-0c5d9430a859",
            "userCheckInInfo": {
              "checkedIn": false,
              "checkedOut": false
            }
          },
          {
            "userEmail": "aitor.gil@bookercorp.com",
            "resource": {
              "id": "902895dd-72eb-4abb-a11f-c4164ec9f72f",
              "name": "Puesto 3 P3",
              "posterCode": "A03P3",
              "externalSyncEmail": "puesto03p3@resource.com",
              "phone": "989731231",
              "mapCoordinates": {
                "topLeftX": 292,
                "topLeftY": 3226,
                "bottomRightX": 340,
                "bottomRightY": 3274
              },
              "approachable": true,
              "floor": {
                "id": "1ed6c4c3-a6c1-415b-bee4-0ca3323c51f7"
              },
              "subcategory": {
                "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
              },
              "visible": true
            },
            "bookingId": "3e414b31-fd91-44f0-a4e3-80536350232e",
            "userCheckInInfo": {
              "checkedIn": false,
              "checkedOut": false
            }
          },
          {
            "userEmail": "aitor.gomez@bookercorp.com",
            "resource": {
              "id": "d048868a-32dd-406c-8411-5578581b12a0",
              "name": "Puesto 4 P3",
              "posterCode": "A04P3",
              "externalSyncEmail": "puesto04p3@resource.com",
              "phone": "963127831",
              "mapCoordinates": {
                "topLeftX": 209,
                "topLeftY": 3226,
                "bottomRightX": 258,
                "bottomRightY": 3274
              },
              "approachable": true,
              "floor": {
                "id": "1ed6c4c3-a6c1-415b-bee4-0ca3323c51f7"
              },
              "subcategory": {
                "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
              },
              "visible": true
            },
            "bookingId": "cf90cbca-ebd2-4274-a667-e2561ba4a413",
            "userCheckInInfo": {
              "checkedIn": false,
              "checkedOut": false
            }
          }
        ]
      },
      {
        "startDate": 1567832400000,
        "endDate": 1567833300000,
        "assignationInfoList": [
          {
            "userEmail": "aitor.gomez@bookercorp.com",
            "resource": {
              "id": "d048868a-32dd-406c-8411-5578581b12a0",
              "name": "Puesto 4 P3",
              "posterCode": "A04P3",
              "externalSyncEmail": "puesto04p3@resource.com",
              "phone": "963127831",
              "mapCoordinates": {
                "topLeftX": 209,
                "topLeftY": 3226,
                "bottomRightX": 258,
                "bottomRightY": 3274
              },
              "approachable": true,
              "floor": {
                "id": "1ed6c4c3-a6c1-415b-bee4-0ca3323c51f7"
              },
              "subcategory": {
                "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
              },
              "visible": true
            },
            "bookingId": "c1e8b299-c1f4-48c1-ae1a-2fd0f758b627",
            "userCheckInInfo": {
              "checkedIn": false,
              "checkedOut": false
            }
          },
          {
            "userEmail": "aitor.gil@bookercorp.com",
            "resource": {
              "id": "902895dd-72eb-4abb-a11f-c4164ec9f72f",
              "name": "Puesto 3 P3",
              "posterCode": "A03P3",
              "externalSyncEmail": "puesto03p3@resource.com",
              "phone": "989731231",
              "mapCoordinates": {
                "topLeftX": 292,
                "topLeftY": 3226,
                "bottomRightX": 340,
                "bottomRightY": 3274
              },
              "approachable": true,
              "floor": {
                "id": "1ed6c4c3-a6c1-415b-bee4-0ca3323c51f7"
              },
              "subcategory": {
                "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
              },
              "visible": true
            },
            "bookingId": "c7796be6-b6b7-4b92-98fa-1f732da1d67a",
            "userCheckInInfo": {
              "checkedIn": false,
              "checkedOut": false
            }
          },
          {
            "userEmail": "david.navarro@bookkercorp.com",
            "resource": {
              "id": "fa6bb859-575e-4771-a03b-fafbc9935d6a",
              "name": "Puesto 5 P3",
              "posterCode": "A05P3",
              "externalSyncEmail": "sala.negro@kabel.es",
              "phone": "967432831",
              "mapCoordinates": {
                "topLeftX": 144,
                "topLeftY": 3000,
                "bottomRightX": 194,
                "bottomRightY": 3048
              },
              "approachable": true,
              "floor": {
                "id": "1ed6c4c3-a6c1-415b-bee4-0ca3323c51f7"
              },
              "subcategory": {
                "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
              },
              "visible": true
            },
            "bookingId": "f5fb73cf-7e90-4382-b85d-8a7a7f237c1a",
            "userCheckInInfo": {
              "checkedIn": false,
              "checkedOut": false
            }
          }
        ]
      }
    ]
  }
]
```
