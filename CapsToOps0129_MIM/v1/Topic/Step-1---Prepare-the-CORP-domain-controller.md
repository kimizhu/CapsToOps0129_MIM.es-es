---
title: Paso 1: Preparar el controlador del dominio CORP
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
ms.assetid: 995a36ef-28b0-4831-8ac7-353314594c2a
robots: noindex,nofollow
---
# Paso 1: Preparar el controlador del dominio CORP
En este paso, creará un controlador de dominio y una estación de trabajo miembro en un nuevo dominio de un bosque nuevo. Este bosque simulará un bosque existente que contiene recursos que se van a administrar.  El recurso que se va a proteger en este escenario está representado por un recurso compartido de archivos.

1.  Prepare cuatro máquinas virtuales con unidades independientes que estén conectadas entre sí en una red virtual compartida.  Estas máquinas virtuales pueden hospedarse en Windows 8.1, Windows Server 2012 R2 o en otras plataformas de sistema operativo. La unidad donde se almacenarán las imágenes de disco de máquina virtual debe tener un mínimo de 100 GB de espacio libre en disco para contener todas las máquinas virtuales.

2.  En una de las máquinas virtuales, instale Windows Server 2012 R2 para crear un equipo "*CORPDC*".

    1.  Especifique Windows Server 2012 R2 Standard (servidor con una GUI) x64.

        ![](../Image/PAM_GS_Select_WS2012.png)

    2.  Revise los términos de licencia y acéptelos.

    3.  Puesto que el disco estará vacío, seleccione *Personalizada: instalar solo Windows* y use el espacio de disco que no se ha inicializado.

3.  Inicie sesión en ese nuevo equipo como su administrador.  En el Panel de Control, establezca su nombre como *CORPDC* y asígnele una dirección IP estática en la red virtual.  Esto requerirá el reinicio del servidor.

4.  Una vez reiniciado el servidor, inicie sesión como administrador. Mediante el Panel de control, configure el equipo para que compruebe si hay actualizaciones y para que instale todas las actualizaciones necesarias.  Esto podría precisar el reinicio del servidor.

5.  Una vez reiniciado el servidor, inicie sesión como administrador. Mediante PowerShell, agregue los servicios de dominio de Active Directory (AD DS), los roles de servidor DNS y servidor de archivos (parte de la sección Servicios de archivos y almacenamiento) y promueva a este servidor a controlador de dominio de un bosque nuevo llamado "contoso.local", tal como se describe a continuación:

    1.  Con la sesión iniciada como Administrador, inicie PowerShell.

    2.  Escriba los siguientes comandos:

        ```
        import-module ServerManager Add-WindowsFeature AD-Domain-Services,DNS,FS-FileServer –restart  –IncludeAllSubFeature -IncludeManagementTools Install-ADDSForest –DomainMode Win2008R2 –ForestMode Win2008R2 –DomainName contoso.local –DomainNetbiosName contoso –Force -NoDnsOnNetwork
        ```
        Se le solicitará una contraseña para el administrador del modo seguro.  Tenga en cuenta que aparecerán mensajes de advertencia de delegación de DNS y configuración de criptografía.  Estos mensajes son normales.

    3.  Cuando se haya creado el bosque, cierre la sesión y el servidor se reiniciará automáticamente.

6.  Una vez reiniciado el servidor, inicie sesión en *CORPDC* como administrador del dominio, normalmente el usuario *CONTOSO\Administrador*, que tendrá la misma contraseña que especificó al instalar Windows en *CORPDC*.

7.  Cree nuevos usuarios y grupos, incluido un grupo denominado "CorpAdmins", un usuario denominado "Jen", así como un grupo que AD necesita para fines de auditoría. El nombre del grupo debe ser el nombre del dominio NetBIOS, seguido por tres signos de dólar: "*CONTOSO$ $$*".  El ámbito del grupo debe ser "Dominio local" y el tipo de grupo, "Seguridad".  Esto es necesario para que se puedan crear grupos en el bosque PRIV en un paso posterior.

    1.  Inicie PowerShell.

    2.  Escriba los siguientes comandos:

        ```
        import-module activedirectory New-ADGroup –name CorpAdmins –GroupCategory Security –GroupScope Global          –SamAccountName CorpAdmins New-ADUser –SamAccountName Jen –name Jen Add-ADGroupMember –identity CorpAdmins –Members Jen $jp = ConvertTo-SecureString "Pass@word1" –asplaintext –force Set-ADAccountPassword –identity Jen –NewPassword $jp Set-ADUser –identity Jen –Enabled 1 -DisplayName "Jen" New-ADGroup –name 'CONTOSO$$$' –GroupCategory Security –GroupScope DomainLocal   –SamAccountName 'CONTOSO$$$'
        ```

