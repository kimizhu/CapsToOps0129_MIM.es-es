---
title: Definici&#243;n de roles para Privileged Access Management
ms.custom: na
ms.prod: identity-manager-2015
ms.reviewer: na
ms.service: active-directory
ms.suite: na
ms.technology: 
  - active-directory-domain-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a368e8e-68e1-4f40-a279-916e605581bc
---
# Definici&#243;n de roles para Privileged Access Management
## Introducción

Una forma habitual de definir los roles necesarios para Privileged Access Management es construir y revisar una hoja de cálculo que enumera los roles e identifica los requisitos de gobernanza y los permisos que requiere cada rol.

Los requisitos de gobernanza variarán según cualquier identidad existente y los requisitos de cumplimiento o directivas de acceso que deberían abordar los controles de Privileged Access Management. Los parámetros para identificar cada rol podrían incluir identificar al propietario del rol, los usuarios candidatos que puede haber en ese rol y determinar cuales controles de autenticación, aprobación o notificación deberían estar asociados con el uso del rol.

Los permisos de rol dependerán de las aplicaciones que se administran. Este artículo usa a Active Directory como aplicación de ejemplo y divide los permisos en dos categorías:

- Las necesarias para administrar el servicio de Active Directory mismo (por ejemplo, configurar la topología de replicación).

- Las necesarias para administrar los datos almacenados en Active Directory (por ejemplo, crear usuarios y grupos).

## Consideraciones de la selección de rol

Para comenzar, cree una ficha en una hoja de cálculo y escriba cada rol potencial en una fila. Para encontrar los roles adecuados, identifique las aplicaciones dentro del ámbito de la administración (¿son de nivel 0, nivel 1 o nivel 2?) y los privilegios que afectan la confidencialidad, la integridad o la disponibilidad de la aplicación. Considere también las dependencias que podría tener la aplicación en otros componentes del sistema, como bases de datos, infraestructura de red o de seguridad o la plataforma de virtualización o de hospedaje. Luego, determine cómo agrupar esos privilegios, de manera tal que los usuarios que son administradores puedan seleccionar fácilmente el rol adecuado, sin recibir inadvertidamente demasiados permisos.

El objetivo del modelado de rol es diseñar la asignación con menos privilegios. Esto puede basarse en las responsabilidades organizacionales actuales (o planificadas) para los usuarios e incluiría el privilegio que requieren las obligaciones del usuario. Además, podría incluir también los privilegios que simplifican las operaciones, sin crear ningún riesgo.

Otras consideraciones en la evaluación de los permisos para incluir un rol son:

- ¿Cuántas personas trabajan en un rol determinado? Si no hay 2, como mínimo, podría ser prematuro definir un rol si nadie lo va a ejercer o si está definido por las obligaciones de una persona determinada.

- ¿Cuántos roles asume una persona? ¿Los usuarios podrían seleccionar el rol correcto para su tarea?

- ¿La población de usuarios y la forma en que interactúan con las aplicaciones sería compatible con Privileged Access Management?

- ¿Es posible separar la administración y auditoría, de manera que un usuario en un rol administrativo no pueda borrar los registros de auditoría de sus acciones?

Al final de esta sección, se incluye una lista de roles de ejemplo.

## Requisitos de gobierno de rol

A medida que identifique los roles de candidato, comience a rellenar la hoja de cálculo. Cree columnas para los requisitos pertinentes a su organización y, para cada rol, especifique las opciones para cada uno de ellos:

- ¿Quién es el propietario de rol que sería responsable de la definición de rol, elegir los permisos y mantener la configuración de gobierno (cambio de la forma en que se obtiene acceso a la cuenta y cómo se utiliza, etc.) del rol?

- ¿Quiénes son los titulares (usuarios) del rol que realizarán las tareas u obligaciones del rol?

- ¿Qué método de acceso (que se analiza en la sección siguiente) sería apropiado para los titulares del rol?

- ¿Se requiere la aprobación manual por parte de un propietario de rol cuando un usuario activa su rol?

- ¿Se requiere una notificación cuando un usuario activa su rol?

- ¿Usar este rol generará una alerta o notificación en un sistema SIEM con fines de seguimiento?

- ¿Es necesario restringir a los usuarios que activan el rol para que solo puedan iniciar sesión en equipos donde se requiere acceso para realizar los deberes del rol y donde hay una comprobación suficiente del host que podrá proteger los privilegios/credenciales ante un uso incorrecto?

- ¿Es necesario proporcionar una estación de trabajo de administración dedicada a los titulares del rol?

- ¿Qué permisos de aplicación (consulte la lista de ejemplo para AD) están asociados con este rol?

## Selección de un método de acceso

