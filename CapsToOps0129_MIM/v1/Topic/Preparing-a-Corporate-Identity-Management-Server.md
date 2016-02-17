---
title: Preparaci&#243;n de un servidor de administraci&#243;n de identidades corporativo
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
ms.assetid: a79eec00-022f-48d5-88e0-2743fe8af85d
---
# Preparaci&#243;n de un servidor de administraci&#243;n de identidades corporativo

## Implementar y configurar Windows Server 2012 R2

1.  Cree una máquina de Windows Server 2012 R2 con un mínimo de 8 GB de RAM.Al instalar, especifique la edición "Windows Server 2012 R2 Standard (servidor con una GUI) x64".

2.  Inicie sesión en el nuevo equipo como su administrador.

3.  Mediante el Panel de control, asígnele una dirección IP estática en la red, configure esa interfaz de red para que envíe consultas DNS a la dirección IP del controlador de dominio del paso anterior y establezca el nombre del equipo como CORPIDM.Esto requerirá el reinicio del servidor.

4.  Si el equipo está en una red virtual que no proporciona conectividad a Internet, agregue una interfaz de red adicional al equipo que proporciona conexión a Internet.Esto será necesario para instalar SharePoint y se podrá deshabilitar cuando se complete este paso.

5.  Abra el Panel de control y únalo al mismo dominio que acaba de configurar (*contoso.local*).Para ello, deberá proporcionar el nombre de usuario y las credenciales de un administrador del dominio, como *Contoso\Administrador*.Cuando aparezca el mensaje de bienvenida, cierre el cuadro de diálogo y vuelva a reiniciar este servidor.

6.  Inicie sesión en el equipo *CorpIDM* con credenciales de administrador del dominio, como *Contoso\Administrador*.

7.  Inicie una ventana de PowerShell como administrador y escriba el siguiente comando para actualizar el equipo según la configuración de directiva de grupo.`gpupdate /force /target:computer`

    Antes de un minuto, se completará y se mostrará el mensaje "La actualización de la directiva de equipo se completó correctamente".

8.  Agregue los roles **Servidor Web (IIS)** y **Servidor de aplicaciones**, las características de  **.NET Framework** 3.5, 4.0 y 4.5, y el módulo de **Active Directory** para Windows PowerShell.

    ![](../Image/MIM_DeployWS2.png)

9. Ejecute **Windows PowerShell** como administrador.

    Escriba los siguientes comandos:Tenga en cuenta que puede que sea necesario especificar una ubicación diferente para los archivos de origen de las características de **.NET Framework** 3.5.Estas características normalmente no están presentes cuando se instala Windows Server, pero están disponibles en la carpeta en paralelo (SxS) en la carpeta de orígenes de disco de instalación del sistema operativo, p. ej., "*d:\Sources\SxS\*".

    ```
    import-module ServerManager
    Install-WindowsFeature Web-WebServer, Net-Framework-Features,rsat-ad-powershell,Web-Mgmt-Tools,Application-Server,Windows-Identity-Foundation,Server-Media-Foundation,Xps-Viewer –includeallsubfeature -restart -source d:\sources\SxS
    ```

10. Configure la directiva de seguridad de servidor para que permita que las cuentas recién creadas se ejecuten como servicios.

    -   Inicie el programa Directiva de seguridad local.

    -   Vaya a **Directivas locales, Asignación de derechos de usuario**.

    -   En el panel de detalles haga clic con el botón secundario en **Iniciar sesión como servicio** y seleccione **Propiedades**.

    -   Haga clic en **Agregar usuario o grupo** y, en **Nombres de usuario y grupo**, escriba `contoso\mimsync; contoso\mimma; contoso\MIMService; contoso\SharePoint; contoso\SqlServer; contoso\mimsspr`, haga clic en **Comprobar nombres** y haga clic en **Aceptar**.

    -   Haga clic en **Aceptar** para cerrar la ventana Propiedades de Iniciar sesión como servicio.

    -   En el panel de detalles, haga clic con el botón secundario en **Denegar el acceso desde la red a este equipo** y seleccione Propiedades.

    -   Haga clic en **Agregar usuario o grupo** y, en Nombres de usuario y grupo, escriba contoso\MIMSync; contoso\MIMService y haga clic en Aceptar.

    -   Haga clic en **Aceptar** para cerrar la ventana Propiedades de Denegar el acceso desde la red a este equipo.

    -   En el panel de detalles, haga clic con el botón secundario en **Denegar el inicio de sesión localmente** y seleccione Propiedades.

    -   Haga clic en **Agregar usuario o grupo** y, en Nombres de usuario y grupo, escriba `ontoso\MIMSync; contoso\MIMService` y haga clic en Aceptar.

    -   Haga clic en **Aceptar** para cerrar la ventana Propiedades de Denegar el inicio de sesión localmente.

    -   Cierre la ventana Directiva de seguridad local.

