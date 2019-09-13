---
title: Creación de reserva supervisada
permalink: /docs/creacion-reserva-supervisada/
---

**Versión documento: ** v1

**Creación: ** 27/08/2019

**Última modificación: ** 02/09/2019

### Crear reserva supervisada

Permite a un gestor de equipo crear una reserva para un número determinado de usuarios, nunca menor que 1, ni mayor del establecido en la base de datos.

A tener en cuenta:

- El estado de estas reservas es **PENDING_ASSIGNMENT**.
- Si algún recurso está ocupado no se realizará ninguna reserva, aunque los demás esten disponibles.
- Si las fechas no son validas, o la duración es menor a 15 minutos, no se realizará ninguna reserva.
- La recurrencia está permitida, para ello hay que enviar varias fechas.

### Request

##### HTTP Request

```http
POST /api/v1/users/me/bookings/supervised
POST /api/v1/users/{userId}/bookings/supervised
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Body

En el cuerpo de la solicitud, proporcione una representación JSON del objeto [SupervisedBookingInfo](#SupervisedBookingInfo)

| Property | Type                                            | Description                                                               | Required |
| -------- | ----------------------------------------------- | ------------------------------------------------------------------------- | -------- |
| Booking  | [SupervisedBookingInfo](#SupervisedBookingInfo) | Objeto con las fechas, los ids de los recursos y el título de la reserva. | true     |

### Response

Si se han conseguido crear las reservas, se devuelve un código `201` con el mismo objeto SupervisedBookingInfo enviado, pero ahora con el **Id de la reserva supervisada**, y sin la lista de fechas.

```json
{
  "supervisedBookingId": "32c65446-6990-45fd-9efa-d92f7f7c88bc",
  "resourceIdsList": [
    "50b5e144-025d-4693-8645-f8c2ae450995",
    "867d751d-098c-41fa-9412-0de068ef2782"
  ],
  "title": "Primera prueba de reserva supervisada!"
}
```

### SupervisedBookingInfo

##### Con título

```json
{
  "bookingDays": [
    {
      "startDate": 1566907426000,
      "endDate": 1566914626000
    }
  ],
  "resourceIdsList": [
    "50b5e144-025d-4693-8645-f8c2ae450995",
    "867d751d-098c-41fa-9412-0de068ef2782"
  ],
  "title": "Primera prueba de reserva supervisada!",
  "optionalCheckIn": true
}
```

##### Sin título

```JSON
{
	"bookingDays": [
		{
			"startDate": 1566907426000,
			"endDate": 1566914626000
		}

	],
	"resourceIdsList": [
			"50b5e144-025d-4693-8645-f8c2ae450995",
			"867d751d-098c-41fa-9412-0de068ef2782"
	],
    "optionalCheckIn": true
}
```

##### Con recurrencia

```json
{
  "bookingDays": [
    {
      "startDate": 1566907426000,
      "endDate": 1566914626000
    },
    {
      "startDate": 1566993826000,
      "endDate": 1567001026000
    }
  ],
  "resourceIdsList": [
    "50b5e144-025d-4693-8645-f8c2ae450995",
    "867d751d-098c-41fa-9412-0de068ef2782"
  ],
  "title": "Primera prueba de reserva supervisada!",
  "optionalCheckIn": true
}
```
