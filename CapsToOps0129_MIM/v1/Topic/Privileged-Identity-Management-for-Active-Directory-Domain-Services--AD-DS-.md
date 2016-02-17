---
title: Privileged Identity Management para los Servicios de dominio de Active Directory (AD DS)
ms.custom: 
  - Identity Management
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf3796f7-bc68-4cf7-b887-c5b14e855297
---
# Privileged Identity Management para los Servicios de dominio de Active Directory (AD DS)
Privileged Identity Management (PIM) es una solución basada en Microsoft Identity Manager (MIM), Windows Server 2012 R2 y Windows Server Technical Preview. Ayuda a las organizaciones a restringir el acceso con privilegios en un entorno de Active Directory existente.

NOTA: La funcionalidad de Active Directory local de PIM se denomina Privileged Access Manager (PAM).

El proceso para configurar PIM incluye la creación de un nuevo bosque bastión de Active Directory. El bosque bastión tiene una relación de confianza con el bosque existente. Establece un entorno en perfecto estado que se sabe que está libre de artefactos originados por usuarios malintencionados o por el robo de credenciales con privilegios, lo que permite establecer una base para recobrar el control en el caso de las organizaciones cuyo entorno de Active Directory podría estar en peligro. También restringe el uso de cuentas con privilegios y reduce el riesgo de que roben dichas credenciales, ya que no se necesitan para tareas no administrativas.

Como resultado de este diseño, PIM no requiere ningún cambio en las aplicaciones existentes o en los usuarios del entorno de Active Directory. No es necesario actualizar los servidores o elevar los niveles funcionales de dominio o bosque en el entorno para empezar a usar PIM.

## ¿Qué problemas soluciona PIM?
Una preocupación real de las empresas de hoy en día es la incertidumbre en lo que respecta al acceso a los recursos en un entorno de Active Directory. Resultan especialmente preocupantes las noticias relativas a las vulnerabilidades, las elevaciones de privilegios no autorizadas y otros tipos de acceso no autorizado, como los ataques pass-the-hash, los ataques pass-the-ticket, la suplantación de identidad (phishing) de objetivos específicos y la pérdida de confidencialidad de Kerberos. Todos estos posibles ataques son un problema para las empresas.

¿Es posible que el entorno de Active Directory corra peligro? Si no es así, ¿cuánto tiempo puede tardar un atacante en localizar y poner en peligro una cuenta de administrador de dominio? Después de que los atacantes consigan tener acceso, ¿qué puede detenerlos? ¿Cuánto tiempo pueden pasar ocultos en la red después de obtener dicho acceso? ¿Cuánto tiempo puede estar en peligro el entorno antes de que se detecte el riesgo? Los atacantes pueden dejar puertas traseras (es decir, crear un método que les permita volver a acceder sin usar los procedimientos normales), filtrar datos y vulnerar la seguridad de otras maneras.

El objetivo de PIM es cambiar los períodos de tiempo durante los que se pueden aprovechar estas vulnerabilidades. Hoy en día, es muy fácil que los atacantes obtengan las credenciales de las cuentas de administradores de dominio, y es muy difícil detectar estos ataques después de que se produzcan. Junto con otras mejoras, PIM hará que a los atacantes les resulte más difícil penetrar una red y obtener acceso a cuentas con privilegios. PIM agrega protección a los grupos con privilegios que controlan el acceso a una serie de equipos unidos a un dominio y a las aplicaciones de dichos equipos. También agrega mayores supervisión y visibilidad, así como controles más precisos, para que las organizaciones puedan ver quiénes son sus administradores con privilegios y qué están haciendo. PIM permite a las organizaciones comprender mejor cómo se usan las cuentas administrativas en el entorno.

## ¿Cómo se configura PIM?
PIM se basa en el principio de la administración Just-In-Time, que funciona en combinación con las características relacionadas de [Just Enough Administration (JEA)](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2014/DCIM-B362). JEA es un kit de herramientas de Windows PowerShell que define un conjunto de comandos para realizar actividades con privilegios y un extremo donde los administradores pueden obtener autorización para ejecutar dichos comandos. Si JEA permite una tarea determinada a los usuarios con un privilegio determinado, un usuario puede solicitar el privilegio y, a continuación, realizar la tarea durante un período de tiempo limitado. Un administrador puede especificar cuánto durará dicho período de tiempo y, una vez transcurrido, ya no se podrá usar la cuenta con privilegios. Las características Just-in-Time y Just Enough Administration de PIM pueden implementarse a la vez o por separado.

