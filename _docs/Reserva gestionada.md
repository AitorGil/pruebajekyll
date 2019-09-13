---
title: Crear reserva supervisada
permalink: /docs/crear-reserva-supervisada/
---

**Fecha de creación:** 10/09/2019

**Fecha de modificación:** 10/09/2019

### Funcionalidad

Permite a un gestor de equipos realizar una reserva a uno o más usuarios ya sean internos o externos.

Aspectos generales:

- Este tipo de reservas pueden convivir simultáneamente con las reservas convencionales.

- No se tiene en cuenta las reglas de usuarios, es decir, se las salta, entre otras cosas esto causa que la duración de este tipo de reservas no cuente para la duración máxima permitida para el usuario.
- De igual forma que con las reglas de usuarios, las de los recursos también se ignoran, lo único que se comprueba es que las fechas sean válidas y la duración sea de mínimo 15 minutos.
- El supervisor podrá hacer tanto check-in como check-out a los usuarios asignados, así como ver la hora de check-in y check-out de éstos.
- El gestor de equipos que crea la reserva puede asignarse a sí mismo, así como crear tantas reservas como quiera.

#### Crear reserva

El gestor de equipos deberá seleccionar un número determinado de recursos (puestos) a los que tenga acceso, que siempre tendrá que ser al menos uno, y no más del establecido por la organización (configurado en la plataforma de gestión).

Todos los recursos deben estar en la misma planta, asi como no estar ocupados para la fecha escogida.

Si no se asigna una reserva gestionada después de crearla, se eliminará al cabo de unos minutos, establecidos también por la organización.

El gestor de equipos podrá elegir activar el check-in opcional, esto provoca que la reserva nunca expire.

#### Asignar usuarios

El gestor de equipos deberá asignar un usuario (interno o externo, o el mismo) a cada puesto seleccionado previamente. Es importante tener en cuenta que no se puede asignar el mismo usuario a puestos diferentes.

#### Editar reserva

Permite editar una instancia (un día) de una reserva gestionada, es decir, si es recurrente (se repite varias veces), se tendrá que editar día por día.

Sólo un gestor de equipos podrá editar una reserva gestionada, en la que, por supuesto, tendrá que ser el supervisor.

Sólo se permite editar el título de la reserva , así como los usuarios asignados a los puestos.

Es importante tener en cuenta que no es posible eliminar a un usuario de un puesto, y dejar ese puesto sin usuario asignado.

#### Cancelar reserva

Permite a un gestor de equipos cancelar una reserva gestionada completamente, en la que, de igual forma que para editar, tendrá que ser el supervisor.

También es posible cancelar un día concreto de una reserva gestionada, de esta forma se cancelará la reserva de ese día para todos los usuarios asignados a ese día.

Existe una última opción, que permite cancelar la reserva de un día concreto, pero sólo para un usuario en específico.
