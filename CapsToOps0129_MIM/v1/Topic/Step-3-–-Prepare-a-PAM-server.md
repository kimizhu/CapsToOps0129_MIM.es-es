---
title: Paso 3: Preparar un servidor de PAM
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
ms.assetid: 68ec2145-6faa-485e-b79f-2b0c4ce9eff7
robots: noindex,nofollow
---
# Paso 3: Preparar un servidor de PAM

1.  En una tercera máquina virtual, instale Windows Server 2012 R2, específicamente Windows Server 2012 R2 Standard (servidor con una GUI) x64, para convertir un equipo nuevo en "*PAMSRV*".   Tenga en cuenta que, puesto que se instalarán SQL Server y SharePoint 2013 en este equipo, este debe tener al menos 8 GB de RAM.

    1.  Especifique Windows Server 2012 R2 Standard (servidor con una GUI) x64.

        ![](../Image/PAM_GS_Select_WS2012.png)

    2.  Revise los términos de licencia y acéptelos.

    3.  Como el disco estará vacío, seleccione **Personalizada: instalar solo Windows** y use el espacio de disco que no se ha inicializado.

2.  Inicie sesión en ese nuevo equipo como su administrador.  Mediante el Panel de control, asígnele una dirección IP estática en la red virtual, configure esa interfaz de red para que envíe consultas DNS a la dirección IP de **PRIVDC** y establezca el nombre del equipo en **PAMSRV**.  Esto requerirá el reinicio del servidor.

3.  Si la red virtual no proporciona conectividad a Internet, agregue una interfaz de red adicional al equipo que proporciona una conexión a Internet.  Esto será necesario para instalar SharePoint y se podrá deshabilitar cuando se complete este paso.

4.  Una vez que se haya reiniciado el servidor, inicie sesión como el administrador. Mediante el Panel de control, configure el equipo para que compruebe si hay actualizaciones y para que instale todas las actualizaciones necesarias.  Esto podría precisar el reinicio del servidor.

5.  Una vez que el servidor se haya reiniciado, inicie sesión como Administrador, abra el Panel de control y una **PAMSRV** al dominio **PRIV** (*priv.contoso.local*).  Para ello se deberá proporcionar el nombre de usuario y las credenciales de un administrador del dominio **PRIV**, como *PRIV\Administrador*. Después de que aparezca el mensaje de bienvenida, cierre el cuadro de diálogo y reinicie este servidor.

6.  Encienda el equipo **PAMSRV** e inicie sesión en él como administrador del dominio **PRIV**, como *PRIV\Administrador*.

7.  Agregue los roles Servidor Web (IIS) y Servidor de aplicaciones, las características de .NET Framework 3.5, el módulo de Active Directory para Windows PowerShell y otras características requeridas por SharePoint.

    1.  Con la sesión iniciada como Administrador, inicie PowerShell.

    2.  Escriba los siguientes comandos:   Tenga en cuenta que puede que sea necesario especificar una ubicación diferente para los archivos de origen de las características de .NET Framework 3.5. Estas características normalmente no están presentes cuando se instala Windows Server, pero están disponibles en la carpeta en paralelo (SxS) en la carpeta de orígenes de disco de instalación del sistema operativo, p. ej., "*d:\Sources\SxS\*".

        ```
        import-module ServerManager Install-WindowsFeature Web-WebServer, Net-Framework-Features,rsat-ad-powershell,Web-Mgmt-Tools,Application-Server,Windows-Identity-Foundation,Server-Media-Foundation,Xps-Viewer –includeallsubfeature -restart -source d:\sources\SxS
        ```

