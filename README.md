# Sistema de Gestión de Turnos Digitales

### Descripción General del Sistema

Este proyecto consiste en un sistema de gestión de turnos de manera virtual, aplicando programación orientada a objetos (POO) y diversos patrones de diseño.

### Objetivos del Modelado

comprender de manera clara las funcionalidades y la arquitectura del sistema utilizando Diagrama de Caso de Uso, Diagrama de Clases con Patrones de diseños aplicados y finalmente la implementación UML.

### 1. Diagrama de Casos de Uso UML

![](https://github.com/0bamium/Sistema_de_Gestion_de_Turnos_Digitales/blob/79a9d3ab93484920dc6999ac59ea796d39bf73b1/imagenes/GestionTurnoDigital.drawio.png)

#### Descripción general

El análisis permitió identificar de manera clara los actores involucrados y las funcionalidades del sistema. Además, se aplicaron correctamente relaciones de `<<include>>` y `<<extend>>` para describir el flujo del proceso.

#### Actores identificados:

- Cliente: Responsable de reservar un turno, ver su estado y poder cancelarlo.
- Recepcionista: Responsable de atender a los clientes segun el tuno en el que se encuentra, atenderlos y posteriormente avanzar el turno y atender al nuevo cliente.

#### Casos de uso destacados y relaciones aplicadas:

##### Generar un número al turno que reservó
- `<<include>>` Generar Numero: La generación de un número para el cliente es obligatorio al momento de reservar un turno.
##### Consulta del estado del turno por SMS
- `<<extend>>` Enviar notificacion SMS:  De manera opcional, al momento de reservar un turno o cancelarlo, puede recibir una notificación por SMS.
##### Proceso de atención al cliente
- `<<include>>` Atender Cliente: El recepcionista siempre atenderá al nuevo cliente luego de llamarlo por su número.
- `<<include>>` Marcar turno atendido: Luego de atender al cliente, el recepcionista va a marcar el turno actual como "atendido" avanzando al siguiente turno y repitiendo el proceso de atención al cliente.

#### Justificación de las relaciones aplicadas:

- Se utilizaron `<<include>>` en procesos donde el caso de uso depende de otro obligatorio, como en el caso de reservar un turno, es necesario generar un número para ser atendido.
- Se utilizaron `<<extend>>` en procesos donde es opcional el proceso del caso de uso, como en el caso de enviar una notificacion SMS, ya que el cliente tiene la opcion de querer recibirla o no.

### 2. Diagrama de Clases UML con Patrones Aplicados
![](https://github.com/0bamium/Sistema_de_Gestion_de_Turnos_Digitales/blob/509f8e62dfd4a2eb9fcc419824c924742f596422/imagenes/DigramaDeClases_SistemaDeGestionDeTurnosDigitales.png)

### Justificación Arquitectónica y Patrones Aplicados

#### Selección de patrones
Para la creación del diagrama, se utilizaron los siguientes patrones para una correcta implementación
- Prototype
- Singleton
- Bridge
- Adapter

#### 1. Singleton (`SistemaDeTurnos`)

##### Justificación:
Esta decisión de diseño se fundamenta en el hecho de que el sistema debe centralizar la generación, asignación y gestión de turnos para todos los clientes y recepcionistas, por ello la mejor opcion es optar por una única instancia. Permitir múltiples instancias de SistemaDeTurnos podría provocar inconsistencias en la numeración de los turnos.

##### Intención arquitectónica:
- mantener la coherencia del flujo de turnos
- evitar la duplicación de datos
- Encapsula la lógica compartida y mejora la mantenibilidad al evitar múltiples puntos de decisión y almacenamiento de estado

#### 2. Prototype (`Turno`)

##### Justificación:
La implementacion de este patrón de diseño permite la clonación rápida y eficiente de objetos turno a partir de una instancia base o plantilla. Es útil cuando se desea crear múltiples turnos similares sin repetir la inicialización completa.

##### Intención arquitectónica:
- Promueve la reutilización de estructuras base de turnos, como plantillas o configuraciones preestablecidas
- Provee una forma flexible y eficiente de crear nuevos objetos a partir de prototipos existentes
- Nuevos tipos de turno pueden clonarse fácilmente a partir de prototipos sin modificar la lógica interna de SistemaDeTurnos.

#### 3. Adapter (`AdaptadorSMS` y `AdaptadorEmail`)

##### Justificación:
Se utiliza para integrar diferentes canales de notificación (como SMS o Email) que poseen interfaces distintas e incompatibles con la estructura esperada por el sistema.

##### Intención arquitectónica:
- Promueve la escalabilidad, ya que se pueden incorporar nuevos tipos de notificaciones sin alterar el sistema base
- Separa la lógica del negocio del sistema de las dependencias externas (como APIs de SMS o Email)

#### 3. Bridge (`NotificacionConcreta`)

##### Justificación:
Se aplica el patrón Bridge para separar la abstracción del sistema de notificaciones `Notificacion` de su implementación específica `CanalNotificacion`.

##### Intención arquitectónica:
- Mejora la mantenibilidad al permitir modificar o extender los canales de envío sin tocar la lógica principal del sistema
- Evita la explosión de subclases (como NotificacionPorSMS, NotificacionPorEmail, etc)
- Desacopla una abstracción de su implementación, permitiendo que ambas evolucionen de forma independiente.

### 3. Diagrama de Implementación UML

#### Despliegue Físico y decisiones técnicas:

### Reflexiones Finales del Modelado
