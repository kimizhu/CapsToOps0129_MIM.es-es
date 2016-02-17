---
title: Paso 2: Preparar el controlador de dominio PRIV
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e9993a0-b8ae-40e2-8228-040256adb7e2
---
# Paso 2: Preparar el controlador de dominio PRIV
## Creación de un nuevo bosque de administración de acceso con privilegios

En este paso creará un nuevo dominio para un nuevo bosque de administración de acceso con privilegios.

### Instalación de Windows Server 2012 R2

En otra máquina virtual sin software instalado, instale Windows Server 2012 R2 para convertir un equipo en "PRIVDC".

1. Seleccione la opción de instalación personalizada (y no la de actualización) de Windows Server. Cuando realice la instalación, especifique *Windows Server 2012 R2 Standard (servidor con una GUI) x64*; **no** seleccione *Data Center ni Server Core*.

2. Revise los términos de licencia y acéptelos.

3. Como el disco estará vacío, seleccione *Personalizada: Instalar solo Windows* y use el espacio de disco que no se ha inicializado.

4. Después de instalar la versión del sistema operativo, inicie sesión en este nuevo equipo como el nuevo administrador. Use el Panel de control para establecer el nombre del equipo en "PRIVDC", asígnele una dirección IP estática de la red virtual y configure el servidor DNS para que sea el del controlador de dominio instalado en el paso anterior. Esto requerirá el reinicio del servidor.

5. Una vez que se haya reiniciado el servidor, inicie sesión como el administrador. Mediante el Panel de control, configure el equipo para que compruebe si hay actualizaciones y para que instale todas las actualizaciones necesarias. Esto podría precisar el reinicio del servidor.

### Incorporación de roles

Agregue los roles Servicios de dominio de Active Directory (AD DS) y Servidor DNS y promueva el servidor a un controlador de dominio de un nuevo bosque.

**NOTA**: En este documento, el nombre *priv.contoso.local* se utiliza como el nombre de dominio del nuevo bosque. El nombre del bosque no es crítico y no es necesario que esté subordinado a un nombre de bosque existente en la organización. Sin embargo, los nombres de NetBIOS y de dominio del bosque nuevo deben ser únicos y diferentes a los de cualquier otro dominio existente en la organización.

1. Con la sesión iniciada como Administrador, inicie PowerShell.
2. Escriba los siguientes comandos:

`import-module ServerManager`

`Install-WindowsFeature AD-Domain-Services,DNS –restart –IncludeAllSubFeature -IncludeManagementTools`

`$ca= get-credential`

`Install-ADDSForest –DomainMode 6 –ForestMode 6 –DomainName priv.contoso.local –DomainNetbiosName priv –Force –CreateDNSDelegation –DNSDelegationCredential $ca`

3. Cuando aparezca la ventana emergente, proporcione las credenciales de administrador del bosque CORP (p. ej., el nombre de usuario CONTOSO\\Administrador y la contraseña correspondiente especificada en el paso 1). Después se le pedirá dentro de la ventana de PowerShell una Contraseña de administrador de modo seguro: escriba una contraseña nueva dos veces. Tenga en cuenta que aparecerán mensajes de advertencia de delegación de DNS y configuración de criptografía. Estos mensajes son normales.

Cuando se haya terminado de crear el bosque, el servidor se reiniciará automáticamente.

### Creación de cuentas de usuario y servicio

Cree las cuentas de usuario y servicio, que serán necesarias durante la instalación del Servicio MIM y el Portal de MIM, en el contenedor Usuarios del dominio **priv.contoso.local**.

1. Después del reinicio, inicie sesión en PRIVDC como administrador del dominio (PRIV\\Administrador).

2. Escriba los siguientes comandos:

`import-module activedirectory`

`$sp = ConvertTo-SecureString "Pass@word1" –asplaintext –force`

`New-ADUser –SamAccountName MIMMA –name MIMMA`

`Set-ADAccountPassword –identity MIMMA –NewPassword $sp`

`Set-ADUser –identity MIMMA –Enabled 1 –PasswordNeverExpires 1`

`New-ADUser –SamAccountName MIMMonitor –name MIMMonitor -DisplayName MIMMonitor`

`Set-ADAccountPassword –identity MIMMonitor –NewPassword $sp`

`Set-ADUser –identity MIMMonitor –Enabled 1 –PasswordNeverExpires 1`

`New-ADUser –SamAccountName MIMComponent –name MIMComponent -DisplayName MIMComponent`

`Set-ADAccountPassword –identity MIMComponent –NewPassword $sp`

`Set-ADUser –identity MIMComponent –Enabled 1 –PasswordNeverExpires 1`

`New-ADUser –SamAccountName MIMSync –name MIMSync`

`Set-ADAccountPassword –identity MIMSync –NewPassword $sp`

`Set-ADUser –identity MIMSync –Enabled 1 –PasswordNeverExpires 1`

`New-ADUser –SamAccountName MIMService –name MIMService`

