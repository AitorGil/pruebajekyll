---
title: Sincronización con Microsoft Outlook
permalink: /docs/sincronizacion-microsoft-outlook/
---

## Bookker v2

La sincronización con Outlook dispone de tres partes principalmente:

- Notificación desde Bookker hasta Outlook de los cambios realizados por los usuarios. Todas las acciones se realizan en los calendarios de los usuarios.
- Notificación desde Bookker hasta Outlook de los cambios realizados por el sistema de Bookker. Todas las acciones se realizan en los calendarios de los recursos.
- Notificación desde Outlook hasta Bookker de los cambios realizados en los calendarios de los recursos.

En base a estos canales de comunicación se monta un sistema de sincronización donde los usuarios de Bookker pueden ver reflejadas las reservas de espacios en sus calendarios de Outlook y viceversa.

### Sincronización unidirecional

Las reservas de espacios, realizadas en Bookker, se ven reflejadas en los calendarios de los usuarios en MS Outlook.

**No es necesario** que la empresa tenga **correos de recurso** (en Outlook) para los espacios.

#### Flujo de creación de reserva:

![Flujo sincronización Outlook](/home/aitorgc/Documentos/Bookker/Documentacion/Bookker-B2B-API/Images/Flujo Sincronización con Microsoft Graph.png)

- El usuario crea una reserva desde la aplicación móvil de Bookker. **[BOOKKER]**
- Bookker procesa la petición, comprobando las restricciones y el acceso del usuario, y realiza una petición a Outlook de creación de evento. **[BOOKKER]**
- Si la petición es correcta, y todo ha ido bien, Outlook contesta un 200 OK. **[OUTLOOK]**
- Al recibir el 200 OK, se guarda la reserva en la base de datos de Bookker y se devuelve un 201 Created a los usuarios. **[BOOKKER]**

### Sincronización bidireccional

Las reservas de espacios, realizadas en Bookker, se ven reflejadas en los calendarios de los usuarios en MS Outlook y las reservas creadas desde las aplicaciones de MS Outlook son procesadas por Bookker y registradas en su sistema.

**Es necesario** que la empresa tenga **correos de recurso** (en Outlook) para los espacios.

#### Flujo de creación de reserva desde Bookker:

![Flujo sincronización Outlook](/home/aitorgc/Documentos/Bookker/Documentacion/Bookker-B2B-API/Images/Flujo Sincronización con Microsoft Graph.png)

1. El usuario crea una reserva desde la aplicación móvil de Bookker.
2. El API de Bookker valida la petición de reserva.
   1. Comprueba que el usuario tenga acceso al espacio.
   2. Comprueba las reglas del usuario.
   3. Comprueba las reglas del espacio.
3. Bookker realiza una petición de creación de evento en el calendario del espacio usando MS Graph REST API.
4. Si se consigue crear el evento, en el calendario del usuario, MS Graph responde `200 OK`.
5. **Bookker convierte el Evento** de MS Outlook **en** un objeto **Reserva** de Bookker y lo almacena en la base de datos.
6. La base de datos notifica de que se ha almacenado correctamente la reserva.
7. Bookker responde a la petición de creación un `201 Created`.

Por otra parte, MS Outlook procesará el evento creado en el calendario del usuario y lo propagará a el calendario del recurso y de los invitados. También se encargará de enviar notificaciones push a las suscripciones que, previamente, Bookker ha establecido a través de MS Graph.

#### Flujo de proceso de las notificaciones push de MS Graph

Bookker recibe tres tipos de notificaciones: Creación, actualización y eliminación de eventos en los calendarios de los recursos.

##### Creación de evento

1. Se recupera el evento en el calendario del recurso en Outlook.
2. Como los eventos se crean en el calendario de los usuarios pero el cambio notificado corresponde al evento en el calendario del recurso, debemos intentar buscar por el iCalUId para **discernir si es un evento creado desde Bookker o una nueva creación** que debemos procesar y registrar.

3. a) En caso de ser una notificación de un **evento creado desde Bookker** (se ha encontrado una coincidencia en Bookker con el iCalUId) **se para el procesamiento de la notificación**.

4. b) En caso de que la creación del evento se haya realizado desde Outlook, **se comprueba si es un evento serie o una única instancia**. Si es un evento serie se procede a recuperar todas sus instancias para procesarlas como una lista de eventos.
5. **Los eventos son procesados por Bookker**, comprobando las restricciones y el acceso del usuario.
6. a) **Si se cumplen todas las condiciones** para la realización de la reserva, **se procede a almacenar el evento**, como una reserva mas, **y notificar a los usuarios** a través de Bookker.