Puede haber varios roles en un sistema de Privileged Access Management con los mismos permisos asignados, si distintas comunidades de usuarios tienen requisitos de control de acceso. Por ejemplo, una organización puede optar por aplicar distintas directivas a sus propios empleados de tiempo completo que actúan como administradores que para los empleados de TI tercerizada de otra organización que actúen como administradores.

En algunos casos, es posible asignar a un usuario permanentemente a un rol, por lo que no es necesario que soliciten o activen una asignación de rol. Algunos ejemplos de escenarios de asignación permanente incluyen:

- Una cuenta de servicio administrada en un bosque existente

- Una cuenta de usuario en el bosque existente, con una credencial administrada fuera de PAM (por ejemplo, una cuenta "de emergencia", donde un rol como "Mantenimiento de dominio/controlador de dominio" necesario para corregir problemas de estado de controlador de dominio y confianza se asigna permanentemente a la cuenta, con una contraseña físicamente protegida).

- Una cuenta de usuario en el bosque administrativo que se autentica con una contraseña (por ejemplo, un usuario que necesita permisos administrativos permanente las 24 horas del día, los 7 días de la semana y que inicia sesión desde un dispositivo que no admite una autenticación sólida).

- Una cuenta de usuario en el bosque administrativo, con una tarjeta inteligente o una tarjeta inteligente virtual (por ejemplo, una tarjeta inteligente sin conexión, necesaria para las tareas de mantenimiento poco frecuentes).

