---
title: Paso 2: Preparar el controlador del dominio PRIV
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
ms.assetid: 10eb5639-56e0-4208-8f71-58b549ca706e
robots: noindex,nofollow
---
# Paso 2: Preparar el controlador del dominio PRIV
En este paso creará un nuevo dominio para un nuevo bosque de administración de acceso con privilegios.

1.  En otra máquina virtual nueva sin software instalado, instale Windows Server 2012 R2 para convertir un equipo en "*PRIVDC*".

    1.  Seleccione la opción de instalación personalizada (y no la de actualización) de Windows Server.

    2.  Al realizar la instalación, especifique **Windows Server 2012 R2 Standard (servidor con una GUI) x64**; no seleccione Data Center ni Server Core.

        ![](../Image/PAM_GS_Select_WS2012.png)

    3.  Revise los términos de licencia y acéptelos.

    4.  Puesto que el disco estará vacío, seleccione **Personalizada: instalar solo Windows** y use el espacio de disco que no se ha inicializado.

2.  Después de instalar la versión del sistema operativo, inicie sesión en este nuevo equipo como el nuevo administrador.  Use el Panel de control para establecer el nombre del equipo en "*PRIVDC*", asígnele una dirección IP estática de la red virtual y configure el servidor DNS para que sea el del controlador de dominio instalado en el paso anterior.  Esto requerirá el reinicio del servidor.

3.  Una vez que se haya reiniciado el servidor, inicie sesión como el administrador. Mediante el Panel de control, configure el equipo para que compruebe si hay actualizaciones y para que instale todas las actualizaciones necesarias.  Esto podría precisar el reinicio del servidor.

4.  Agregue los roles **Servicios de dominio de Active Directory** (AD DS) y **Servidor DNS** y promueva el servidor a un controlador de dominio de un nuevo bosque.

    1.  Con la sesión iniciada como Administrador, inicie PowerShell.

    2.  Escriba los siguientes comandos:

        ```
        import-module ServerManager Install-WindowsFeature AD-Domain-Services,DNS –restart                            –IncludeAllSubFeature -IncludeManagementTools $ca= get-credential Install-ADDSForest –DomainMode 6 –ForestMode 6 –DomainName priv.contoso.local –DomainNetbiosName priv –Force –CreateDNSDelegation –DNSDelegationCredential $ca
        ```
        Cuando aparezca la ventana emergente, proporcione las credenciales de administrador del bosque CORP (p. ej., el nombre de usuario CONTOSO\Administrador y la contraseña correspondiente especificada en el paso 1).  Después se le pedirá dentro de la ventana de PowerShell una Contraseña de administrador de modo seguro: escriba una contraseña nueva dos veces.  Tenga en cuenta que aparecerán mensajes de advertencia de delegación de DNS y configuración de criptografía. Estos mensajes son normales.

    3.  Cuando se haya terminado de crear el bosque, el servidor se reiniciará automáticamente.

5.  Cree las cuentas de usuario y servicio, que serán necesarias durante la instalación del Servicio MIM y el Portal de MIM, en el contenedor **Usuarios** del *dominio priv.contoso.local*.

    1.  Después del reinicio, inicie sesión en *PRIVDC* como administrador del dominio (*PRIV\Administrador*).

    2.  Escriba el siguiente comando para actualizar el controlador de dominio a partir de la configuración de directiva de grupo.

        ```
        import-module activedirectory $sp = ConvertTo-SecureString "Pass@word1" –asplaintext –force New-ADUser –SamAccountName MIMMA –name MIMMA Set-ADAccountPassword –identity MIMMA –NewPassword $sp Set-ADUser –identity MIMMA –Enabled 1 –PasswordNeverExpires 1 New-ADUser –SamAccountName MIMMonitor –name MIMMonitor -DisplayName MIMMonitor Set-ADAccountPassword –identity MIMMonitor –NewPassword $sp Set-ADUser –identity MIMMonitor –Enabled 1 –PasswordNeverExpires 1 New-ADUser –SamAccountName MIMComponent –name MIMComponent -DisplayName MIMComponent Set-ADAccountPassword –identity MIMComponent –NewPassword $sp Set-ADUser –identity MIMComponent –Enabled 1 –PasswordNeverExpires 1 New-ADUser –SamAccountName MIMSync –name MIMSync Set-ADAccountPassword –identity MIMSync –NewPassword $sp Set-ADUser –identity MIMSync –Enabled 1 –PasswordNeverExpires 1 New-ADUser –SamAccountName MIMService –name MIMService Set-ADAccountPassword –identity MIMService –NewPassword $sp Set-ADUser –identity MIMService –Enabled 1 –PasswordNeverExpires 1 New-ADUser –SamAccountName SharePoint –name SharePoint Set-ADAccountPassword –identity SharePoint –NewPassword $sp Set-ADUser –identity SharePoint –Enabled 1 –PasswordNeverExpires 1 New-ADUser –SamAccountName SqlServer –name SqlServer Set-ADAccountPassword –identity SqlServer –NewPassword $sp Set-ADUser –identity SqlServer –Enabled 1 –PasswordNeverExpires 1 New-ADUser –SamAccountName BackupAdmin –name BackupAdmin Set-ADAccountPassword –identity BackupAdmin –NewPassword $sp Set-ADUser –identity BackupAdmin –Enabled 1 -PasswordNeverExpires 1 Add-ADGroupMember "Domain Admins" SharePoint Add-ADGroupMember "Domain Admins" MIMService
        ```