8.  Configure la directiva de seguridad de servidor para que permita que las cuentas recién creadas se ejecuten como servicios.

    1.  Inicie el programa **Directiva de seguridad local**.

    2.  Vaya a **Directivas locales » Asignación de derechos de usuario**.

    3.  En el **panel de detalles** haga clic con el botón derecho en **Iniciar sesión como servicio** y seleccione **Propiedades**.

    4.  Haga clic en **Agregar usuario o grupo** y en Nombres de usuario y grupo, escriba *priv\mimmonitor; priv\MIMService; priv\SharePoint; priv\mimcomponent; priv\SqlServer*, haga clic en **Comprobar nombres** y en **Aceptar**.

    5.  Haga clic en **Aceptar** para cerrar la ventana Propiedades de Iniciar sesión como servicio.

    6.  En el **panel de detalles** haga clic con el botón derecho en **Denegar el acceso desde la red a este equipo** y seleccione **Propiedades**.

    7.  Haga clic en **Agregar usuario o grupo** y en Nombres de usuario y grupo, escriba *priv\mimmonitor; priv\MIMService; priv\mimcomponent* y haga clic en **Aceptar**.

    8.  Haga clic en **Aceptar** para cerrar la ventana Propiedades de Denegar el acceso desde la red a este equipo.

    9. En el **panel de detalles** haga clic con el botón derecho en **Denegar el inicio de sesión localmente** y seleccione **Propiedades**.

    10. Haga clic en **Agregar usuario o grupo** y en Nombres de usuario y grupo, escriba *priv\mimmonitor; priv\MIMService; priv\mimcomponent* y haga clic en **Aceptar**.

    11. Haga clic en **Aceptar** para cerrar la ventana Propiedades de Denegar el inicio de sesión localmente.

    12. **Cierre**  la ventana Directiva de seguridad local.

9. Cambie la configuración de IIS para permitir que las aplicaciones usen el modo de autenticación de Windows.

    1.  Abra una ventana de PowerShell

    2.  Detenga IIS y desbloquee la configuración de host de aplicación con estos comandos

        ```
        iisreset /STOP C:\Windows\System32\inetsrv\appcmd.exe unlock config /section:windowsAuthentication -commit:apphost iisreset /START
        ```

    3.  Como alternativa, use un editor de texto como el Bloc de notas para abrir este archivo: C:\Windows\System32\inetsrv\config\applicationHost.config y en la línea 82 de ese archivo, reemplace el valor de etiqueta de *overrideModeDefault*:

        &lt;section name="windowsAuthentication" overrideModeDefault="Deny" /&gt;

        por

        &lt;section name="windowsAuthentication" overrideModeDefault="Allow" /&gt;

        Después, guarde el archivo y reinicie IIS con el comando *iisreset /START*.

10. Instale **SQL Server 2012 Service Pack 1** o una versión posterior o **SQL Server 2014**. En los siguientes pasos se supone que se ha instalado SQL 2014.

    1.  Inicie PowerShell como administrador de dominio.

    2.  Cambie al directorio donde se encuentra el programa de instalación de SQL Server.

    3.  Escriba los siguientes comandos:

        ```
        .\setup.exe /Q /IACCEPTSQLSERVERLICENSETERMS /ACTION=install /FEATURES=SQL,SSMS /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="PRIV\SqlServer" /SQLSVCPASSWORD="Pass@word1"   /AGTSVCSTARTUPTYPE=Automatic /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /SQLSYSADMINACCOUNTS="PRIV\Administrator"
        ```

11. Mediante el **instalador de SharePoint Foundation 2013 con SP1**, instale los requisitos previos de software de SharePoint en *PAMSRV*.  Tenga en cuenta que esto hará que se reinicie el servidor. Además, este equipo deberá disponer de conectividad a Internet para que el programa de instalación pueda descargar los requisitos previos.

    1.  Inicie PowerShell como administrador de dominio.

    2.  Cambie al directorio donde se desempaquetó SharePoint.

    3.  Escriba el siguiente comando:

        ```
        .\prerequisiteinstaller.exe
        ```

12. Una vez que se hayan instalado los requisitos previos de SharePoint, instale **SharePoint Foundation 2013 con SP1**.

    1.  Inicie PowerShell como administrador de dominio.

    2.  Cambie al directorio donde se desempaquetó SharePoint.

    3.  Escriba el siguiente comando:

        ```
        .\setup.exe
        ```

    4.  Seleccione el tipo de servidor completo.

    5.  Una vez completada la instalación, seleccione esta opción para que se ejecute el asistente.