La configuración y el funcionamiento de PIM constan de cuatro pasos.

![](../Image/MIM_PIM_SetupProcess.png)

1.  **Preparación**: identifique los grupos del bosque existente que tengan privilegios importantes. Como parte de la configuración de PIM, se quitará a los miembros de estos grupos del bosque actual y se crearán los grupos sin miembros en el bosque bastión.

2.  **Protección**: configure el ciclo de vida y la protección de la autenticación, como Multi-Factor Authentication (MFA), para cuando los usuarios soliciten administración Just-In-Time. MFA ayuda a evitar ataques programáticos por parte de software malintencionado o el robo subsiguiente de credenciales.

3.  **Funcionamiento**: una vez que se cumplen los requisitos de autenticación y se aprueba una solicitud, se agrega una cuenta de usuario a un grupo con privilegios del bosque bastión. Por ejemplo, un administrador de Microsoft SharePoint puede solicitar privilegios. Dicha solicitud puede requerir MFA para que pueda aprobarse. Una vez que el administrador de SharePoint se autentique por teléfono, se agregará la cuenta del administrador a un grupo con privilegios del bosque bastión durante un período de tiempo especificado, como, por ejemplo, de 4 horas. Durante ese tiempo, el administrador tiene todos los privilegios y permisos de acceso que están asignados a ese grupo. Después de 4 horas, la cuenta se quita del grupo.

4.  **Supervisión**: PIM agrega auditoría, alertas e informes de las solicitudes de acceso con privilegios. Puede consultar en todo momento el historial de acceso con privilegios y ver quién llevó a cabo tal actividad. Puede saber si la actividad es válida o no e identificar fácilmente actividades no autorizadas, como un intento de agregar un usuario directamente a un grupo con privilegios del bosque original. Este paso es importante no solo para identificar el software malintencionado, sino para llevar un seguimiento de los ataques desde dentro de la organización.

## ¿Cómo funciona PIM?
PIM está basado en las capacidades nuevas de AD DS, especialmente en el caso de la autenticación y la autorización de cuentas de dominio, y en otras nuevas de MIM. PIM ofrece un modo de separar las cuentas con privilegios de un entorno de Active Directory existente. Cuando es necesario usar una cuenta con privilegios, primero hay que solicitarlo y aprobarlo. Tras la aprobación, la cuenta con privilegios recibe permiso a través de un grupo de entidades de seguridad externas en un nuevo bosque bastión, en lugar de en el bosque actual del usuario o la aplicación. El uso de un bosque bastión ofrece a la organización un mayor control, por ejemplo, en lo relativo a cuándo un usuario puede pertenecer a un grupo con privilegios y cómo debe autenticarse dicho usuario.

Active Directory, el servicio de MIM y otros componentes de esta solución también pueden implementarse en una configuración de alta disponibilidad.

En el ejemplo siguiente se muestra con más detalle el funcionamiento de PIM.

![](../Image/MIM_PIM_howitworks.png)

Este patrón de acceso administrativo permite al bosque bastión emitir pertenencias a grupos con un límite de tiempo, que a su vez producen TGT con límite de tiempo que las aplicaciones o servicios existentes basados en Kerberos pueden respetar y aplicar, incluidas las aplicaciones y los servicios de otros bosques que tengan una relación de confianza con el bosque bastión.

No es necesario mover las cuentas de uso diario de los usuarios a un nuevo bosque que opere en un nivel funcional específico. Pueden permanecer en el bosque independientemente de su nivel funcional. Lo mismo pasa con los equipos, las aplicaciones y los grupos. Pueden permanecer en el lugar del bosque donde se encuentren actualmente. Tampoco es necesario actualizarlos. Un ejemplo sería el caso de una organización preocupada por los problemas de ciberseguridad de hoy en día, pero que no tiene planes inmediatos para actualizar la infraestructura de servidores a la próxima versión de Windows Server. Dicha organización puede aprovechar igualmente esta solución combinada si usa MIM y un nuevo bosque bastión para poder controlar mejor el acceso a los recursos.

PIM ofrece las siguientes ventajas:

-   **Aislamiento y ámbito de los privilegios**: los usuarios no tienen privilegios en las cuentas que realizan tareas que no requieren acceso con privilegios. Por ejemplo, si tienen cuentas que usan para actividades diarias, como comprobar el correo electrónico o explorar la red, dichas cuentas no tendrán privilegios de administrador. Los usuarios deben solicitar los privilegios pertinentes. Las solicitudes se aprobarán o se denegarán en función de las directivas de MIM que defina un administrador de PIM. Mientras no se apruebe una solicitud, el acceso con privilegios no estará disponible.