`Set-ADAccountPassword –identity MIMService –NewPassword $sp`

`Set-ADUser –identity MIMService –Enabled 1 –PasswordNeverExpires 1`

`New-ADUser –SamAccountName SharePoint –name SharePoint`

`Set-ADAccountPassword –identity SharePoint –NewPassword $sp`

`Set-ADUser –identity SharePoint –Enabled 1 –PasswordNeverExpires 1`

`New-ADUser –SamAccountName SqlServer –name SqlServer`

`Set-ADAccountPassword –identity SqlServer –NewPassword $sp`

`Set-ADUser –identity SqlServer –Enabled 1 –PasswordNeverExpires 1`

`New-ADUser –SamAccountName BackupAdmin –name BackupAdmin`

`Set-ADAccountPassword –identity BackupAdmin –NewPassword $sp`

`Set-ADUser –identity BackupAdmin –Enabled 1 -PasswordNeverExpires 1`

`New-ADUser -SamAccountName MIMAdmin -name MIMAdmin`

`Set-ADAccountPassword –identity MIMAdmin  -NewPassword $sp`

`Set-ADUser -identity MIMAdmin -Enabled 1 -PasswordNeverExpires 1`

`Add-ADGroupMember "Domain Admins" SharePoint`

`Add-ADGroupMember "Domain Admins" MIMService`

### Configuración de los derechos de auditoría e inicio de sesión

1. Asegúrese de que haya iniciado sesión como administrador del dominio (como, por ejemplo, PRIV\\Administrador).

2. Vaya a **Inicio** » **Herramientas administrativas** » **Administración de directivas de grupo**.

3. Vaya a Bosque: *priv.contoso.local* » **Dominios** » *priv.contoso.local* » **Controladores de dominio** » **Directiva predeterminada de controladores de dominio**. Aparecerá un mensaje de advertencia.

4. Haga clic con el botón derecho en **Directiva predeterminada de controladores de dominio** y seleccione **Editar** en el menú.

5. En el árbol de la consola **Editor de administración de directivas de grupo**, vaya a **Configuración del equipo** » **Directivas** » **Configuración de Windows** » **Configuración de seguridad** » **Directivas locales** » **Directiva de auditoría**.

6. En el panel **Detalles**, haga clic con el botón derecho en **Auditar la administración de cuentas** y seleccione **Propiedades** en el menú. Haga clic en **Definir esta configuración de directiva**, marque la casilla **Éxito** y la casilla **Error**, haga clic en **Aplicar** y, luego, en **Aceptar**.

7. En el panel **Detalles**, haga clic con el botón derecho en **Auditar el acceso del servicio de directorio** y seleccione **Propiedades** en el menú. Haga clic en **Definir esta configuración de directiva**, marque la casilla **Éxito** y la casilla **Error**, haga clic en **Aplicar** y, luego, en **Aceptar**.

8. Vaya a **Configuración del equipo** » **Directivas** » **Configuración de Windows** » **Configuración de seguridad** » **Directivas de cuenta** » **Directiva Kerberos**.

9. En el panel **Detalles**, haga clic con el botón derecho en **Vigencia máxima del vale de usuario** y seleccione **Propiedades** en el menú. Haga clic en **Definir esta configuración de directiva**, establezca la cantidad de horas en *1*, haga clic en **Aplicar** y, luego, en **Aceptar**. Tenga en cuenta que las otras definiciones de la ventana también cambiarán.

10. En la ventana **Administración de directivas de grupo**, seleccione **Directiva predeterminada de dominio**, haga clic con el botón derecho y seleccione **Editar**. Se mostrará la ventana **Editor de administración de directivas de grupo**.

11. Expanda **Configuración del equipo** » **Directivas** » **Configuración de Windows** » **Configuración de seguridad** » **Directivas locales** y seleccione **Asignación de derechos de usuario**.

12. En el panel **Detalles**, haga clic con el botón derecho en **Denegar el inicio de sesión como trabajo por lotes** y seleccione **Propiedades**.

13. Marque la casilla **Definir esta configuración de directiva**, haga clic en **Agregar usuario o grupo** y en el campo **Nombres de usuario y grupo**, escriba *priv\\mimmonitor; priv\\MIMService; priv\\mimcomponent* y haga clic en **Aceptar**.

14. Haga clic en **Aceptar** para cerrar la ventana **Denegar el inicio de sesión como trabajo por lotes » Propiedades**.

15. En el panel **Detalles**, haga clic con el botón derecho en **Denegar inicio de sesión a través de Servicios de Escritorio remoto** y seleccione **Propiedades**.

16. Haga clic en la casilla **Definir esta configuración de directiva**, haga clic en **Agregar usuario o grupo** y en el campo **Nombres de usuario y grupo**, escriba *priv\\mimmonitor; priv\\MIMService; priv\\mimcomponent* y haga clic en **Aceptar**.

17. Haga clic en **Aceptar** para cerrar la ventana **Denegar inicio de sesión a través de Servicios de Escritorio remoto » Propiedades**.

