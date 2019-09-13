---
title: Recuperar recursos del usuario
permalink: /docs/recursos-usuario/
---

**Versión documento: ** v1

**Creación: ** 13/06/2019

**Última modificación: ** 04/09/2019

## Recursos del usuario

Los usuarios de las aplicaciones móviles de **Bookker** tienen un alcance, dentro de su organización, que está limitado por los grupos a los que pertenece dicho usuario.

Siendo así, cada usuario tendrá una serie de recursos a los que tendrá acceso:

- Categorías / Subcategorías.
- Diccionarios.
- Edificios.
- Plantas / Mapas.
- Tema de la organización.

### Recuperar recursos del usuario

Intenta recuperar los recursos a los que tiene acceso el usuario.

#### Request

##### HTTP request

```http
GET /api/v1/users/me/resources
GET /api/v1/users/{userId}/resources
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Param             | Value                                           | Required |
| ----------------- | ----------------------------------------------- | -------- |
| buildingsDate     | Long - Fecha de última versión en milisegundos. | false    |
| floorsDate        | Long - Fecha de última versión en milisegundos. | false    |
| subcategoriesDate | Long - Fecha de última versión en milisegundos. | false    |
| dictionariesDate  | Long - Fecha de última versión en milisegundos. | false    |

#### Response

Si se ha conseguido validar que el usuario tiene acceso para realizar la petición, se devuelve un código `200` con la información de los recursos del usuario, introducido en la petición, en el cuerpo de la respuesta. En caso de no haber información nueva se devuelve un código `304`.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "floorsDate": 1560510618000,
    "dictionariesDate": 1560510618000,
    "floors": [
        {
            "id": "c52bf01f-4bb4-49e5-9df5-4229ae7b5a19",
            "name": "TEST1560510610242",
            "floorNumber": 0,
            "building": {
                "id": "d71e0d8c-73c7-44bd-9cee-289bfa669d39"
            }
        }
    ],
    "buildingsDate": 1560337818000,
    "buildings": [
        {
            "id": "d71e0d8c-73c7-44bd-9cee-289bfa669d39",
            "name": "TEST1560510610242",
            "address": {
                "country": "Spain",
                "city": "Logroño",
                "address": "C/ Duques de Nájera 43 Bis",
                "coordinates": {
                    "longitude": 5e-324,
                    "latitude": 1.7976931348623157e+308
                }
            },
            "organization": {
                "id": "2207bf3d-ca7b-495d-8c25-acf2c438d437"
            },
            "userCanAccess": false
        }
    ],
    "subcategories": [
        {
            "id": "e77fa7f1-e868-4058-bd12-e58be143c67a",
            "name": "Puesto de trabajo1560510610242",
            "category": "WORKSTATION",
            "organization": {
                "id": "2207bf3d-ca7b-495d-8c25-acf2c438d437"
            },
            "features": [
                {
                    "id": "d6f1fd6f-7fda-4e25-b60c-f502c401efc5",
                    "name": "TEST1560510610242",
                    "organization": {
                        "id": "2207bf3d-ca7b-495d-8c25-acf2c438d437"
                    }
                }
            ]
        }
    ],
    "subcategoriesDate": 1560510618000,
    "dictionaries": [
        {
            "dictionary": "rutafalsa",
            "building": {
                "id": "d71e0d8c-73c7-44bd-9cee-289bfa669d39"
            },
            "subcategory": {
                "id": "e77fa7f1-e868-4058-bd12-e58be143c67a"
            }
        }
    ],
    "theme": {
        "id": "818aeff1-12ac-4021-ae14-0cc4df710883",
        "primaryColor": "primaryColor",
      	"secondaryColor": "secondaryColor",
      	"logoApps": "rutaDelLogo",
        "organization": {
            "id": "4c6c300e-ff5a-400b-adb4-60e513e1f4ba"
        }
    }
}
```