6.  Configure los derechos de auditoría e inicio de sesión.

    1.  Asegúrese de que haya iniciado sesión como administrador del dominio (como, por ejemplo, *PRIV\Administrador*).

    2.  Vaya a **Inicio » Herramientas administrativas » Administración de directivas de grupo**.

    3.  Vaya a **Bosque**:*priv.contoso.local, Dominios, priv.contoso.local, Controladores de dominio, Directiva predeterminada de controladores de dominio* . Tenga en cuenta que aparecerá un mensaje de advertencia.

    4.  Haga clic con el botón derecho en **Directiva predeterminada de controladores de dominio** y seleccione **Editar** en el menú contextual.

    5.  En el árbol de la consola **Editor de administración de directivas de grupo** vaya a *Configuración del equipo, Directivas, Configuración de Windows, Configuración de seguridad, Directivas locales, Directiva de auditoría*.

    6.  En el **panel de detalles** haga clic con el botón derecho en **Auditar la administración de cuentas** y seleccione **Propiedades** en el menú contextual. Haga clic en **Definir esta configuración de directiva**, seleccione Correcto, seleccione **Error**, y haga clic en **Aplicar** y en **Aceptar**.

    7.  En el **panel de detalles** haga clic con el botón derecho en **Auditar el acceso del servicio de directorio** y seleccione **Propiedades** en el menú contextual. Haga clic en **Definir esta configuración de directiva** coloque una casilla en **Correcto**, otra casilla en **Error** y haga clic en **Aplicar** y en **Aceptar**.

    8.  Cierre la ventana **Editor de administración de directivas de grupo**.

    9. En la ventana **Administración de directivas de grupo**, seleccione **Directiva predeterminada de dominio**, haga clic con el botón derecho y seleccione **Editar**. Se mostrará la ventana **Editor de administración de directivas de grupo**.

    10. Expanda *Configuración del equipo, Directivas, Configuración de Windows, Configuración de seguridad, Directivas locales* y seleccione **Asignación de derechos de usuario**.

    11. En el **panel de detalles** haga clic con el botón derecho en **Denegar el inicio de sesión como trabajo por lotes** y seleccione **Propiedades**.

    12. Haga clic en la casilla **Definir esta configuración de directiva**, haga clic en **Agregar usuario o grupo** y en **Nombres de usuario y grupo** escriba *priv\mimmonitor; priv\MIMService; priv\mimcomponent* y haga clic en **Aceptar**.

    13. Haga clic en **Aceptar** para cerrar la ventana Propiedades de Denegar el inicio de sesión como trabajo por lotes.

    14. En el **panel de detalles** haga clic con el botón derecho en **Denegar inicio de sesión a través de Servicios de Escritorio remoto** y seleccione **Propiedades**.

    15. Haga clic en la casilla **Definir esta configuración de directiva**, haga clic en **Agregar usuario o grupo** y en **Nombres de usuario y grupo** escriba *priv\mimmonitor; priv\MIMService; priv\mimcomponent* y haga clic en **Aceptar**.

    16. Haga clic en **Aceptar** para cerrar la ventana Propiedades de Denegar inicio de sesión a través de Servicios de Escritorio remoto.

    17. Cierre las ventanas **Editor de administración de directivas de grupo** y **Administración de directivas de grupo**.

7.  Inicie una ventana de PowerShell como administrador y escriba el siguiente comando para actualizar el controlador de dominio a partir de la configuración de directiva de grupo.

    ```
    gpupdate /force /target:computer
    ```
    Transcurrido un minuto, se completará y se mostrará el mensaje "La actualización de la directiva de equipo se completó correctamente".

8.  Configure los valores del registro necesarios para migrar el historial de SID. Inicie PowerShell y escriba los siguientes comandos que configurarán el dominio de origen para permitir el acceso de llamada a procedimiento remoto (RPC) a la base de datos del administrador de cuentas de seguridad (SAM).

    ```
    New-ItemProperty –Path HKLM:SYSTEM\CurrentControlSet\Control\Lsa –Name TcpipClientSupport –PropertyType DWORD –Value 1
    ```

9. Mediante PowerShell en *PRIVDC* configure el reenvío de nombres DNS.  Especifique *contoso.local* para el dominio DNS y la dirección IP de red virtual del equipo *CORPDC* como una dirección IP del servidor maestro. Inicie PowerShell y escriba el siguiente comando, cambiando la dirección IP de "10.1.1.31" por la dirección IP de red virtual del equipo *CORPDC*.

    ```
    Add-DnsServerConditionalForwarderZone –name "contoso.local" –masterservers 10.1.1.31
    ```

10. Mediante PowerShell, agregue SPN para que SharePoint, la API de REST de PAM y el Servicio MIM puedan usar la autenticación Kerberos (SharePoint se configurará en el paso 3 que se muestra debajo).

    ```
    setspn -S http/pamsrv.priv.contoso.local PRIV\SharePoint setspn -S http/pamsrv PRIV\SharePoint setspn -S FIMService/pamsrv.priv.contoso.local PRIV\MIMService
    ```

11. Configure la delegación.

    1.  Inicie **Usuarios y equipos de Active Directory**.

    2.  Haga clic con el botón derecho en el **dominio priv.contoso.local** y seleccione **Control delegado**.

    3.  En la pestaña **Usuarios y grupos seleccionados** haga clic en **Agregar**.

    4.  En la ventana emergente **Cuadro de diálogo Seleccionar usuarios, equipos o grupos**, escriba *mimcomponent; mimmonitor* y haga clic en **Comprobar nombres**.  Una vez que se hayan subrayado los nombres, haga clic en **Aceptar** y después en **Siguiente**.

    5.  En la lista de tareas comunes, seleccione "**Crear, eliminar y administrar cuentas de usuario**" y "**Modificar la pertenencia de un grupo**" y después haga clic en **Siguiente** y en **Finalizar**.

    6.  Cierre **Usuarios y equipos de Active Directory**.

12. Reinicie el servidor PRIVDC para que se apliquen los cambios.

