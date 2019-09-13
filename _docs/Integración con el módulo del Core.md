---
title: Integración con el módulo del Core
permalink: /docs/integracion-modulo-core/
---

El módulo del core nos proporciona un conjunto de clases entidad o DAO (Data Access Object) que son la representación java de las tablas de la base de datos.

Si bien estas clases son las que utilizaremos para hacer transacciones con la base de datos (insertar, actualizar, eliminar registros) puede que no nos sean tan útiles a la hora de enviar / recibir información entre el servidor y el cliente. Esto es debido a que hay información que esta en las clases DAO que no queremos enviar a los clientes, por ejemplo:

Supongamos la clase UsuarioDAO la cual contiene los siguientes datos:

- Nombre
- Apellidos
- Contraseña
- Fecha nacimiento

Supongamos también que en el API definimos una llamada para recuperar la información de otro usuario. Lo más seguro es que, por temas de seguridad en este caso, no nos interese devolver la contraseña del usuario cuando devolvamos el resto de la información del mismo.

Para solucionar este problema de una forma sencilla y limpia he decidido utilizar el patrón **Converter**. Este patrón se encarga de proveer de forma genérica, una manera de convertir bidireccionalmente entre dos tipos de objetos, permitiendo una implementación limpia en la que los objetos no necesitan preocuparse de los otros.

Aplicando este patrón al problema planteado anteriormente tendríamos las siguientes clases:

**UsuarioDAO** -> Clase entidad con la que accedemos a los datos de la base de datos.

- Nombre
- Apellidos
- Contraseña
- Fecha nacimiento

**UsuarioDTO** -> Clase que utilizaremos para compartir información entre el Cliente y el Servidor.

- Nombre
- Apellidos
- Fecha nacimiento

**Conversor** -> Conversor genérico del cual heredaran las implementaciones especificas.

- convertirDesdeDTO
- convertirDesdeDAO

**ConversorUsuario** -> Implementación del Conversor genérico para los objetos usuario, donde se definen las funciones que transforman los objetos UsuarioDAO a UsuarioDTO y UsuarioDTO a UsuarioDAO.

## Bibliografía

- [Converter Pattern](http://ramesh-java-design-patterns.blogspot.com/2018/03/converter-pattern.html)

- [Design patterns implemented in Java - Converter Pattern](https://github.com/iluwatar/java-design-patterns/tree/master/converter/src/main/java/com/iluwatar/converter)