11. Cambie el **modo autenticación de Windows IIS**.

    1.  Abra una ventana de PowerShell.

    2.  Detenga IIS mediante el comando *iisreset /STOP*.

        ```
        iisreset /STOP
        C:\Windows\System32\inetsrv\appcmd.exe unlock config /section:windowsAuthentication -commit:apphost
        iisreset /START
        ```

## Implementar SQL Server
Instale **Microsoft SQL Server 2014 Standard Edition**.

-   Inicie **PowerShell** como administrador de dominio.

-   Cambie al directorio donde se encuentra el programa de instalación de SQL Server.

-   Escriba los siguientes comandos:

    ```
    .\setup.exe /Q /IACCEPTSQLSERVERLICENSETERMS /ACTION=install /FEATURES=SQL,SSMS /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="contoso\SqlServer" /SQLSVCPASSWORD="Pass@word1"   /AGTSVCSTARTUPTYPE=Automatic /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /SQLSYSADMINACCOUNTS="contoso\Administrator"
    ```

## Implementar SharePoint

1.  Instale **SharePoint Foundation 2013 con SP1**.

    > [!NOTE]
    > Requiere conectividad a Internet para que el programa de instalación descargue los requisitos previos.

    El servidor se reiniciará al final de la instalación.

2.  Inicie **PowerShell** como administrador de dominio.

    -   Cambie al directorio donde se desempaquetó SharePoint.

    -   Escriba el siguiente comando:

        ```
        .\prerequisiteinstaller.exe
        ```

3.  Una vez instalados los requisitos previos de **SharePoint**, escriba el siguiente comando para instalar **SharePoint Foundation 2013 con SP1**:

    ```
    .\setup.exe
    ```

4.  Seleccione el tipo de servidor completo.

5.  Cuando finalice la instalación, ejecute el asistente.

6.  Ejecute el **Asistente para configuración de Productos de SharePoint** para configurar SharePoint.

    -   En la pestaña **Conectar a una granja de servidores**, cambie para crear una nueva granja de servidores.

    -   Especifique este servidor como servidor de base de datos para la base de datos de configuración y *contoso\SharePoint* como la cuenta de acceso a la base de datos que usará SharePoint.

    -   Especifique una contraseña como la frase de contraseña de seguridad de la granja de servidores (no se usará más adelante en este entorno de laboratorio).

    -   Cuando el Asistente para la configuración complete la tarea de configuración 10 de 10, haga clic en Finalizar y se abrirá un explorador web.

    -   En la ventana emergente de Internet Explorer, autentíquese como *contoso\Administrador* (o la cuenta de administrador de dominio equivalente) para continuar.

    -   Inicie el asistente (dentro de la aplicación web) para configurar la granja de SharePoint.

    -   Seleccione la opción de usar la cuenta administrada existente (*Contoso\SharePoint*) y haga clic en **Siguiente**.

    -   En la ventana de **creación de colección de sitios**, haga clic en **Omitir**.A continuación, haga clic en **Finalizar**.

7.  Cuando se completen los asistentes, use **PowerShell** para crear una **aplicación web de SharePoint Foundation 2013** que hospede el **portal de MIM**.

    > [!NOTE]
    > Inicialmente, no se configurará SSL.Asegúrese de configurar SSL o un equivalente antes de habilitar el acceso a este portal.

    1.  Inicie el **Shell de administración de SharePoint 2013** y ejecute el siguiente script de PowerShell:

        ```
        $dbManagedAccount = Get-SPManagedAccount -Identity contoso\SharePoint
        New-SpWebApplication -Name "MIM Portal" -ApplicationPool "MIMAppPool"
          -ApplicationPoolAccount $dbManagedAccount -AuthenticationMethod "Kerberos" -Port 82 -URL http://corpidm.contoso.local
        ```

    2.  Aparecerá un mensaje de advertencia que indicará que se está usando el método de autenticación clásico de Windows y el comando final puede tardar varios minutos en responder.Cuando se complete, el resultado indicará la dirección URL del nuevo portal.Mantenga abierta la ventana del **Shell de administración de SharePoint 2013**, ya que se necesitará en una tarea posterior.

