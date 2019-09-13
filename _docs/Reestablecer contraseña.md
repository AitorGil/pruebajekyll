---
title: Restablecer contraseña
permalink: /docs/restablecer-contrasena/
---

**Versión documento: ** v1

**Creación: ** 08/07/2019

**Última modificación: ** 08/07/2019

## Reestablecer contraseña

Permite cambiar la contraseña de un usuario por otra generada automáticamente.

### Reestablecer contraseña de un usuario

En caso de que el usuario olvide su contraseña, podrá restablecerla por una nueva, para ello hay que enviar el email de dicho usuario.

Si el estado del usuario es LOCKED o FIRED o el usuario no existe no se realizará la operación.

Si el usuario existe y su estado es ACTIVATED, el servidor generará una contraseña automáticamente y de forma aleatoria y mandará un correo electrónico al email proporcionado, con la nueva contraseña dentro de dicho correo.

![Ejemplo del email recibido](/home/aitor/Documentos/Images/cambiar pass.png)

#### Request

##### HTTP request

```http
GET /api/v1/users/forgotpassword
```

##### Headers

| Header        | Value                                        | Required |
| ------------- | -------------------------------------------- | -------- |
| Authorization | Bearer eyJ0eXBlIjoiSldUIiwiYWxnIjoiSFM1MT... | true     |

##### Params

| Param | Value                                                | Required |
| ----- | ---------------------------------------------------- | -------- |
| email | String - Email del usuario (Ej: usuario1@prueba.com) | true     |

#### Response

Si se consigue reestablecer la contraseña y enviar el email al usuario, se devuelve un código `200` con el cuerpo de la respuesta vacía.
