#Sistema de Gestión de Turnos Digitales

###Descripción General del Sistema

Este proyecto consiste en un sistema de gestión de turnos de manera virtual, aplicando programación orientada a objetos (POO) y diversos patrones de diseño.

###Objetivos del Modelado

comprender de manera clara las funcionalidades y la arquitectura del sistema utilizando Diagrama de Caso de Uso, Diagrama de Clases con Patrones de diseños aplicados y finalmente la implementación UML.

###1. Diagrama de Casos de Uso UML

####Descripción general

El análisis permitió identificar de manera clara los actores involucrados y las funcionalidades del sistema. Además, se aplicaron correctamente relaciones de `<<include>>` y `<<extend>>` para describir el flujo del proceso.

####Actores identificados:

- Cliente: Responsable de reservar un turno, ver su estado y poder cancelarlo.
- Recepcionista: Responsable de atender a los clientes segun el tuno en el que se encuentra, atenderlos y posteriormente avanzar el turno y atender al nuevo cliente.

####Casos de uso destacados y relaciones aplicadas:

##### Generar un número al turno que reservó
- `<<include>>` Generar Numero: La generación de un número para el cliente es obligatorio al momento de reservar un turno.
##### Consulta del estado del turno por SMS
- `<<extend>>` Enviar notificacion SMS:  De manera opcional, al momento de reservar un turno o cancelarlo, puede recibir una notificación por SMS.
##### Proceso de atención al cliente
- `<<include>>` Atender Cliente: El recepcionista siempre atenderá al nuevo cliente luego de llamarlo por su número.
- `<<include>>` Marcar turno atendido: Luego de atender al cliente, el recepcionista va a marcar el turno actual como "atendido" avanzando al siguiente turno y repitiendo el proceso de atención al cliente.

####Justificación de las relaciones aplicadas:

- Se utilizaron `<<include>>` en procesos donde el caso de uso depende de otro obligatorio, como en el caso de reservar un turno, es necesario generar un número para ser atendido.
- Se utilizaron `<<extend>>` en procesos donde es opcional el proceso del caso de uso, como en el caso de enviar una notificacion SMS, ya que el cliente tiene la opcion de querer recibirla o no.

###2. Diagrama de Clases UML con Patrones Aplicados

###Justificación Arquitectónica y Patrones Aplicados

####Selección de patrones

####1. Singleton (ConfiguracionSistema)

#####Justificación:

#####Intención arquitectónica:

####2. Prototype (PlantillaMovimiento)

#####Justificación:

#####Intención arquitectónica:

####3. Adapter (Adaptador)

#####Justificación:

#####Intención arquitectónica:

###3. Diagrama de Implementación UML

####Despliegue Físico y decisiones técnicas:

###Reflexiones Finales del Modelado