13. Ejecute el **Asistente para configuración de Productos de SharePoint** para configurar SharePoint.

    1.  En la pestaña "Conectar a una granja de servidores", cambie para crear una nueva granja de servidores.

    2.  Especifique **PAMSRV** como el servidor de base de datos de la base de datos de configuración y **PRIV\SharePoint** como la cuenta de acceso de la base de datos que usará SharePoint.

    3.  Especifique una contraseña como la frase de contraseña de seguridad de la granja de servidores (no se usará más adelante en este entorno de laboratorio).

    4.  Para este entorno de laboratorio de pruebas, acepte el resto de la configuración predeterminada del Asistente para la configuración de SharePoint.

    5.  Cuando el Asistente para la configuración complete la tarea de configuración 10 de 10, haga clic en **Finalizar** y se abrirá un explorador web.

    6.  En la ventana emergente de Internet Explorer, autentíquese como **PRIV\Administrador** (o la cuenta de administrador de dominio equivalente) para continuar.

    7.  Inicie el asistente (dentro de la aplicación web) para configurar la granja de SharePoint.

    8.  Seleccione esta opción para usar la cuenta administrada existente (**PRIV\SharePoint**) y haga clic en **Siguiente**.

    9. Una vez que se muestre la ventana de creación de colección de sitios, haga clic en **Omitir**.  A continuación, haga clic en **Finalizar**.

14. Después que se completen los asistentes, use PowerShell para crear una **aplicación web de SharePoint Foundation 2013** para hospedar el Portal de MIM.  Tenga en cuenta que puesto que este es un entorno de laboratorio de pruebas, no se habilitará SSL.

    1.  Inicie el Shell de administración de SharePoint 2013 y ejecute el siguiente script de PowerShell:

        ```
        $dbManagedAccount = Get-SPManagedAccount -Identity PRIV\SharePoint New-SpWebApplication -Name "MIM Portal" -ApplicationPool "MIMAppPool"            -ApplicationPoolAccount $dbManagedAccount -AuthenticationMethod "Kerberos" -Port 82 -URL http://PAMSRV.priv.contoso.local
        ```
        Aparecerá un mensaje de advertencia que indicará que se está usando el método de autenticación clásico de Windows y el comando final puede tardar varios minutos en responder.  Cuando se complete, el resultado indicará la dirección URL del nuevo portal.  Mantenga abierta la ventana del Shell de administración de SharePoint 2013, ya que se necesitará en una tarea posterior.

15. Después, cree una **Colección de sitios de SharePoint** asociada a esa aplicación web para hospedar el Portal de MIM.

    1.  Inicie el **Shell de administración de SharePoint 2013** si no está abierto y ejecute el siguiente script de PowerShell

        ```
        $t = Get-SPWebTemplate -compatibilityLevel 14 -Identity "STS#1" $w = Get-SPWebApplication http://pamsrv.priv.contoso.local:82 New-SPSite -Url $w.Url -Template $t -OwnerAlias PRIV\Administrator                -CompatibilityLevel 14 -Name "MIM Portal" -SecondaryOwnerAlias PRIV\BackupAdmin $s = SpSite($w.Url) $s.AllowSelfServiceUpgrade = $false $s.CompatibilityLevel
        ```
        Compruebe que el resultado de la variable *CompatibilityLevel* es "14".  (Para obtener más información, [vea http://technet.microsoft.com/library/jj863242(v=ws.10).aspx](http://technet.microsoft.com/library/jj863242%28v=ws.10%29.aspx)). Si el resultado es "15", la colección de sitios no se creó para la versión de la experiencia 2010. Elimine la colección de sitios y vuelva a crearla.

    2.  Deshabilite el estado de vista de lado servidor y la tarea "*Trabajo de análisis de mantenimiento (Cada hora, Temporizador de Microsoft SharePoint Foundation, Todos los servidores*" ejecutando los siguientes comandos de PowerShell en el **Shell de administración de SharePoint 2013**:

        ```
        $contentService = [Microsoft.SharePoint.Administration.SPWebService]::ContentService; $contentService.ViewStateOnServer = $false; $contentService.Update(); Get-SPTimerJob hourly-all-sptimerservice-health-analysis-job | disable-SPTimerJob
        ```

16. Abra una nueva pestaña en el explorador web, vaya a *http://pamsrv.priv.contoso.local:82/* e inicie sesión como *PRIV\Administrador*.  Se mostrará un sitio de SharePoint vacío denominado "Portal de MIM". Luego, en Internet Explorer, abra **Opciones de Internet** cambie a la pestaña **Seguridad**, seleccione **Intranet local** y agregue el sitio web. (Tenga en cuenta que si se produce un error al conectarse, puede que sea necesario actualizar los SPN de Kerberos que se crearon en el paso 2).

17. Mediante **Servicios** (que se encuentra en Herramientas administrativas), inicie el servicio **Administración de SharePoint**, si aún no se está ejecutando.