8.  Configure la auditoría.

    1.  Vaya a *Inicio, Herramientas administrativas* e inicie *Administración de directivas de grupo*.

    2.  Vaya a *Bosque: contoso.local, Dominios, contoso.local, Controladores de dominio, Directiva predeterminada de controladores de dominio*. Aparecerá un mensaje informativo.

        ![](../Image/PAM_GS_GroupPolicyManagement.png)

    3.  Haga clic con el botón secundario en *Directiva predeterminada de controladores de dominio* y seleccione **Editar...** en el menú contextual.  Aparecerá una ventana nueva.

    4.  En la ventana *Editor de administración de directivas de grupo*, bajo el árbol *Directiva predeterminada de controladores de dominio*, localice y expanda *Configuración del equipo, Directivas, Configuración de Windows, Configuración de seguridad, Directivas locales, Directiva de auditoría*.

        ![](../Image/PAM_GS_Group_Policy_Management_Editor.png)

    5.  En el panel de detalles haga clic con el botón secundario en **Auditar la administración de cuentas** y seleccione **Propiedades** en el menú contextual. Haga clic en **Definir esta configuración de directiva**, seleccione Correcto, seleccione *Error*, y haga clic en **Aplicar** y en **Aceptar**.

    6.  En el panel de detalles, haga clic con el botón derecho en **Auditar el acceso del servicio de directorio** y seleccione **Propiedades** en el menú contextual. Haga clic en **Definir esta configuración de directiva**, seleccione *Correcto*, seleccione Error y haga clic en **Aplicar** y en **Aceptar**.

        ![](../Image/PAM_GS_Group_Policy_Management_Editor2.png)

9. Cierre las ventanas Editor de administración de directivas de grupo y Administración de directivas de grupo. A continuación, para aplicar la configuración de auditoría, inicie una ventana de PowerShell y escriba:

    ```
    gpupdate /force /target:computer
    ```
    El mensaje “La actualización de la directiva de equipo se completó correctamente.” debe aparecer después de unos minutos.

10. Configure las opciones del registro necesarias para la migración del historial de SID, que se utilizará para la creación del grupo de administración de acceso con privilegios y reinicie el controlador de dominio.

    1.  Inicie PowerShell.

    2.  Escriba los siguientes comandos, que configurarán el dominio de origen para permitir el acceso de llamada a procedimiento remoto (RPC) a la base de datos del administrador de cuentas de seguridad (SAM).

        ```
        New-ItemProperty –Path HKLM:SYSTEM\CurrentControlSet\Control\Lsa –Name TcpipClientSupport –PropertyType DWORD –Value 1 Restart-Computer
        ```
        Esto reiniciará CORPDC.  Para obtener más información sobre esta configuración del registro, consulte: [http://support.microsoft.com/kb/322970](http://support.microsoft.com/kb/322970)

11. En otra máquina virtual nueva sin software instalado, instale Windows 8.1 Enterprise para convertir un equipo en "*COPRWKSTN*".

    1.  Use la configuración rápida durante la instalación.

    2.  Tenga en cuenta que es posible que la instalación no pueda conectarse a Internet. Haga clic en **Crear una cuenta local**.  Especifique otro nombre de usuario; no utilice "Administrador" o "Jen".

12. Mediante el Panel de control, dé a este equipo una dirección IP estática en la red virtual y configure el servidor DNS preferido de la interfaz para que sea el del servidor *CORPDC*.

13. Mediante el Panel de control, una el equipo CORPWKSTN al dominio *contoso.local*.  Será necesario proporcionar credenciales de administrador del dominio Contoso.   Cuando se complete, reinicie el equipo *CORPWKSTN*.

14. Una vez reiniciado el equipo, haga clic en el icono "**Cambiar de usuario**" y, a continuación, en "**Otro usuario**". Asegúrese de que el usuario *CONTOSO\Jen* puede iniciar sesión en *CORPWKSTN*.

15. En *CORPWKSTN*, cree y comparta una carpeta nueva denominada "*CorpFS*" con el grupo "*CorpAdmins*".

    -   En el **menú Inicio**, escriba PowerShell y seleccione **Ejecutar como administrador**.

    -   Cuando se abre la ventana, escriba los siguientes comandos.

        ```
        mkdir c:\corpfs New-SMBShare –Name corpfs –Path c:\corpfs –ChangeAccess CorpAdmins $acl = Get-Acl c:\corpfs $car = New-Object System.Security.AccessControl.FileSystemAccessRule( "CONTOSO\CorpAdmins", "FullControl", "Allow") $acl.SetAccessRule($car) Set-Acl c:\corpfs $acl
        ```

