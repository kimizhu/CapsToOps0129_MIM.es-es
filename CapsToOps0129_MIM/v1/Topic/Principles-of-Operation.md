---
title: Principios de funcionamiento
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
ms.assetid: 6932f732-286b-4c89-a302-84fab819dbc9
---
# Principios de funcionamiento
La solución para la externalización de las cuentas administrativas está compuesta por bosques paralelos.   En esta guía hay dos bosques:

-   **"CORP"**: un bosque corporativo de uso general que incluye uno o varios dominios.   Las organizaciones pueden tener varios bosques "CORP", sin embargo, con el fin de simplificar, en esta guía del laboratorio de pruebas se supone que solo existe un bosque con un único dominio.

-   **"PRIV"**: un bosque dedicado para la administración de cuentas con privilegios, creado especialmente para este escenario de PAM. Este bosque incluye un dominio. Este dominio acomodará cuentas y grupos con privilegios que son duplicados a partir de uno o varios dominios CORP.

El controlador de dominio de Active Directory del bosque "PRIV" proporciona autorización y autenticación de usuario con privilegios.  Además, MIM exige el acceso a través de miembros de tiempo limitado de cuentas de usuario en grupos de seguridad y grupos de entidades de seguridad externas.  Tenga en cuenta que en las versiones de Windows Server a las que se hace referencia en esta Guía del laboratorio de pruebas, los grupos de entidades de seguridad externas todavía no están disponibles. Estos se proporcionarán en futuras actualizaciones de esta Guía para la próxima versión de Windows Server.

Microsoft Identity Manager agrega nuevas actividades de flujo de trabajo y recursos relacionados para las solicitudes de elevación "justo a tiempo" de privilegios de acceso, que se envían directamente al controlador de dominio de Active Directory del bosque "PRIV".  También proporciona nuevos cmdlets de PowerShell para las solicitudes de elevación.

La solución MIM tal como está configurada para PAM incluye los siguientes componentes:

-   **Servicio MIM**: implementa la lógica de negocios para realizar operaciones de administración de identidades y acceso, incluyendo la administración de cuentas con privilegios y de solicitudes de elevación.

-   **Portal de MIM**: portal basado en SharePoint, hospedado por SharePoint 2013, que proporciona una interfaz de usuario para la configuración y la administración de administradores.

-   **Base de datos del Servicio MIM**: almacenada en SQL Server 2012 o 2014, almacena metadatos y datos de identidad necesarios para el Servicio MIM.

-   **Servicio de supervisión de PAM y Servicio de componente de PAM**: dos servicios que administran el ciclo de vida de las cuentas con privilegios y ayudan a PRIV AD en lo relativo al ciclo de vida de pertenencia a grupos.

-   **Cmdlets de PowerShell**: para rellenar el Servicio MIM y PRIV AD con usuarios y grupos correspondientes a usuarios y grupos del bosque CORP para administradores de PAM y para usuarios finales que soliciten el uso de privilegios "justo a tiempo" (JIT) en una cuenta administrativa.

-   **API de REST de PAM y portal de ejemplo**: para los desarrolladores que integren MIM en el escenario de PAM con clientes personalizados para realizar operaciones de elevación sin necesidad de usar PowerShell o SOAP. El uso de la API de REST se demuestra con una aplicación web de ejemplo.

Una vez que se haya instalado y configurado, cada grupo creado mediante el procedimiento de migración en el bosque PRIV es un grupo de seguridad basada en SIDHistory duplicado (o en una actualización posterior con Windows Server vNext, un grupo de entidades de seguridad externas) que refleja el SID de un grupo en el bosque CORP original. Además, cuando el Servicio MIM agrega miembros a estos grupos en el bosque PRIV, esas pertenencias serán de tiempo limitado.

Como resultado, cuando un usuario solicita la elevación mediante los cmdlets de PowerShell y se aprueba su solicitud, el Servicio MIM agregará su cuenta del bosque PRIV a un grupo del bosque PRIV.  Cuando el usuario inicia sesión con su cuenta con privilegios, su token de Kerberos contendrá un identificador de seguridad (SID) idéntico al SID del grupo del bosque CORP.  Puesto que el bosque CORP está configurado para confiar en el bosque PRIV, se muestra la cuenta con privilegios elevados que se usa para acceder a un recurso en el bosque CORP, para que un recurso que comprueba las pertenencias al grupo Kerberos sea miembro de los grupos de seguridad de ese recurso.  Esto se proporciona a través de la autenticación entre bosques de Kerberos.

Además, estas pertenencias son de tiempo limitado para que después de un intervalo preconfigurado de tiempo, la cuenta administrativa del usuario deje de formar parte del grupo en el bosque PRIV.  Como resultado, dicha cuenta ya no se podrá usar para acceder a otros recursos.

Por ejemplo, suponga que el bosque CORP CONTOSO contiene un grupo "CONTOSO\CorpAdmins" con un miembro "CONTOSO\Jen".  Hay un recurso confidencial, como puede ser un recurso compartido de archivos, cuya lista de control de acceso hace referencia a ese grupo.  Dado que Jen es miembro de ese grupo, cuando Jen intenta acceder al recurso compartido de archivos, puede hacerlo.

Después de instalar y configurar MIM, se crea un nuevo usuario en el bosque PRIV: PRIV.Jen.  Esta cuenta de usuario no tendrá ningún privilegio de forma predeterminada.  Además, se creará un nuevo grupo en el bosque PRIV: PRIV\CONTOSO.CorpAdmins.  Ese grupo no tendrá ningún miembro de forma predeterminada.  Además, ese grupo PRIV\CONTOSO.CorpAdmins tiene el mismo SID que CONTOSO\CorpAdmins.

En este momento, CONTOSO\Jen puede quitarse (manualmente) del grupo CONTOSO\CorpAdmins.  Si Jen solicita acceso desde MIM y obtiene la autorización, el Servicio MIM agrega PRIV.Jen a PRIV\CONTOSO.CorpAdmins.  A partir de ese momento Jen puede acceder con su nueva cuenta PRIV.Jen a recursos como el recurso compartido de archivos.  Más adelante, la pertenencia de esa cuenta a PRIV\CONTOSO.CorpAdmins finalizará automáticamente. Si Jen sigue necesitando acceso, deberá volver a solicitar la elevación.

