---
title: Modelo de niveles para el particionamiento de los privilegios administrativos
ms.custom: na
ms.prod: identity-manager-2015
ms.reviewer: na
ms.service: active-directory
ms.suite: na
ms.technology: 
  - active-directory-domain-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6e3cd02-1e32-4194-a8ed-3a0b3d022a43
---
# Modelo de niveles para el particionamiento de los privilegios administrativos
## Introducción

El actual entorno de amenazas ha diluido la eficacia de una defensa centrada en el perímetro, a pesar de que el perímetro sigue siendo un componente válido de una estrategia mayor. La pérdida de este perímetro requiere que una organización asuma que ya se produjo la infracción de seguridad y diseñe, en consecuencia, defensas para los recursos informáticos y de negocio. Con la finalidad de permitir que las organizaciones realicen una administración a gran escala, en este documento se describe un modelo de seguridad que pretende brindar protección contra la elevación de privilegios, lo que ofrece una buena experiencia del usuario (mientras que sigue respetando los procedimientos recomendados y los principios de seguridad).

La partición de los privilegios administrativos en niveles simplifica el proceso de determinar los usuarios y grupos apropiados para incluirlos en un [*entorno bastión*](https://technet.microsoft.com/library/mt620090.aspx).

## Antecedentes: Elevación de privilegios en bosques de Active Directory

Las cuentas de usuarios, servicios o aplicaciones que reciben privilegios administrativos completos y permanentes sobre los bosques de Active Directory de Windows Server presentan una gran cantidad de riesgos para la misión y el negocio de la organización. Estas cuentas suelen ser objetivo de los atacantes porque, si se ven comprometidas, el atacante de inmediato tiene el privilegio para conectarse, de forma arbitraria, a otros servidores o aplicaciones del dominio.

En algunas implementaciones, los dominios se configuraron de manera tal que los operadores de cuentas y los operadores de servidores son, en efecto, administradores totales a través de las cuentas, servidores y aplicaciones que estos roles pueden, de hecho, controlar. En la mayoría de los casos, estas configuraciones se realizaron para admitir la necesidad que tiene una aplicación de ejercer los derechos administrativos para todos los clientes o los servidores en el dominio, o bien todas las cuentas de usuario o de equipo en el dominio. Sin embargo, son pocas las aplicaciones que requieren ambos tipos de derechos, por lo tanto, otorgar derechos de administrador de directorio para ambos crea un estado de demasiados permisos, el que beneficia a un atacante o a un infiltrado malintencionado.

## Modelo en niveles para mitigar la elevación de privilegios

Las siguientes instrucciones ofrecen un modelo simple para clasificar rápidamente los recursos existentes y configurar zonas para limitar el uso de la cuenta. Este modelo adapta los modelos jerárquicos Biba y Bell-LaPadula al control administrativo y está representado con tres niveles de privilegios administrativos, más un nivel para usuarios finales que no son administradores de todo el dominio. Para particionar y administrar de mejor forma los derechos de acceso administrativo, las cuentas y las aplicaciones se clasifican en uno de cuatro niveles de privilegios, según la capacidad que tengan de afectar las operaciones y la misión de la organización:

- **Nivel 0:** Admins. de bosque: Control administrativo directo o indirecto de los controladores de dominio, dominios o bosque de Active Directory.

- **Nivel 1:** Admins. de servidor: Control administrativo directo o indirecto sobre un servidor único o varios servidores.

- **Nivel 2:** Admins. de estación de servicio: Control administrativo directo o indirecto sobre varios dispositivos.

- **Nivel 3:** Usuarios: Control administrativo o usuarios sin privilegios sobre un dispositivo único.

Algunas necesidades del negocio específicas pueden requerir otros niveles o una segmentación adicional, pero este modelo se puede usar como punto de partida.

![pam-tiers](/Image/pam-tiers.jpg)

### Guías sobre el modelo de privilegio en niveles

El modelo está diseñado para evitar la escalación de una ruta de privilegios de un atacante que utiliza credenciales robadas y está definido según las reglas siguientes:

1. Todos los recursos que se administrarán (grupo, cuenta, servidores, estación de trabajo, objeto de Active Directory o aplicación) estarán clasificados exactamente en un nivel para evitar una escalación de la ruta de privilegios de un atacante que usa técnicas de robo de credencial.

2. El personal que cuenta con responsabilidades para iniciar sesión en recursos y administrarlos en varios niveles tendrá cuentas administrativas independientes creadas para cada uno de los niveles requeridos. Toda cuenta que actualmente inicie sesión en varias categorías se dividirá en varias cuentas, donde cada una de ellas encajará dentro de una sola definición de nivel. Estas cuentas también deberán tener distintas contraseñas.

3. Las cuentas administrativas podrían no controlar recursos de nivel superior a través del acceso administrativo, como las listas de control de acceso (ACL), agentes de aplicación o control de cuentas de servicio. Las cuentas que controlar un nivel superior podrían no iniciar sesión en equipos de nivel inferior, porque el inicio de sesión en dichos equipos podrían exponer y, de forma inadvertida, otorgar control de las credenciales y privilegios de la cuenta asignados a esa cuenta. En algunas excepciones específicas, las conexiones de Escritorio remoto, con RDP con modo de administración restringida, se podrían usar sin exponer las credenciales.

4. Las cuentas administrativas pueden controlar los recursos de nivel inferior tal como lo requiere su rol, pero solo a través de interfaces de administración que se encuentran en el nivel superior y que no exponen las credenciales; por ejemplo, las cuentas de administración de dominio (nivel 0) que administran objetos de cuenta de Active Directory de administración de servidor (nivel 1) a través de consolas de administración de Active Directory en un controlador de dominio (nivel 0).

5. Cada unidad organizativa (UO) que contiene cuentas de equipo solo puede contener cuentas de equipo para ese nivel específico. Si se trata de una unidad organizativa que contiene cuentas de equipo para varios niveles, las cuentas de equipo de un nivel se moverán a otro dominio, y se creará una unidad organizativa o subunidades organizativas independientes para alojar cada nivel respectivo.

### Nivel 0: Administrador de bosque/dominio

Cualquier persona que tenga control sobre los grupos, cuentas, controladores de dominio, objetos especiales de Active Directory y aplicaciones en este nivele tiene la capacidad de ejecutar código arbitrario en cualquier lugar del dominio o el bosque. El ámbito del nivel 0 está relacionado con un dominio de Active Directory único, a pesar de que algunas cuentas u otros elementos pueden tener un impacto de nivel 0 en varios dominios. El nivel 0 incluye:

#### Servidores y estaciones de trabajo

- Controladores de dominio
- Servidores que hospedan una aplicación de administración que controla un agente en un controlador de dominio.
- Servidores o estaciones de trabajo donde inician sesión las cuentas de nivel 0, incluido cualquier servidor o estación de trabajo donde se expone una credencial de nivel 0 (como servidores o estaciones de trabajo que ejecutan un servicio con las mismas credenciales de cuenta que ejecutan un servicio en un servidor de nivel 0 o que, de otro modo, se usan para administrar un servidor de nivel 0).

#### Objetos de Active Directory

- El objeto AdminSDHolder en el contenedor del sistema de cada dominio.
- El contenedor del sistema en el contexto de nomenclatura de dominio.
- La unidad organizativa de controladores de dominio.
- Cualquier unidad organizativa que contenga objetos de nivel 0 (incluidas unidades organizativas principales).
- Cualquier directiva de grupo vinculada a una unidad organizativa de nivel 0.

#### Grupos de Active Directory

- Grupos de AD integrados y predefinidos, además de miembros de esos grupos, entre los que se incluyen:
- Admins. del dominio
- Administradores de empresas
- Administradores de esquema
- Administradores integrados
- Operadores de cuentas
- Operadores de copia de seguridad

- Grupos a los que se delegaron permisos equivalentes a un grupo de nivel 0 (mencionados anteriormente), que incluyen:
- La capacidad de modificar todos, o casi todos, los objetos en Active Directory.
- La capacidad de restablecer las contraseñas de cualquier cuenta de nivel 0.
- Los grupos que recibieron control total o de modificación sobre cualquier otro objeto de nivel 0 (usuario, grupo, equipo, UO, directiva de grupo u objetos especiales).

#### Cuentas

- La cuenta predefinida de administrador.
- Cuentas que forman parte de cualquier grupo de nivel 0.
- Cuentas que tienen privilegios de control total o de escritura sobre cualquier objeto de nivel 0.
- Cuentas a las que se delegaron permisos equivalentes a un grupo de nivel 0 (incluidos los privilegios enumerados anteriormente en los grupos de nivel 0).
- Cuentas con derechos administrativos sobre aplicaciones en nivel 0.

#### Aplicaciones

- Aplicaciones que se ejecutan como servicio en controladores de dominio.
- Aplicaciones que controlan un agente en controladores de dominio.

#### Hardware y dispositivos

- Hardware en el que se ejecutan los sistemas de nivel 0 (tenga en cuenta que esto podría depender de si hay VM blindadas implementadas para los controladores de dominio).
- Cualquier personas con acceso a hardware físico de controladores de dominio, sistemas y copias de seguridad similares.
- Cualquier persona con acceso administrativo a los hosts de máquinas virtuales donde se hospedan los equipos virtualizados de nivel 0.
- Dispositivos donde se ingresan o almacenan credenciales de nivel 0 (como dispositivos móviles usados para acceso remoto).

### Nivel 1: Administradores de servidores y aplicaciones

Cualquier persona con control sobre los servidores de controlador no de dominio y las cuentas y grupos administrativos para ellos en el entorno de dominio de producción de Active Directory tiene la capacidad de ejecutar código arbitrario en cualquier lugar de esos servidores. El ámbito de nivel 1 está relacionado con un dominio de Active Directory único. Los recursos de nivel 1 incluyen todos los recursos que cumplen con los siguientes criterios (y que no están clasificados como nivel 0):

#### Servidores y estaciones de trabajo

- Servidores unidos al dominio
- Estaciones de trabajo donde inician sesión las cuentas de nivel 1, incluida cualquier estación de trabajo donde se expone una credencial de nivel 1 (como estaciones de trabajo que ejecutan un servicio con las mismas credenciales de cuenta que ejecutan un servicio en un servidor de nivel 1 o que, de otro modo, se usan para administrar un servidor de nivel 1).

#### Objetos de Active Directory

- Cualquier unidad organizativa que contiene objetos de nivel 1.
- Cualquier directiva de grupo vinculada a una unidad organizativa de nivel 1.

#### Grupos de Active Directory

- El grupo Operadores de servidor (o un grupo miembro del mismo).
- Grupos cuyos miembros reciben privilegios de control total o de escritura sobre cualquier objeto de nivel 1, o bien grupos que reciben control total o de modificación sobre cualquier objeto de nivel 1 (usuario, grupo, equipo, UO u objetos de directiva de grupo).

#### Cuentas

- Cuentas que forman parte de cualquier grupo de nivel 1.
- Cuentas con privilegios de control total o de escritorio sobre cualquier otro objeto de nivel 1 (con frecuencia, cuentas de soporte técnico), incluidas cuentas a las que se delegan permisos equivalentes a un grupo de nivel 1 (que incluyen los privilegios nombrados anteriormente en los grupos de nivel 1).
- Cuentas que forman parte del grupo de administradores locales en uno o más servidores.
- Cuentas con derechos administrativos en aplicaciones de nivel 1.

#### Aplicaciones

- Aplicaciones que se ejecutan como servicio en servidores de nivel 1.
- Aplicaciones que controlan un agente en servidores de nivel 1.

#### Hardware y dispositivos

- Hardware en el que se ejecutan los sistemas de nivel 1.
- Cualquier persona con acceso al hardware físico de los servidores.
- Cualquier persona con acceso administrativo a los hosts de máquinas virtuales donde se hospedan los equipos virtualizados de nivel 1.
- Dispositivos donde se ingresan o almacenan credenciales de nivel 1 (como dispositivos móviles usados para acceso remoto).

### Nivel 2: Administradores de estación de trabajo y usuario final

Cualquier persona con control sobre las estaciones de trabajo y los usuarios estándar en el entorno de dominio de producción de Active Directory tiene la capacidad de ejecutar código arbitrario en cualquier lugar de esas estaciones de trabajo o en esos usuarios. El ámbito de nivel 2 está relacionado con un dominio de Active Directory único. Los recursos de nivel 2 incluyen todos los recursos que cumplen con los siguientes criterios (y que no están clasificados como nivel 0 o nivel 1):

#### Estaciones de trabajo

- Estaciones de trabajo en el entorno donde cualquier usuario podría iniciar sesión (sin incluir las estaciones de trabajo administrativas que las cuentas de nivel 1 o nivel 0 usan).

#### Objetos de Active Directory

- Cualquier unidad organizativa que contiene objetos de nivel 2.
- Cualquier directiva de grupo vinculada a una unidad organizativa de nivel 2.

#### Grupos de Active Directory

- Los grupos que recibieron control total o de modificación sobre cualquier objeto de nivel 2 o nivel 3 (usuario, grupo, equipo, UO u objetos de directiva de grupo).
- Grupos que forman parte del grupo de administradores locales en una o más estaciones de trabajo (por ejemplo, administradores de soporte técnico y otros grupos de soporte técnico para el equipo y el usuario final).

#### Cuentas

- Cuentas que forman parte de cualquier grupo de nivel 2.
- Cuentas que forman parte del grupo de administradores local en una o más estaciones de trabajo.

>{Esto puede incluir a todos los usuarios finales si se les otorgan derechos administrativos sobre sus estaciones de trabajo.}

- Cuentas que tienen privilegios de control total o de escritura sobre cualquier objeto de nivel 2.
- Cuentas con derechos administrativos sobre las aplicaciones en el nivel 2.

#### Aplicaciones

- Aplicaciones que se ejecutan como servicio en estaciones de trabajo.
- Aplicaciones que controlan un agente en estaciones de trabajo.

#### Hardware y dispositivos

- Hardware en el que se ejecutan los sistemas de nivel 2.
- Cualquier persona con acceso al hardware físico de las estaciones de trabajo.
- Cualquier persona con acceso administrativo a los hosts de máquinas virtuales donde se hospedan los equipos virtualizados de nivel 2.
- Dispositivos donde se ingresan o almacenan credenciales de nivel 2 (como dispositivos móviles usados para acceso remoto).

### Nivel 3: Usuarios estándar

Este nivel describe a los usuarios estándar sin privilegios administrativos sobre varios equipos del dominio.

## Restricción de la exposición de las credenciales con restricciones de inicio de sesión

Contener el riesgo de robo de credenciales en las cuentas administrativas generalmente requiere reformular las prácticas administrativas para limitar la exposición a los atacantes. Como primer paso, se recomienda que las organizaciones:

- Limiten la cantidad de hosts en los que se exponen las credenciales administrativas.
- Limiten los privilegios de rol al mínimo requerido.
- Garanticen que las tareas administrativas no se realizan en hosts usados para las actividades de usuario estándar (por ejemplo, correo electrónico y exploración web).

El próximo paso es implementar restricciones de inicio de sesión y habilitar los procesos y prácticas para cumplir con los requisitos del modelo en niveles. De forma ideal, la exposición de las credenciales se verá reducida al menor privilegio posible requerido para el rol dentro de cada nivel:

Se deben aplicar restricciones de inicio de sesión para asegurar lo siguiente:

- Los administradores de dominio (nivel 0) no pueden iniciar sesión en servidores empresariales (nivel 1) ni en estaciones de trabajo de usuario estándar (nivel 2).
- Los administradores de servidor (nivel 1) no pueden iniciar sesión en estaciones de trabajo de usuario estándar (nivel 2).

>[Nota] {Los administradores de servidor no deben estar en el grupo de administración de dominio. El personal que tiene responsabilidades para administrar tanto los controladores de dominio como los servidores empresariales deben tener cuentas independientes}.

Las restricciones de inicio de sesión se pueden aplicar con lo siguiente:

- Restricciones de derechos de inicio de sesión de directiva de grupo, incluida la configuración de Denegar el acceso a este equipo desde la red, Denegar el inicio de sesión como trabajo por lotes, Denegar el inicio de sesión como servicio, Denegar localmente el inicio de sesión, Denegar el inicio de sesión a través de Escritorio remoto.
- Silos y directivas de autenticación, si usa Windows Server 2012 o posterior.
- Autenticación selectiva, si la cuenta está en un bosque administrativo dedicado.

En el siguiente documento, [*Planificación de un entorno bastión*](https://technet.microsoft.com/library/mt620090.aspx), se describe cómo agregar un bosque administrativo dedicado para que Microsoft Identity Manager establezca las cuentas administrativas.