7. b) En caso de que **no se pueda realizar la reserva se declina el evento en Outlook**. Este último proceso generará una nueva notificación push de actualización de Outlook hacia Bookker.

##### Actualización de evento

1.  Se **recupera el evento en el calendario del recurso en Outlook**.
2.  **Recuperamos la información de las reservas** en Bookker.
3.  **Comprobamos que la información que se ha modificado sea modificable** en Bookker.

4.  a) **Si se puede realizar la actualización** del evento **se almacenan los cambios** en Bookker.

5.  b) **En caso contrario, se actualiza el evento en Outlook** (lo que crea otra notificación posterior de actualización) **volviendo a dejar los datos como estaban anteriormente**.

##### Eliminación de evento

1. Intenta eliminar la reserva con el identificador externo recibido en la notificación.

#### Problemas encontrados en la sincronización

- Los eventos tienen diferentes identificadores según el calendario en el que se miren.
  - Identificador del evento en el calendario del usuario.
  - Identificador del evento en el calendario del recurso.
  - iCalUId identificador compartido entre todos los calendarios.
- El sistema de Webhook de MS Graph es inconsistente, es decir, el tiempo que tarda en notificar los cambios en los calendarios es variable en un rango desde unos pocos segundos hasta varios minutos. Incluso se han detectado ocasiones en las que no se ha notificado de los cambios.
- Perdida de información entre el modelo de Reserva (Bookker) y de Evento (Outlook).
  - Incompatibilidad de los eventos serie.
  - ...
- El procesamiento de las notificaciones. Cualquier acción que realizamos desde Bookker tiene como consecuencia una o varias notificaciones de Outlook, con lo que el procesamiento de las notificaciones se hace pesado (discernir si hay que procesar la notificación o no).

### Tecnologías utilizadas

- [MS Graph REST API](https://docs.microsoft.com/es-es/graph/api/overview?view=graph-rest-1.0)

## Bookker v3

### Mejoras en la sincronización

Para mejorar la sincronización con MS Outlook, se pretenden llevar a cabo cambios que permitan, de una forma sencilla, evitar la perdida de información al almacenar los eventos en Bookker y dar un sistema más robusto a la hora de consultar la información.

Principales cambios con respecto a Bookker v2:

- Ya no se intentará convertir los eventos de Outlook en reservas de Bookker. Se almacenarán con toda la información, evitando perdida de datos al realizar conversiones.
- Haciendo uso de las [OpenTypeExtensions](https://docs.microsoft.com/en-us/graph/api/opentypeextension-post-opentypeextension?view=graph-rest-1.0) de MS Graph se añadirá información relevante de Bookker a los eventos de Outlook.
- Las aplicaciones móviles deberán implementar formularios de creación de reservas acordes con la nueva información que añade MS Outlook en sus eventos.

### Problemas encontrados en la sincronziación

Con estos cambios podemos gestionar de forma más sencilla la información de los eventos evitando alguno de los problemas de la versión anterior:

- Los eventos tienen diferentes identificadores según el calendario en el que se miren.

  - Identificador del evento en el calendario del usuario.
  - Identificador del evento en el calendario del recurso.
  - iCalUId identificador compartido entre todos los calendarios.

  **[SOLUCIONADO]**: Ahora podemos almacenar de forma sencilla todas las referencias de los identificadores junto con toda la información del evento, además de tener la posibilidad de añadir el identificador del evento en el calendario del usuario y del recurso como información extra con los OpenTypeExtensions.

* El sistema de Webhook de MS Graph es inconsistente, es decir, el tiempo que tarda en notificar los cambios en los calendarios es variable en un rango desde unos pocos segundos hasta varios minutos. Incluso se han detectado ocasiones en las que no se ha notificado de los cambios.

- Perdida de información entre el modelo de Reserva (Bookker) y de Evento (Outlook). **[SOLUCIONADO]**

  - Incompatibilidad de los eventos serie.
  - ...

  **[SOLUCIONADO]**: Ahora se almacena toda la información de los eventos, con lo que no existe perdida de información en las conversiones.

* El procesamiento de las notificaciones. Cualquier acción que realizamos desde Bookker tiene como consecuencia una o varias notificaciones de Outlook, con lo que el procesamiento de las notificaciones se hace pesado (discernir si hay que procesar la notificación o no).

**[SOLUCIONADO]**: Al almacenar toda la información de los eventos disponemos de valores de control de versión como **changeKey**, **createdDateTime** y **lastModifiedDateTime**.

### Tecnologías utilizadas

- Se hará uso de la librería de autenticación de microsoft llamada [MS ADAL](https://github.com/AzureAD/microsoft-authentication-library-for-java).
- Se hará uso del [SDK de MS Graph](https://github.com/microsoftgraph/msgraph-sdk-java) para Java.