-   **Actualización a una edición superior y pruebas**: se trata de nuevos desafíos de autenticación y autorización que ayudan a administrar el ciclo de vida de las cuentas administrativas independientes. El usuario puede solicitar la elevación de una cuenta administrativa. A continuación, dicha solicitud pasará por los flujos de trabajo de MIM.

-   **Inicio de sesión adicional**: además de los flujos de trabajo integrados de MIM, hay un inicio de sesión adicional para PIM que identifica la solicitud, cómo se autorizó y los eventos que se producen tras la aprobación.

-   **Flujo de trabajo personalizable**: es posible configurar los flujos de trabajo de MIM para diferentes escenarios, y pueden usarse varios flujos de trabajo según los parámetros del usuario que realiza la solicitud o de las funciones solicitadas.

## ¿De qué otra forma pueden los usuarios solicitar acceso con privilegios?
Un usuario puede enviar una solicitud de varias maneras: mediante las opciones tradicionales, como la API de servicios web de los servicios MIM, y con las interfaces nuevas, por ejemplo, a través de un extremo REST y Windows PowerShell (**New-PAMRequest**), lo que facilita a los usuarios la creación de solicitudes nuevas.

## ¿Qué flujos de trabajo y opciones de supervisión están disponibles?
Por poner un ejemplo, supongamos que un usuario pertenecía a un grupo administrativo antes de que se configurase PIM. Como parte de la configuración de PIM, el usuario se quitó del grupo administrativo y se creó una directiva en MIM. La directiva especifica que, si ese usuario solicita privilegios administrativos y se autentica mediante MFA, la solicitud se aprueba y se agrega una cuenta independiente para el usuario en el grupo con privilegios del bosque bastión.

Suponiendo que la solicitud se apruebe, el flujo de trabajo de acción se comunica directamente con el bosque bastión de Active Directory para incluir a un usuario en un grupo. Por ejemplo, cuando Jen solicita administrar la base de datos de recursos humanos, la cuenta administrativa de Jen se agrega al grupo con privilegios del bosque bastión en cuestión de segundos. La pertenencia de Jen a la cuenta administrativa de ese grupo expirará transcurrido un límite de tiempo, como una hora, un día o una semana, o lo que corresponda a dicha solicitud. Con Windows Server Technical Preview, esta pertenencia está asociada en Active Directory a un límite de tiempo; con Windows Server 2012 R2 en el bosque bastión, ese límite de tiempo se aplica mediante MIM.

> [!NOTE]
> Cuando se agrega un nuevo miembro a un grupo, el cambio debe replicarse en otros controladores de dominio del bosque bastión. La latencia de replicación puede afectar a la capacidad de los usuarios para acceder a los recursos. Para obtener información acerca de la latencia de replicación, consulte [Funcionamiento de la topología de replicación de Active Directory](https://technet.microsoft.com/library/cc755994%28v=ws.10%29.aspx).
> 
> En cambio, los vínculos que expiran los evalúa en tiempo real el Administrador de cuentas de seguridad (SAM). Esto significa que, aunque la adición de un miembro del grupo es un cambio que debe replicar el controlador de dominio que recibe la solicitud de acceso, no es necesario replicar la eliminación de un miembro del grupo. Se evalúa de forma instantánea en cualquier controlador de dominio.

Este flujo de trabajo está pensado específicamente para estas cuentas administrativas. Los administradores (o incluso los scripts) que solo necesitan un acceso ocasional para grupos con privilegios pueden solicitar el acceso. MIM registra la solicitud y los cambios en Active Directory y, si lo desea, puede verlos en el Visor de eventos. Es muy fácil enviar la salida de este sistema a soluciones de supervisión empresarial, como System Center 2012: Servicios de recopilación de auditorías (ACS) de Operations Manager u otras herramientas de terceros.

Una vez completados los flujos de trabajo, los usuarios pueden comprobar que sus cuentas del bosque bastión se encuentren en los mismos grupos a los que pertenecían originalmente sus cuentas de bosque existentes (“Corp” en el diagrama anterior), como si en ningún momento hubieran dejado de pertenecer a ellos. A continuación, pueden usar su cuenta del bosque bastión para acceder a las aplicaciones del bosque. Los derechos de acceso desaparecerán automáticamente cuando expire el vale, y también expirarán las pertenencias a los grupos, salvo en el caso de que se renueven.

