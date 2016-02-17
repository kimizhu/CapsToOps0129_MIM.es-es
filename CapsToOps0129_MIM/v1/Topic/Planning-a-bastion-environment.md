---
title: Planificaci&#243;n de un entorno basti&#243;n
ms.custom: na
ms.prod: identity-manager-2015
ms.reviewer: na
ms.service: active-directory
ms.suite: na
ms.technology: 
  - active-directory-domain-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bfc7cb64-60c7-4e35-b36a-bbe73b99444b
---
# Planificaci&#243;n de un entorno basti&#243;n
>{Este contenido deriva de las notas del producto "Mitigating Pass-the-Hash and Other Credential Theft, version 2" ("Mitigación de los ataques pass-the-hash y otros tipos de robo de credencial, versión 2", desarrolladas por el grupo Trustworthy Computing de Microsoft Corporation}

## Introducción

Agregar un entorno bastión con un bosque administrativo dedicado a una instancia de Active Directory permite que las organizaciones administren fácilmente las cuentas administrativas, estaciones de trabajo y grupos de un entorno que tiene controles de seguridad más eficaces que los del entorno de producción existente.

Esta arquitectura permite contar con diversos controles que no serían posibles o que no podrían configurarse fácilmente en una arquitectura de un solo bosque. Este enfoque permite el aprovisionamiento de cuentas como usuarios estándar sin privilegios en el bosque administrativo y que cuentan con altos privilegios en el entorno de producción, lo que permite un mayor cumplimiento técnico de la gobernanza. Esta arquitectura también permite usar la característica de autenticación selectiva de una confianza como un medio de restringir los inicios de sesión (y la exposición de credenciales) solo a los hosts autorizados. En situaciones en las que se desea un mayor nivel de control para el bosque de producción sin el costo y la complejidad que implica una recompilación total, un bosque administrativo puede proporcionar un entorno que aumente el nivel de control del entorno de producción.

Se pueden utilizar técnicas adicionales al bosque administrativo dedicado. Estas técnicas incluyen restringir la exposición de las credenciales administrativas, limitar los privilegios de rol de los usuarios en ese bosque y garantizar que las tareas administrativas no se realicen en los hosts que se utilizan para las actividades de usuario estándar (por ejemplo, correo electrónico y exploración web).

## Consideraciones sobre el bosque de entorno bastión

Un bosque administrativo dedicado es un bosque de Active Directory de dominio único estándar dedicado a la función de administración de Active Directory. Los dominios y bosques administrativos se pueden proteger más rigurosamente que los bosques de producción, debido a los casos de uso limitados. Además, como este bosque es independiente y no confía en los bosques existentes de la organización, en caso de que, más adelante, se descubra que uno de los bosques existentes de la organización se encuentra en peligro, este peligro no se extendería al bosque dedicado.

El diseño de un bosque administrativo tiene las siguientes consideraciones:

**Ámbito limitado**: El valor de un bosque administrativo es el gran nivel de aseguramiento de calidad y una menor superficie expuesta a ataques, lo que genera un menor riesgo residual. El bosque se puede usar para albergar aplicaciones y funciones de administración adicionales, pero cada aumento en el ámbito aumentará la superficie del bosque y sus recursos expuesta a ataques. El objetivo es limitar las funciones del bosque y los usuarios administradores existentes para que la superficie expuesta a ataques sea la mínima posible; por tanto, cada aumento del ámbito se debe considerar cuidadosamente. Las cuentas existentes en un bosque administrativo dedicado deben estar en un solo nivel, normalmente el nivel 0 o el nivel 1 y, en caso de ser el nivel 1, deben estar limitadas, además, a un ámbito determinado de una aplicación (por ejemplo, aplicaciones financieras) o una comunidad de usuarios (por ejemplo, proveedores tercerizados de TI).

**Confianza restringida**: Configure la confianza desde los dominios o bosques administrados al bosque administrativo.

- Se requiere una confianza unidireccional desde el entorno de producción al bosque administrativo. Puede tratarse de una confianza de dominio o una confianza de bosque. No es necesario que el dominio del bosque administrativo confíe en los bosques y dominios administrados para poder administrar Active Directory; sin embargo, algunas aplicaciones adicionales podrían requerir una relación de confianza bidireccional, validación de la seguridad y prueba.

- Se debe utilizar la autenticación selectiva para restringir las cuentas en el bosque administrativo para que solo inicie sesión en los hosts de producción adecuados. Para mantener los controladores de dominio y delegar derechos en Active Directory, normalmente se requiere otorgar el derecho "Se permite el inicio de sesión" de los controladores de dominio a las cuentas de administración designadas de nivel 0 en el bosque administrativo. Consulte [Configuración de la autenticación selectiva](http://technet.microsoft.com/library/cc755844%28v=ws.10%29.aspx) para obtener más información.

## Implementación del bosque

En esencia, el entorno bastión incluirá una colección de servidores controladores de dominio de Active Directory para autenticación y autorización, además de servidores de Microsoft Identity Manager para la administración del ciclo de vida de las cuentas privilegiadas y el procesamiento del flujo de solicitudes. También incluirá estaciones de trabajo de administradores con privilegios para que los administradores realicen la autenticación.

### Mantenimiento de una separación lógica

Con la finalidad de asegurarse de que el entorno bastión no se vea impactado por incidentes de seguridad existentes o futuros en la instancia de Active Directory existente de la organización, se debe utilizar las siguientes guías cuando se preparan los sistemas para el entorno bastión:

- Los servidores de Windows Server no deben estar unidos a un dominio ni tampoco deben utilizar la distribución de configuración o software del entorno existente.

- El entorno bastión debe contener sus propios Servicios de dominio de Active Directory, lo que brinda Kerberos y LDAP, DNS, tiempo y servicios de tiempo al entorno bastión. Los servidores que proporcionan Servicios de dominio de Active Directory deben ejecutar Windows Server 2012 R2 o posterior y el nivel funcional del bosque debe ser el nivel Windows Server 2012 R2 o posterior.

- Microsoft Identity Manager requiere SQL Server 2012 Service Pack 1 o SQL Server 2014. Se debe implementar en servidores dedicados en el entorno bastión; MIM no debe usar una granja de bases de datos SQL en el entorno existente.

- El entorno bastión necesita que Microsoft Identity Manager 2016 esté implementado en el escenario PAM; especialmente, deben estar implementados los componentes de PAM y el Servicio MIM.

- El software y los medios de copia de seguridad del entorno bastión deben estar separados de los sistemas de los bosques existentes, de manera tal que un administrador del bosque existente no pueda trastocar una copia de seguridad del entorno bastión.

- Los usuarios que administrar los servidores del entorno bastión deben iniciar sesión desde estaciones de trabajo a la que los administradores del entorno existente no puedan tener acceso, de manera tal que no se filtren las credenciales correspondientes al entorno bastión. A continuación, se describen con mayor detalle la implementación y la protección de las estaciones de trabajo administrativas dedicadas.

### Aseguramiento de la disponibilidad de los servicios de administración desde el entorno bastión

A medida que la administración de las aplicaciones del bosque existente hace la transición al entorno bastión, la planificación de la implementación del entorno bastión debe considerar cómo brindar la disponibilidad suficiente como para satisfacer los requisitos de esas aplicaciones. Las técnicas incluyen:

- Implementar Servicios de dominio de Active Directory en varios equipos del entorno bastión. Se necesitan al menos dos para garantizar que la autenticación continúe, incluso si un servidor se reinicia de forma temporal para realizar un mantenimiento programado. Es posible que se requieran equipos adicionales para una mayor carga o si la organización tiene recursos y administradores ubicados en varias regiones geográficas.

- Preparar cuentas de emergencia en el bosque existente y en el bosque administrativo dedicado, con fines de emergencia.

- Implementar SQL Server y Servicio MIM en varios equipos del entorno bastión.

- Mantener una copia de seguridad, a partir de cada cambio en los usuarios o las definiciones de rol en el bosque administrativo dedicado, de AD y SQL para la recuperación ante desastres.

### Configuración de los permisos adecuados de Active Directory

El bosque administrativo debe estar configurado en el menor nivel de privilegio según los requisitos para la administración de Active Directory.

- Las cuentas existentes en el bosque administrativo que se usan para administrar el entorno de producción no deben contar con privilegios administrativos para el bosque administrativo o los dominios o estaciones de trabajo que existen en él.

Por ejemplo, si Alice es responsable de las operaciones en el entorno bastión, Bob es propietario de rol para la administración de Exchange y Carol es administradora de Exchange, en el bosque administrativo dedicado, ni Bob ni Carol necesitarían estar en el grupo de administradores en el entorno administrativo dedicado.

- Un proceso sin conexión controlará rigurosamente los privilegios administrativos sobre el bosque administrativo mismo, con el fin de disminuir la posibilidad de que un atacante o un infiltrado malintencionado borre los registros de auditoría. Esto también ayuda a asegurarse de que el personal con cuentas de administración de producción no flexibilice las restricciones sobre sus cuentas y aumente el riesgo para la organización.

- El bosque administrativo debe respetar las configuraciones de Microsoft Security Compliance Manager (SCM) para el dominio, incluidas configuraciones seguras para los protocolos de autenticación.

Cuando cree el entorno bastión, antes de instalar Microsoft Identity Manager, identifique y cree las cuentas que se usarán para la administración dentro de este entorno. Esto incluirá:

- **Cuentas de emergencia**. Estas cuentas solo podrán iniciar sesión en los controladores de dominio en el entorno bastión.

- **Administradores de "tarjeta roja"**. Estas cuentas de usuario tienen con finalidad aprovisionar otras cuentas y realizar mantenimiento no programado. No tienen acceso a bosques o sistemas existentes fuera del entorno bastión. Las credenciales, por ejemplo, una tarjeta inteligente, deben protegerse de manera física y se debe registrar el uso de estas cuentas.

- **Cuentas de servicio**, que son necesarias para Microsoft Identity Manager, SQL Server y otro tipo de software instalado en el entorno bastión.

### Integración con SIEM y herramientas de análisis del comportamiento

Se deben diseñar controles de detección para el bosque administrativo con el fin de alertar anomalías existentes en el bosque administrativo. La cantidad limitada de actividades y escenarios autorizados puede ayudar a ajustar estos controles de manera más precisa que en el entorno de producción. Esto puede incluir exportar los registros desde Active Directory y Microsoft Identity Manager a un sistema SIEM para su análisis.

### Protección de los hosts

Todos los hosts, incluidos controladores de dominio, servidores y estaciones de trabajo unidas al bosque administrativo, deben tener instalados y actualizados los sistemas operativos y Service Packs más recientes. Además,

- Las aplicaciones necesarias para realizar la administración deben estar instaladas previamente en las estaciones de trabajo, para que no sea necesario que las cuentas que las usan estén en el grupo de administradores locales para instalarlas. Normalmente, el mantenimiento de los controladores de dominio se realiza con RDP y con Herramientas de administración remota del servidor.

- Las actualizaciones de seguridad se deben aplicar automáticamente a los hosts del bosque administrativo. Aunque esto puede generar un riesgo de interrumpir las operaciones de mantenimiento de los controladores de dominio, permite mitigar, en gran medida, el riesgo de seguridad de las vulnerabilidades a las que no se aplicó una revisión.

Es posible configurar Windows Server Update Services para que apruebe automáticamente las actualizaciones. Si desea obtener más información, consulte la sección "Aprobación automática de las actualizaciones para instalación" en Aprobación de las actualizaciones.

#### Protección de las estaciones de trabajo

Cualquier hosts donde los administradores ingresen credenciales o realicen tareas administrativas cuentan con los privilegios asociados con la cuenta que se usa, incluso si es de manera temporal. El acto de escribir físicamente una contraseña, un PIN de tarjeta inteligente o cualquier otro comprobador, o de conectar un dispositivo de autenticación física otorga los permisos de las credenciales a ese equipo. El riesgo que corre un sistema se mide según la actividad de mayor riesgo que se realiza en él; por ejemplo, explorar Internet, enviar y recibir correo electrónico o usar otras aplicaciones que procesan contenido desconocido o que no es de confianza.

Los hosts administrativos incluyen los siguientes equipos:

- Un equipo de escritorio, en el que se escriben o ingresan físicamente las credenciales del administrador.

- "Servidores de salto" administrativos, donde se ejecutan las herramientas y las sesiones administrativas.

- Todos los hosts donde se realizan acciones administrativas, incluidos los que usan un escritorio de usuario estándar que ejecuta un cliente RDP para administrar servidores y aplicaciones de forma remota.

- Servidores que hospedan aplicaciones que se deben administrar, y a los que no se puede tener acceso mediante RDP con modo de administración restringida o la comunicación remota de Windows PowerShell.

#### Implementación de estaciones de trabajo administrativas dedicadas

A pesar de ser inconvenientes, es posible que las estaciones de trabajo protegidas e independientes dedicadas a usuarios con credenciales administrativas de alto impacto sean necesarias para brindar un host con un nivel de seguridad igual o mayor que el nivel de los privilegios otorgados a las credenciales. Mantener la seguridad ante un adversario determinado y talentoso puede requerir tomar medidas adicionales, como se muestra a continuación:

- **Comprobación de que todos los medios creados son limpios**, con la finalidad de mitigar el malware instalado en una imagen maestra o insertado en un archivo de instalación durante la descarga o el almacenamiento.

- **Líneas base de seguridad** que se deben usar como configuraciones iniciales.

Los clientes pueden usar Microsoft Security Compliance Manager (SCM) para configurar las líneas base en los hosts administrativos.

- **Arranque seguro**, para mitigar el riesgo de atacantes o malware que intenten cargar código sin firma en el proceso de arranque.

Esta característica se presentó en Windows 8 para usar Unified Extensible Firmware Interface (UEFI).

- **Restricción de software**, para garantizar que solo se ejecute software administrativo autorizado en los hosts administrativos.

Los clientes pueden usar AppLocker para esta tarea con una lista blanca de aplicaciones autorizadas, con la finalidad de evitar que se ejecute software malintencionado y aplicaciones no compatibles.

- **Cifrado del volumen completo** para mitigar la pérdida física de equipos, como equipos portátiles administrativos que se usan de forma remota.

- **Restricciones USB**, para protección contra vectores de infección físicos.

- **Aislamiento de la red**, para protección contra ataques a la red y acciones administrativas involuntarias. Los firewalls de host deben bloquear todas las conexiones entrantes, excepto las que se requieren de forma explícita, y bloquear todo el acceso a Internet saliente innecesario.

- **Antimalware**, para protección contra malware y amenazas conocidas.

- **Mitigaciones de vulnerabilidades**, para mitigar las amenazas y vulnerabilidades desconocidas, incluido Enhanced Mitigation Experience Toolkit (EMET).

- **Análisis de la superficie expuesta a ataques**, para evitar el ingreso de nuevos vectores de ataque a Windows durante la instalación de software nuevo.

El uso de herramientas como el analizador de superficie expuesta a ataques (ASA) ayudará a evaluar las opciones de configuración de un host y a identificar los vectores de ataque que ingresaron debido a los cambios en la configuración o un software.

- Los usuarios no deberían necesitar privilegios administrativos para el equipo local.

- Las sesiones de RDP salientes deben tener el modo RestrictedAdmin, excepto cuando lo requiere el rol. Consulte [Novedades en Servicios de Escritorio remoto en Windows Server](https://technet.microsoft.com/en-us/library/dn283323.aspx) para obtener más información.

Algunas de estas medidas pueden parecer extremas, pero las revelaciones públicas realizadas en los últimos años mostraron las funcionalidades importantes que poseen los adversarios experimentados para poner en peligro sus objetivos.

### Establecimiento de la confianza y preparación de dominios existentes para su administración desde el entorno bastión

MIM incluye cmdlets de PowerShell para ayudar a establecer la confianza entre los dominios AD existentes y el bosque administrativo dedicado en el entorno bastión. Una vez que se implementa el entorno bastión, y antes de que ningún usuario o grupo se convierta en JIT, los cmdlets New-PAMTrust y New-PAMDomainConfiguration actualizarán las relaciones de confianza de dominio y crearán los artefactos necesarios para AD y MIM.

Cuando la topología de Active Directory existente cambia, los cmdlets `Test-PAMTrust`, `Test-PAMDomainConfiguration`, `Remove-PAMTrust` y `Remove-PAMDomainConfiguration` se pueden usar para actualizar las relaciones de confianza.

#### Procedimientos para establecer la confianza en cada bosque

El cmdlet New-PAMTrust se debe ejecutar una vez para cada bosque existente. Se invoca en el equipo del Servicio MIM en el dominio administrativo. Los parámetros para este comando son el nombre de dominio del dominio principal del bosque existente y la credencial de un administrador de ese dominio.

```
New-PAMTrust -SourceForest "contoso.local" -Credentials (get-credential)
```

Después de establecer la confianza, configure cada dominio para habilitar la administración desde el entorno bastión, tal como se describe en la siguiente sección.

#### Procedimientos para habilitar la administración de cada dominio

Existen siete requisitos para habilitar la administración para un dominio existente.

1. En el dominio existente, debe haber un grupo cuyo nombre sea el nombre de dominio de NetBIOS, seguido de tres signos de dólar; por ejemplo, "CONTOSO$$$". El ámbito del grupo debe ser "local de dominio" y el tipo de grupo debe ser "Seguridad". Esto será necesario para los grupos que se creen en el bosque administrativo dedicado con el mismo identificador de Seguridad que los grupos en este dominio. Esto se puede hacer con el siguiente comando de PowerShell, que un administrador del dominio existente puede realizar y ejecutar en una estación de trabajo unida al dominio existente:

```
New-ADGroup -name 'CONTOSO$$$' -GroupCategory Security -GroupScope DomainLocal -SamAccountName 'CONTOSO$$$'
```

2. La configuración de la directiva de grupo en el controlador de dominio para auditoría debe incluir la auditoría de operaciones exitosas y operaciones con error para Auditar la administración de cuentas y Auditar el acceso del servidor de directorio. Esto se puede realizar con la Consola de administración de directivas de grupo, que un administrador del dominio existente puede realizar y ejecutar en una estación de trabajo unida al dominio existente:

3. **Configuración de la auditoría**. Vaya a Inicio, Herramientas administrativas y, luego, inicie Administración de directivas de grupo.

4. Vaya a Bosque: contoso.local, Dominios, contoso.local, Controladores de dominio, Directiva predeterminada de controladores de dominio. Aparecerá un mensaje informativo.

![pam-group-policy-management-editor](/Image/pam-group-policy-management.jpg)

5. Haga clic con el botón derecho en Directiva predeterminada de controladores de dominio y seleccione Editar… en el menú contextual. Aparecerá una ventana nueva.

6. En la ventana Editor de administrador de directivas de grupo, bajo el árbol Directiva predeterminada de controladores de dominio, localice y expanda Configuración del equipo, Directivas, Configuración de Windows, Configuración de seguridad, Directivas locales, Directiva de auditoría.

![pam-group-policy-management-editor](/Image/pam-group-policy-management-editor.jpg)

5. En el panel Detalles, haga clic con el botón derecho en Auditar la administración de cuentas y seleccione Propiedades en el menú contextual. Haga clic en Definir esta configuración de directiva, seleccione Correcto, seleccione Error, y haga clic en Aplicar y en Aceptar.

6. En el panel Detalles, haga clic con el botón derecho en Auditar el acceso del servicio de directorio y seleccione Propiedades en el menú contextual. Haga clic en Definir esta configuración de directiva, seleccione Correcto, seleccione Error, y haga clic en Aplicar y en Aceptar.

![pam-group-policy-management-editor2](/Image/pam-group-policy-management-editor2.jpg)


7. Cierre las ventanas Editor de administración de directivas de grupo y Administración de directivas de grupo. A continuación, para aplicar la configuración de auditoría, inicie una ventana de PowerShell y escriba:

```
gpupdate /force /target:computere
```

El mensaje “La actualización de la directiva de equipo se completó correctamente.” debe aparecer después de unos minutos.

8. Los controladores de dominio deben permitir conexiones de RPC sobre TCP/IP para LSA desde el entorno bastión. En versiones anteriores de Windows Server, la compatibilidad de TCP/IP en LSA debe estar habilitada en el registro:

```
New-ItemProperty -Path HKLM:SYSTEM\\CurrentControlSet\\Control\\Lsa -Name TcpipClientSupport -PropertyType DWORD -Value 1
```

9. El cmdlet `New-PAMDomainConfiguration` se debe ejecutar en el equipo de Servicio MIM en el dominio administrativo. Los parámetros para este comando son el nombre de dominio del dominio existente y la credencial de un administrador de ese dominio.

```
 New-PAMDomainConfiguration -SourceDomain "contoso" -Credentials (get-credential)
```

10. Las cuentas del bosque bastión que se usan para establecer roles (administradores que usan el cmdlet `New-PAMUser` y el cmdlet `New-PAMGroup`), así como la cuenta que usa el servicio de supervisión de MIM, necesitan permisos de lectura en ese dominio.

Por ejemplo, si CORPDC es un controlador de dominio del dominio existente CONTOSO y PRIV\\Administrador es el usuario en el entorno bastión que necesita acceso de lectura, estos pasos habilitan el acceso de lectura al dominio por parte de un administrador y del servicio de supervisión.

11. **En CORPDC, habilite el acceso de lectura a AD para los administradores de PRIV y el servicio de supervisión.** Asegúrese de que inició sesión en CORPDC como administrador del dominio Contoso (por ejemplo, como Contoso\Administrador).

12. Inicie Usuarios y equipos de Active Directory.

13. Haga clic con el botón derecho en el dominio contoso.local y seleccione Delegar control.

14. En la pestaña Usuarios y grupos seleccionados, haga clic en Agregar.

15. En la ventana emergente Seleccionar usuarios, equipos o grupos, haga clic en Ubicaciones y cambie la ubicación a priv.contoso.local. Como nombre de objeto, escriba Admins. del dominio y haga clic en Comprobar nombres. Cuando aparezca una ventana emergente, escriba priv\administrador como nombre de usuario y la contraseña.

16. Después de Admins. del dominio, escriba "; MIMMonitor". Cuando aparezcan subrayados los nombres Admins. del dominio y MIMMonitor, haga clic en Aceptar y, a continuación, haga clic en Siguiente.

17. En la lista de tareas comunes, seleccione "Leer toda la información del usuario" y, luego, haga clic en Siguiente y en Finalizar.

18. Cierre Usuarios y equipos de Active Directory.

>{Si el objetivo del proyecto de Privileged Access Management es disminuir la cantidad de cuentas con privilegios de administrador de dominio asignados permanentemente al dominio, debe existir una cuenta *de emergencia* en el dominio, en caso de que, más adelante, se genere un problema con la relación de confianza. En cada dominio deben existir cuentas para el acceso de emergencia al bosque de producción y solo deberían tener acceso a los controladores de dominio. En el caso de las organizaciones con varios sitios, es posible que se requieran cuentas adicionales para redundancia.}

19. Por último, revise los permisos en el objeto *AdminSDHolder* del contenedor Sistema de ese dominio. El objeto *AdminSDHolder* tiene una lista de control de acceso (ACL) que se usa para controlar los permisos de las entidades de seguridad que son miembros de los grupos de Active Directory con privilegios integrados. Observe que si se realizaron cambios en los permisos predeterminados que pudieran afectar a los usuarios con privilegios administrativos en el dominio, debido a que esos permisos no se aplicarán a los usuarios con cuentas en el entorno bastión.

### Selección de usuarios y grupos para su inclusión

El próximo paso es definir los roles de PAM, mediante la asociación de los usuarios y grupos a los que deberían tener acceso. Normalmente, este será un subconjunto de los usuarios y grupos del nivel identificado como administrado en el entorno bastión. Puede obtener más información en [*Definición de roles para Privileged Access Management*](https://technet.microsoft.com/library/mt620091.aspx).




