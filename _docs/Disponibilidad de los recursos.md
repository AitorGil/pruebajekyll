---
title: Disponibilidad de los recursos
permalink: /docs/disponibilidad-recursos/
---

**Versión documento: ** v1

**Creación: ** 27/06/2019

**Última modificación: ** 28/06/2019

## Comprobar disponibilidad

Comprueba la disponibilidad de los recursos teniendo en cuenta los siguientes criterios:

- Si el usuario tiene acceso al recurso (grupos).
- Si el recurso tiene las características seleccionadas por el usuario (opcional).
- Si se cumplen las reglas del recurso (antelación de la reserva, horarios...).
- Si el recurso está libre en el momento seleccionado por el usuario.

#### Request

##### HTTP request

```http
Workstations

GET /api/v1/users/me/buildings/{buildingId}/workstations/subcategories/{subcategoryId}/free
GET /api/v1/users/{userId}/buildings/{buildingId}/workstations/subcategories/{subcategoryId}/free


Spaces

GET /api/v1/users/me/buildings/{buildingId}/spaces/subcategories/{subcategoryId}/free
GET /api/v1/users/{userId}/buildings/{buildingId}/spaces/subcategories/{subcategoryId}/free
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Param       | Value                                                                          | Required |
| ----------- | ------------------------------------------------------------------------------ | -------- |
| bookingDays | List<[BookingDay](#BookingDay)>                                                | true     |
| features    | Array de identificadores de las características por las que se quiere filtrar. | false    |
| capacity    | Capacidad mínima de los espacios. **Solo disponible para espacios.**           | false    |

```tex
¡Importante! - Ejemplo de uso del parámetro bookingDays.

Para utilizar una lista en los parámetros de una petición GET hay que hacerlo de la siguiente forma:

http://localhost:9010/api/v1/users/{userId}/buildings/{buildingId}/workstations/subcategories/{subcategoryId}/free?bookingDays[0].startDate=1561708800000&bookingDays[0].endDate=1561712400000&bookingDays[1].startDate=1561723200000&bookingDays[1].endDate=1561730400000

Sin embargo, para poder realizar la petición correctamente hay que encodear la URL ya que los corchetes "[]" son carácteres no válidos.

```

###### Request Example

```http
GET http://localhost:9010/api/v1/users/me/buildings/5068c634-064d-4e15-b17f-1a420c68f051/workstations/subcategories/eaacb523-7a8b-44d4-a3b2-d67f036a3b1c/free?bookingDays%5B0%5D.startDate=1561708800000&bookingDays%5B0%5D.endDate=1561712400000&bookingDays%5B1%5D.startDate=1561723200000&bookingDays%5B1%5D.endDate=1561730400000&features=faf57caf-53ed-410f-bf3d-39f220593ba7,asd57caf-53ed-230f-bf3d-39f220593c4r
```

#### Response

Si se han conseguido procesar la petición, se devuelve un código `200` con la información de los recursos disponibles.

**Wokstation Response**

```json
HTTP/1.1 200 OK
Content-type: application/json

[
    {
        "id": "50b5e144-025d-4693-8645-f8c2ae450995",
        "name": "Puesto #1",
        "posterCode": "A01PB",
        "phone": "941576132",
        "mapCoordinates": {
            "topLeftX": 692,
            "topLeftY": 3209,
            "bottomRightX": 742,
            "bottomRightY": 3259
        },
        "approachable": true,
        "floor": {
            "id": "f2f67b2e-6726-4df5-b0c6-a52d9d994a95"
        },
        "subcategory": {
            "id": "eaacb523-7a8b-44d4-a3b2-d67f036a3b1c"
        },
        "visible": true
    }
]
```

**Space Response**

```json
HTTP/1.1 200 OK
Content-type: application/json

[
    {
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
    }
]
```

### BookingDay

#### Properties

| Name      | Type | Description                                            |
| --------- | ---- | ------------------------------------------------------ |
| startDate | Long | Fecha y hora en milisegundos del inicio de la reserva. |
| endDate   | Long | Fecha y hora en milisegundos del fin de la reserva.    |

```json
{
  "startDate": 1561557600000,
  "endDate": 1561559400000
}
```