8.  Cree una **Colección de sitios de SharePoint** asociada a esa aplicación web para hospedar el **portal de MIM**.

    1.  Inicie el Shell de administración de SharePoint 2013 y ejecute el siguiente script de PowerShell:

        ```
        $t = Get-SPWebTemplate -compatibilityLevel 14 -Identity "STS#1"
        $w = Get-SPWebApplication http://corpidm.domain.local:82 
        New-SPSite -Url $w.Url -Template $t -OwnerAlias contoso\Administrator 
         -CompatibilityLevel 14 -Name "MIM Portal" -SecondaryOwnerAlias contoso\BackupAdmin 
        $s = SpSite($w.Url)
        $s.AllowSelfServiceUpgrade = $false
        $s.CompatibilityLevel
        ```

    2.  Compruebe que el resultado de la variable *CompatibilityLevel* es "14".(Para obtener más información, [vea http://technet.microsoft.com/library/jj863242(v=ws.10).aspx](http://technet.microsoft.com/library/jj863242%28v=ws.10%29.aspx)).Si el resultado es "15", la colección de sitios no se creó para la versión de la experiencia 2010. Elimine la colección de sitios y vuelva a crearla.

9. Deshabilite el **estado de vista de lado servidor** y la tarea "Trabajo de análisis de mantenimiento (Cada hora, Temporizador de Microsoft SharePoint Foundation, Todos los servidores" ejecutando los siguientes comandos de PowerShell en el **Shell de administración de SharePoint 2013**:

    ```
    $contentService = [Microsoft.SharePoint.Administration.SPWebService]::ContentService;
    $contentService.ViewStateOnServer = $false;
    $contentService.Update();
    Get-SPTimerJob hourly-all-sptimerservice-health-analysis-job | disable-SPTimerJob
    ```

10. En el servidor de administración de identidades, abra una nueva pestaña del explorador web, vaya a **http://localhost:82/** e inicie sesión como *contoso\Administrador*.Se mostrará un sitio de SharePoint vacío denominado *Portal de MIM*.

    ![](../Image/MIM_DeploySP1.png)

11. Copie la dirección URL y, en **Internet Explorer** abra **Opciones de Internet**, cambie a la **pestaña Seguridad**, seleccione **Intranet local**, haga clic en **Sitios** y, a continuación, haga clic en **Avanzadas** y agregue a la lista la dirección URL copiada.Haga clic en **Aceptar** dos veces.

    ![](../Image/MIM_DeploySP2.png)

12. Abra **Administrativo**, **Herramientas** y **Servicios**, busque el servicio Administración de SharePoint e inícielo, si aún no se está ejecutando.

## Opcional: Implementar Microsoft Exchange Server
Si desea configurar MIM para enviar y recibir correo electrónico o aprovisionar buzones, es necesario tener Exchange presente en el entorno.Si no tiene Exchange implementado, puede instalar una versión de prueba con fines de evaluación.

-   Descargue e instale Microsoft Office 2010 Filter Packs versión 2.0 y Microsoft Office 2010 Filter Packs versión 2.0 SP1.

    -   [MS Office10 FP2.0](http://www.microsoft.com/en-us/download/details.aspx?id=17062)

    -   [MS Office10 FP2.0 SP1](http://www.microsoft.com/en-us/download/details.aspx?id=26604)

-   Descargue e instale [Microsoft Unified Communications Managed API 4.0, Core Runtime de 64 bits](http://www.microsoft.com/en-us/download/details.aspx?id=34992).

-   Descargue e instale la [versión de prueba de 180 días de MS Exchange Server 2013](http://www.microsoft.com/en-us/evalcenter/evaluate-exchange-server-2013).