MIM permite asignaciones dinámicas basadas en rol, en las que los privilegios se asigna temporalmente a un usuario con un flujo de trabajo y un proceso de aprobación opcional. Esto se puede aplicar tanto para una cuenta de usuario en el bosque administrativo que se autentica con una contraseña, como para una cuenta de usuario que se autentica con una tarjeta inteligente o una tarjeta inteligente virtual. En el caso de las organizaciones preocupadas por la posibilidad de robo o uso incorrecto de credenciales, la guía [Uso de Azure MFA para la activación](https://technet.microsoft.com/library/mt517876.aspx) incluye instrucciones sobre cómo configurar MIM para requerir una comprobación fuera de banda adicional en el momento de la activación de rol.

## Modelado de permisos de Active Directory delegados

Cuando se crea un dominio nuevo en Active Directory, Windows Server crea automáticamente grupos conocidos como "Admins. del dominio". Mientras estos grupos simplifican el comienzo de las operaciones y podrían ser adecuados tal como son para las organizaciones más pequeñas, en las organizaciones de mayor tamaño o en aquellas que requieren que los privilegios administrativos estén más aislados, un objetivo para los proyectos de administración de acceso con privilegios ha sido vaciar grupos como "Admins. del dominio" y reemplazar su uso con grupos adicionales que brindan personalización avanzada de permisos.

Una de las limitaciones del grupo de Admins. del dominio es que otorga permisos para tres funciones independientes: administrar el servicio de Active Directory mismo, administrar los datos contenidos en Active Directory y habilitar el inicio de sesión remoto en los equipos unidos a un dominio. Otra limitación del grupo Admins. del dominio es que no puede tener miembros de un dominio externo. Por lo tanto, en su lugar, una organización podría crear nuevos grupos de seguridad que proporcionan solo los permisos necesarios y usar MIM para brindar dinámicamente esas pertenencias a grupos a las cuentas de administrador.

### Permisos de administración de servicios de Active Directory de ejemplo

En la tabla siguiente, se brindan ejemplos de permisos que podría ser pertinente incluir en los roles para administrar AD.

| Rol| Descripción|
| ---- | ---- |
| Mantenimiento de dominio/controlador de dominio| Pertenencia en el grupo Dominio\Administradores que permite solucionar problemas en el sistema operativo del controlador de dominio, además de modificarlo, lo que promueve un controlador de dominio nuevo a un dominio existente en el bosque y la delegación de rol de AD.
| Administración de controladores de dominio virtuales| Administre máquinas virtuales de controlador de dominio con el software de administración de virtualización.Este privilegio se podrá otorgar a través del control total de todas las máquinas virtuales en la herramienta de administración o mediante el uso de la funcionalidad Control de acceso basado en rol (RBAC).|
| Extender esquema| Administre el esquema, incluida su extensión para incluir nuevas definiciones de objeto, y modifique los permisos a los objetos de esquema y los permisos predeterminados de esquema para los tipos de objeto.|
| Crear copia de seguridad de Base de datos de Active Directory| Realice una copia de seguridad de Base de datos de Active Directory en su totalidad, incluidos todos los secretos otorgados al controlador de dominio y al dominio.|
| Administrar confianzas y niveles funcionales| Cree y elimine confianzas con bosques y dominios externos.|
| Administrar sitios, subredes y replicación| Administre los objetos de topología de replicación de Active Directory, incluida la modificación de sitios, subredes y objetos de vínculo de sitio e inicie las operaciones de replicación.|
| Administrar los GPO| Cree, elimine y modifique objetos de directiva de grupo en todo el dominio.|
| Administrar zonas| Cree, elimine y modifique las zonas de DNS y los objetos en Active Directory.|
| Modificar UO de nivel 0| Modifique las UO de nivel 0 y los objetos contenidos en Active Directory.|
### Permisos de administración de datos de Active Directory de ejemplo

En la tabla siguiente, se brindan ejemplos de permisos que podría ser pertinente incluir en los roles para administrar o usar los datos contenidos en AD.

| Rol| Descripción|
| ---- | ---- |
| Modificar UO de administrador de nivel 1| Modifique las UO que contienen objetos de administrador de nivel 1 en Active Directory.|
| Modificar UO de administrador de nivel 2| Modifique las UO que contienen objetos de administrador de nivel 2 en Active Directory.|
| Administración de cuentas: Crear, eliminar, mover| Modifique cuentas de usuario estándar.|
| Administración de cuentas: Restablecer y desbloquear| Restablezca las contraseñas y desbloquee las cuentas.|
| Grupo de seguridad: Crear y modificar| Cree y modifique los grupos de seguridad en Active Directory.|
| Grupo de seguridad: Eliminar| Elimine los grupos de seguridad en Active Directory.|
| Administración de GPO| Administre todos los GPO en el dominio/bosque que no afecten los servidores de nivel 0.|
| Unir admin. de PC/local| Derechos administrativos locales a todas las estaciones de trabajo.|
| Unir admin. de servidor/local| Derechos administrativos locales a todos los servidores.|
## Ejemplo de definiciones de rol

La elección de las definiciones de rol dependerá del nivel de los servidores que las cuentas con privilegios administran. También dependerá de la elección de las aplicaciones administradas, debido a que aplicaciones como Exchange o productos empresariales de terceros, como SAP, con frecuencia traerán sus propias definiciones de rol adicionales para la administración delegada.

Las siguientes secciones dan ejemplos de escenarios empresariales típicos.

### Nivel 0: Bosque administrativo

El rol adecuado para las cuentas en el entorno bastión podrían incluir:

- Acceso de emergencia al bosque administrativo.
- Administradores de "tarjeta roja": Usuarios que son administradores del bosque administrativo.
- Usuarios que son administradores del bosque de producción.
- Usuarios en los que se delegan los derechos administrativos delegados a las aplicaciones del bosque de producción.

### Nivel 0: Bosque de producción empresarial

Los roles adecuados para administrar los recursos y las cuentas del bosque de producción de nivel 0 podrían incluir:

- Acceso de emergencia al bosque de producción.
- Administradores de directiva de grupo.
- Administradores de DNS.
- Administradores de PKI.
- Administradores de replicación y topología de AD.
- Administradores de virtualización para servidores de nivel 0.
- Administradores de almacenamiento.
- Administradores anti-malware para servidores de nivel 0.
- Administradores de SCCM para SCCM de nivel 0.
- Administradores de SCOM para SCOM de nivel 0.
- Administradores de copia de seguridad para nivel 0.
- Usuarios de controladores de administrador fuera de banda y de placa base (para la administración en horarios nocturnos o KVM) conectados a hosts de nivel 0.

### Nivel 1

Los roles para la administración y la copia de seguridad de los servidores en nivel 1 podrían incluir:

- Mantenimiento del servidor.
- Administradores de virtualización para servidores de nivel 1.
- Cuenta de examen de seguridad
- Administradores anti-malware para servidores de nivel 1.
- Administradores de SCCM para SCCM de nivel 1.
- Administradores de SCOM para SCOM de nivel 1.
- Administradores de copia de seguridad para servidores de nivel 1.
- Usuarios de controladores de administración fuera de banda y de placa base (para la administración en horarios nocturnos o KVM) conectados a hosts de nivel 1.

Además, los roles para administrar aplicaciones empresariales en nivel 1 podrían incluir:

- Administradores de DHCP.
- Administradores de Exchange.
- Administradores de Skype Empresarial.
- Administradores de la granja de SharePoint.
- Administradores de un servicio en la nube; por ejemplo, un sitio web de la empresa o un DNS público.
- Administradores de sistemas legales, financieros o de gestión del capital humano.

### Nivel 2

Los roles para la administración de equipos y usuarios no administrativos podrían incluir:

- Administradores de cuentas.
- Departamento de soporte técnico.
- Administradores de grupos de seguridad.
- Asistencia de escritorio de la estación de trabajo