18. Cierre las ventanas **Editor de administración de directivas de grupo** y **Administración de directivas de grupo**.

19. Inicie una ventana de PowerShell como administrador y escriba el siguiente comando para actualizar el controlador de dominio a partir de la configuración de directiva de grupo.

`gpupdate /force /target:computer`

Transcurrido un minuto, se completará y se mostrará el mensaje "La actualización de la directiva de equipo se completó correctamente".

### Configure los valores del registro necesarios para migrar el historial de SID.

Inicie PowerShell y escriba los siguientes comandos para configurar el dominio de origen que permitir el acceso de llamada a procedimiento remoto (RPC) a la base de datos del administrador de cuentas de seguridad (SAM).

    `New-ItemProperty –Path HKLM:SYSTEM\\CurrentControlSet\\Control\\Lsa –Name TcpipClientSupport –PropertyType DWORD –Value 1`

### Configuración del reenvío de nombres DNS

Mediante PowerShell en PRIVDC, configure el reenvío de nombres DNS. Especifique *contoso.local* para el dominio DNS y la dirección IP de red virtual del equipo CORPDC como una dirección IP del servidor maestro.

1. Inicie PowerShell y escriba el siguiente comando, cambiando la dirección IP de "10.1.1.31" por la dirección IP de red virtual del equipo CORPDC.

`Add-DnsServerConditionalForwarderZone –name "contoso.local" –masterservers 10.1.1.31`

2. Mediante PowerShell, agregue SPN para que SharePoint, la API de REST de PAM y el Servicio MIM puedan usar la autenticación Kerberos (SharePoint se configurará en el paso 3 que se muestra debajo).

`setspn -S http/pamsrv.priv.contoso.local PRIV\\SharePoint`

`setspn -S http/pamsrv PRIV\\SharePoint`

`setspn -S FIMService/pamsrv.priv.contoso.local PRIV\\MIMService`

`setspn -S FIMService/pamsrv PRIV\MIMService`

**NOTA:** Esta guía describe cómo comenzar a instalar los componentes del servidor MIM 2016 en un solo sistema para fines de prueba. Se requiere una configuración de Kerberos adicional para instalar los componentes del servidor MIM 2016 en varios sistemas para una alta disponibilidad, tal como se describe [aquí](http://social.technet.microsoft.com/wiki/contents/articles/3385.fim-2010-kerberos-authentication-setup.aspx).

### Configure la delegación.

1. Inicie **Usuarios y equipos de Active Directory**.

2. Haga clic con el botón derecho en el dominio *priv.contoso.local* y seleccione **Control delegado**.

3. En la pestaña **Usuarios y grupos seleccionados**, haga clic en **Agregar**.

4. En la ventana **Seleccionar usuarios, equipos o grupos**, escriba *mimcomponent; mimmonitor; mimservice* y haga clic en **Comprobar nombres**. Una vez que se hayan subrayado los nombres, haga clic en **Aceptar** y después en **Siguiente**.

5. En la lista de tareas comunes, seleccione **Crear, eliminar y administrar cuentas de usuario** y **Modificar la pertenencia de un grupo**; luego, haga clic en **Siguiente** y en **Finalizar**.

6. Haga clic con el botón derecho en el *dominio priv.contoso.local* y seleccione **Control delegado**.

7. En la pestaña **Usuarios y grupos seleccionados**, haga clic en **Agregar**.

8. En la ventana emergente **Seleccionar usuarios, equipos o grupos**, escriba *MIMAdmin* y haga clic en **Comprobar nombres**.

9. Una vez que se hayan subrayado los nombres, haga clic en **Aceptar** y después en **Siguiente**.

10. Seleccione **Tarea personalizada**, aplique a **Esta carpeta** con **Permisos generales**.

11. En la lista de permisos, seleccione lo siguiente: **Leer**, **Escribir**, **Crear todos los objetos secundarios**, **Borrar todos los objetos secundarios**, **Leer todas las propiedades**, **Escribir todas las propiedades** y **Migrar historial SID**. Haga clic en **Siguiente** y, luego, en **Finalizar**.

12. Haga clic con el botón derecho en el *dominio priv.contoso.local* y seleccione **Control delegado**.

13. En la pestaña **Usuarios y grupos seleccionados**, haga clic en **Agregar**.

14. En la ventana emergente **Seleccionar usuarios, equipos o grupos**, escriba *MIMAdmin* y, luego, haga clic en **Comprobar nombres**.

15. Una vez que se hayan subrayado los nombres, haga clic en **Aceptar** y después en **Siguiente**.

15. Seleccione **Tarea personalizada**, aplique a **Esta carpeta** y, luego, haga clic en **solo objetos de usuario**.

16. En la lista de permisos, seleccione **Cambiar contraseña** y **Restablecer contraseña**. Luego, haga clic en **Siguiente** y en **Finalizar**.

17. Cierre **Usuarios y equipos de Active Directory**.

16. Reinicie el servidor *PRIVDC* para que se apliquen estos cambios.




