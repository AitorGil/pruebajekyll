---
title: Sincronización externa con Google Calendar
permalink: /docs/sincronizacion-google-calendar/
---

#### Pasos previos a seguir para establecer correctamente la sincronización entre Bookker y Google Calendar.

##### <u>1º Crear un proyecto en la consola de desarrolladores de Google</u>

Lo primero de todo es dirigirse a la [consola de desarrolladores de Google](https://console.developers.google.com) y crear un proyecto nuevo (si es que no hay creado uno ya, si este es el caso, podemos omitir este paso).

En la parte superior izquierda de la pantalla debería aparecer **Selecciona un proyecto**, pulsamos y se abrirá un diálogo.

![crear proyecto](/home/aitor/Documentos/Imagenes Manual Google/crear proyecto.png)

Deberemos elegir la organización correcta y a continuación pulsaremos en **Nuevo proyecto**, esto nos llevará a otra pantalla donde tendremos que introducir diferentes datos.

![nuevo proyecto](/home/aitor/Documentos/Imagenes Manual Google/nuevo proyecto.png)

Lo primero es introducir el nombre del proyecto, a continuación si queremos modificar el ID podemos hacerlo, pero es opcional, en el campo de **Organización** aparecerá la que hemos elegido anteriormente y en ubicación deberemos elegir la correcta.

Una vez introducidos la información necesaria pulsamos en crear.

##### <u>2º Crear una cuenta de servicio y delegarle autorización sobre el dominio.</u>

Es necesario crear una cuenta de servicio ya que esto nos permitirá personificar a los usuarios y/o recursos y así realizar operaciones sin el consentimiento explícito de éstos.

Para crear dicha cuenta hay que seguir los siguientes pasos:

- Dirigirse a este [enlace](https://console.developers.google.com/iam-admin/serviceaccounts), (previamente hay que estar logeado como administrador y tener un proyecto creado) y pulsar en ![crear_cuenta_servicio](/home/aitor/Documentos/Imagenes Manual Google/crear_cuenta_servicio.png)

- A continuación tendremos que introducir los datos que se nos soliciten, en este caso, el **nombre** de la cuenta de servicio, su **ID** y su **descripción**.

  ![](/home/aitor/Documentos/Imagenes Manual Google/crear cuenta de servicio.png)

  Procedemos a pulsar en crear y a continuación se nos dará la opción de otorgar diferentes permisos, esto es opcional y para el uso que se le va a dar a esta cuenta de servicio no es necesario (pulsar en **Continuar** y después en **Listo**.

- Después se nos redirigirá al listado de cuentas de servicio donde aparecerá la que acabamos de crear, pulsamos en su nombre y nos mostrará sus detalles.

  ![habilitar delegación de dominio](/home/aitor/Documentos/Imagenes Manual Google/habilitar delegación de dominio.png)

* Lo que tenemos que hacer ahora es crear una clave y habilitar la delegación en todo el dominio de G Suite, para ello tendremos que pulsar donde dice **Editar**, y a continuación en **Mostrar la delegación en todo el dominio**, y marcamos la casilla.

  Lo siguiente es pulsar donde dice crear clave. Se nos dará a elegir entre dos formatos de archivo, **JSON** o **P12**, es imprescindible escoger **JSON**, esto nos descargará un archivo que necesitaremos más adelante. **(PENDIENTE EN MP: en el formulario de la plataforma de gestión tendría que haber un campo para subir el JSON o su contenido para luego insertarlo en la base de datos)**.

  ![crear clave privada](/home/aitor/Documentos/Imagenes Manual Google/crear clave privada.png)

  Es **MUY IMPORTANTE** no perder este archivo, ya que Google no se hace cargo de lo que pase con éste.

  ![aviso clave privada](/home/aitor/Documentos/Imagenes Manual Google/aviso clave privada.png)

- Una vez pulsemos en guardar, debajo de la casilla que marcamos anteriormente para habilitar la delegación del dominio, habrá aparecido un campo nuevo, este es el **ID de cliente**, deberemos copiarlo ya que lo necesitaremos a continuación.

  ![id cliente](/home/aitor/Documentos/Imagenes Manual Google/id cliente.png)

* Para terminar tendremos que dar permisos a la cuenta de servicio sobre Google Calendar, para esto hay que irse a la consola de administración de G Suite y pulsar en **Seguridad**, si no aparece pulsamos en **Mas controles**, que se encuentra en la parte inferior.

  ![consola de administración](/home/aitor/Documentos/Imagenes Manual Google/consola de administración.png)

* Una vez dentro de este apartado, tendremos que buscar la opción de **Configuración avanzada**, que desplegará otra opcion llamada **Autenticación**.

  ![configuracion avanzada](/home/aitor/Documentos/Imagenes Manual Google/configuracion avanzada.png)

- Pulsamos en **Administrar el acceso de cliente API**, esto nos llevará al siguiente paso, que es otorgarle los permisos sobre Google Calendar a la cuenta de servicio.

  ![administrar acceso](/home/aitor/Documentos/Imagenes Manual Google/administrar acceso.png)

- En el campo de texto **Nombre del cliente**, tendremos que introducir el ID de cliente copiado anteriormente después de habilitar la delegación sobre el dominio. En el campo de texto **Uno o más ámbitos API**, tendremos que introducir **exactamente lo siguiente**:

  - https://www.googleapis.com/auth/admin.directory.resource.calendar,https://www.googleapis.com/auth/calendar

  Una vez introducidos el ID de cliente y los ámbitos, pulsamos en autorizar:

  ![ambitos api](/home/aitor/Documentos/Imagenes Manual Google/ambitos api.png)

  Justo debajo aparecerá el ID de cliente introducido, y a su derecha los ámbitos otorgados (se ha ocultado el ID de cliente por motivos de privacidad).

- Una vez hecho esto, ya tenemos lista la cuenta de servicio.

##### <u>3º Cuenta de administrador para que la cuenta de servicio la personifique.</u>

Es necesario que se cree un usuario con ciertos permisos de administración para que la cuenta de servicio pueda personificarle, esto es necesario ya que Bookker realiza ciertas operaciones que en Google Calendar solo son posibles personificando a un usuario con dichos permisos.

Para crear dicho usuario hay que realizar los siguientes pasos:

- Primero tendremos que crear el usuario, para ello nos dirigimos a la consola de administración de G Suite, y pulsamos en la opción **Usuarios**.
- A continuación seguimos los pasos que se nos indican y creamos un usuario.

- Después volvemos a la consola de administración de G Suite, y buscamos la opción llamada **Funciones de administrador**, si no aparece, deberemos pulsar en **Más controles**.

  ![consola de administración](/home/aitor/Documentos/Imagenes Manual Google/consola de administración.png)

* A continuación deberemos pulsar en dicha opción, y se nos mostrará la siguiente pantalla

  ![administracion](/home/aitor/Documentos/Imagenes Manual Google/administracion.png)

- Deberemos pulsar en **Superadministrador**, y a continuación se nos mostrará un diálogo donde deberemos introducir el nombre o correo del usuario que hemos creado anteriormente, de esta forma aparecerá como opción sugerida, aceptamos y el diálogo se cerrará. Antes de salir, es necesario pulsar en el botón guardar que aparecerá en la parte inferior derecha de la pantalla.

##### <u>4º Añadir y verificar el dominio donde se recibirán las notificaciones</u>

En caso de que la sincronización bidireccional esté contratada, el siguiente paso es añadir y verificar el dominio donde se recibirán las notificaciones, para que Bookker pueda gestionarlas.

Los pasos a seguir son los siguientes:

- Lo primero es ir a la [consola de búsqueda](https://search.google.com/u/1/search-console/welcome) de Google, y logearse preferiblemente como administrador.

  ![search console](/home/aitor/Documentos/Imagenes Manual Google/search console.png)

* Imaginemos que nuestro dominio es **http://www.bookkercorp.com/** (ejemplo), a este dominio tendremos que añadirle siempre esto: **api/v1/notifications/google/{idOrganización}/**, siendo idOrganización el id de la organización registrada en Bookker para la que se está preparando la sincronización bidireccional. Un ejemplo del dominio completo sería:

  - http://www.bookkercorp.com/api/v1/notifications/google/61ef94b4-5775-43fd-880f-f1850d089e28/

  Este dominio lo tendremos que pegar en el campo de la opción **Prefijo de la URL**, y pulsar en **Continuar**, se abrirá el siguiente diálogo:

  ![verificar propiedadpng](/home/aitor/Documentos/Imagenes Manual Google/verificar propiedadpng.png)

- Antes de pulsar en verificar, deberemos descargar el archivo, y copiar su nombre al completo, incluida la extensión del mismo (.html), **(PENDIENTE EN MP: en el formulario de la plataforma de gestión debería haber un campo para pegar el nombre del archivo, y despues insertar el registro necesario en la base de datos)**. Una vez se haya guardado en la base de datos, pulsaremos en verificar, y si todo va bien, debería aparecer un mensaje de confirmación como este:

  ![confirmacion de verificacion](/home/aitor/Documentos/Imagenes Manual Google/confirmacion de verificacion.png)

* Por último, tendremos que añadir el dominio desde la consola de desarrolladores de Google, para así autorizarlo, podemos acceder desde [aquí](https://console.developers.google.com/apis/credentials/domainverification), es importante asegurarse de que estamos usando la consola con el usuario y que estamos en el proyecto correcto.

  ![verificacion dominio consola google](/home/aitor/Documentos/Imagenes Manual Google/verificacion dominio consola google.png)Pulsamos en añadir un dominio e introducimos el mismo dominio usado en el paso anterior.

  Hecho esto la sincronización bidireccional estará preparada.
