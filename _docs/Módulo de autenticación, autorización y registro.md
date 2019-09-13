---
title: Módulo de autenticación y autorización
permalink: /docs/autenticacion-autorizacion/
---

**Versión documento: ** v1

**Creación: ** 06/06/2019

**Última modificación: ** 07/06/2019

## Autenticación

Para poder hacer uso del API de Bookker B2B, las aplicaciones deberán utilizar el siguiente flujo:

1. El cliente se autentica, mediante usuario y contraseña, haciendo una petición al servidor del API.
2. Una vez que el servidor verifica la identidad del cliente, se genera un token de acceso (JWT) que es enviado al cliente.
3. El cliente usa ese token para acceder a los recursos protegidos del API.
4. En cada petición, el servidor desencripta el token y comprueba si el cliente tiene permisos para acceder al recurso.

![Autenticación con JWT](/assets/images/jwtexplanation.png)

### Autenticación

Intenta autenticar al usuario mediante username / email y contraseña.

#### Request

##### HTTP request

```http
POST /api/v1/login
```

##### Headers

| Header       | Value            | Required |
| ------------ | ---------------- | -------- |
| Content-Type | application/json | true     |

##### Body

| Property | Type   | Description                      | Required |
| -------- | ------ | -------------------------------- | -------- |
| username | String | El alias o el email del usuario. | true     |
| password | String | La contraseña del usuario.       | true     |

#### Response

Si se ha conseguido autenticar correctamente al usuario, se devuelve un código `200` con la información básica del usuario y el token de autorización en el cuerpo de la respuesta.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "role": {
        "id": "2f29dae7-bac1-4c83-b43b-e16d787b1509",
        "name": "MOCK_MOBILE_ROLE1559818713447"
    },
    "user": {
        "id": "3eed2a9b-59bb-40a5-a3f2-3f25fa0ad37a",
        "name": "Test1559818716520",
        "surname": "Test1559818716520",
        "alias": "test1559818692351",
        "email": "Test1559818716520@test.com",
        "phone": "123123123",
        "organization": {
            "id": "64259519-7e36-447a-9010-a74fe9378555"
        },
        "department": {
            "id": "c047a97b-b41a-4732-ba1d-a21f346b9c9e"
        },
        "userRule": {
            "id": "6458ed94-1beb-4ecf-a4a8-7093f22340f7"
        },
        "mobileRole": {
            "id": "2f29dae7-bac1-4c83-b43b-e16d787b1509"
        },
        "canBeSearched": true
    },
    "canBeSearched": true,
          "notificationConfig": {
              "createdBy": null,
              "createdDate": 1567413419000,
              "lastModifiedBy": null,
              "lastModifiedDate": 1567413433000,
              "id": "7f320947-adb0-4c6c-8c6d-d238b9e49c88",
              "bookingUpdates": "PUSH;",
              "bookingUpdatesMp": "",
              "bookingInvitation": "PUSH;",
              "bookingExpiration": "EMAIL;PUSH;",
              "userId": "7eccd6ed-3faf-41de-bec1-0b8501316857"
          }
      },
    "token": "eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MTIifQ.eyJpc3MiOiJzZWN1cmUtYXBpIiwiYXVkIjoic2VjdXJlLWFwcCIsInN1YiI6InRlc3QxNTU5ODE4NjkyMzUxIiwiZXhwIjoxNTYwNjgyOTAwLCJyb2wiOlsiTU9DS19NT0JJTEVfUk9MRTE1NTk4MTg3MTM0NDciXX0.GaCyT8AyFWb_iGFk8xBNrsgfNtPU0BxFvlEgCDsvC5HZ0TEoQj-OzLY99O0sLZGBGUHT9EJTZX4gIzIwz4SMDQ"
}
```

### Refresco Autenticación

Intenta refrescar el token del usuario. Solo se podrá refrescar con éxito si el token anterior no ha expirado.

Todos los tokens se pueden utilizar hasta su fecha de expiración, pudiendo hacer uso de más de uno de ellos.

#### Request

##### HTTP request

```http
GET /api/v1/login/refresh
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

#### Response

Si se ha conseguido refrescar el token de autorización correctamente se devuelve un código `200` con la información del nuevo token de autorización en el cuerpo de la respuesta.

```json
HTTP/1.1 200 OK
Content-type: application/json

{
    "token": "eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MTIifQ.eyJpc3MiOiJzZWN1cmUtYXBpIiwiYXVkIjoic2VjdXJlLWFwcCIsInN1YiI6InRlc3QxNTU5ODE4NjkyMzUxIiwiZXhwIjoxNTYwNjgyOTAwLCJyb2wiOlsiTU9DS19NT0JJTEVfUk9MRTE1NTk4MTg3MTM0NDciXX0.GaCyT8AyFWb_iGFk8xBNrsgfNtPU0BxFvlEgCDsvC5HZ0TEoQj-OzLY99O0sLZGBGUHT9EJTZX4gIzIwz4SMDQ"
}
```

## Autorización

En todas las peticiones que requieran autorización habrá que enviar el token de autenticación como un **header** de la propia petición de la siguiente manera:

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

Ejemplo:

```json
GET http://localhost:9010/api/v1/users HTTP/1.1
authorization: Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MTIifQ.eyJpc3MiOiJzZWN1cmUtYXBpIiwiYXVkIjoic2VjdXJlLWFwcCIsInN1YiI6IkFpdG9yR0MiLCJleHAiOjE1NTk4MTExNTEsInJvbCI6W119.MRBm5ESWLaIj_jTURCgRkrg3UUJv1gMbwmfGxtcpurlXif9PtmcRMvon4qKYA1V8_LeMg0oJl7ZOohPvk_URmA
```

## Bibliografía

- [Autenticar con Spring Security y JWT](https://auth0.com/blog/implementing-jwt-authentication-on-spring-boot/)
