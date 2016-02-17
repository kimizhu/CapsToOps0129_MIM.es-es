---
title: Paso 4: Instalar componentes de MIM en un servidor y estaci&#243;n de trabajo PAM
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4152564d-2166-4e57-9ca5-cad39a568ba3
---
# Paso 4: Instalar componentes de MIM en un servidor y estaci&#243;n de trabajo PAM
## Instalación del servicio y portal de MIM y una aplicación web de ejemplo

1. En PAMSRV, inicie sesión como PRIV\MIMAdmin para poder instalar el servicio y portal de MIM y la aplicación web de ejemplo del portal. **Nota**: Debe ser un administrador de dominio; si no está ejecutando los comandos siguientes como administrador de dominio, las comprobaciones de validación de confianza del paso siguiente no se completarán.

2. Si ha descargado MIM, descomprima el archivo de instalación de MIM en una carpeta nueva.

### Instalación del servicio y el portal

Ejecute el programa de instalación del **servicio y portal**. Siga las instrucciones del instalador y complete la instalación:

1. Al seleccionar las características de componentes, es necesario incluir lo siguiente:

-  Servicio MIM (incluida la administración de acceso con privilegios, sin incluir informes MIM)

-  Portal MIM

2. Al configurar los servicios comunes y la conexión a la base de datos de MIM, especifique "Crear una nueva base de datos".

3. Al configurar una conexión de servidor de correo electrónico, establezca el servidor de correo electrónico *"corpdc.contoso.local"* y desactive las casillas **"Usar SSL"** y **"El servidor de correo electrónico es Exchange Server 2007 o Exchange Server 2010"**.

4. Cambie la configuración para **generar un nuevo certificado autofirmado**.

5. Especifique el nombre de la cuenta de servicio como *"MIMService"* y la **contraseña de la cuenta de servicio** como *"Pass@word1"*, el **dominio de la cuenta de servicio** como *"PRIV"* y la **cuenta de servicio de correo electrónico** como *"MIMService@priv.contoso.local"*.

6. Acepte los valores predeterminados para el nombre de host del servidor de sincronización y especifique la **cuenta del agente de administración de MIM** como *"PRIV\\mimma"*. **Nota**: Aparecerá un mensaje advirtiendo de que el servicio de sincronización de MIM no existe. Esto es correcto, ya que el servicio de sincronización de MIM no se utiliza en este escenario de TLG.

7. Especifique *"pamsrv"* como la **dirección del servidor del servicio MIM**.

8. Especifique *"http://pamsrv.priv.contoso.local:82"* como la **dirección URL de la colección de sitios de SharePoint**.

9. Deje en blanco la **dirección URL del portal de registro**.

10. Seleccione la casilla para **Abrir los puertos 5725 y 5726 en el firewall** y la casilla para **conceder a todos los usuarios autenticados** acceso al sitio del portal de MIM.

11. Deje el vacío el campo **Nombre de host de API de REST de PAM** y especifique *8086* como el número de puerto.

12. Configure la **cuenta de la API de REST de MIM PAM** de forma que utilice la misma cuenta que SharePoint (ya que el portal de MIM está ubicado en este "SharePoint"), la **contraseña de cuenta de grupo de aplicaciones** como *"Pass@word1"* y el **dominio de cuenta del grupo de aplicaciones** como *"PRIV"*. **Nota**: Puede aparecer una advertencia que indique que la cuenta de servicio no es segura en su configuración actual.

13. Configure el **servicio de componente MIM PAM**. Especifique el **nombre de la cuenta** como *"mimcomponent"*, la **contraseña de la cuenta de servicio** como *"Pass@word1"* y el **dominio de la cuenta de servicio** como *"PRIV"*.

14. Configure el **servicio de supervisión de PAM**. Especifique el nombre de la cuenta como *"mimmonitor"*, la **contraseña de la cuenta de servicio** como *"Pass@word1"* y el dominio de la cuenta de servicio como "PRIV".

15. En la página **Escribir la información para el portal de contraseñas de MIM**, deje las casillas sin seleccionar y continúe. Luego, haga clic en **Siguiente** para continuar con la instalación.

### Comprobación de que el portal de PIM está activo

Una vez que se finalice la instalación y se reinicie el servidor, compruebe que el portal de MIM está activo y permita que los usuarios vean su propio recurso de objeto en MIM.

1. Una vez que se reinicie PAMSRV, inicie sesión como *PRIV\\MIMAdmin*.

2. Inicie **Internet Explorer** y establezca una conexión con el portal de MIM en *"http://pamsrv.priv.contoso.local:82/identitymanagement"*. **Nota**: Puede haber una breve demora la primera vez que se busca esta página.

4. Si fuese necesario, autentíquese como *PRIV\\MIMAdmin* en **Internet Explorer**.

5. En **Internet Explorer**, abra **Opciones de Internet**, cambie a la pestaña **Seguridad** y agregue el sitio a la zona **Intranet local** si todavía no está en ella. Cierre el cuadro de diálogo **Opciones de Internet**.

6. Use **Internet Explorer** para ver el portal de MIM y haga clic en **Reglas de directiva de administración**.

7. Busque la regla de directivas de administración **Administración de usuarios: Los usuarios pueden leer atributos por sí mismos**.

8. Seleccione esta regla de directiva de administración, desactive la opción **La directiva está deshabilitada**, haga clic en **Aceptar** y, luego, haga clic en **Enviar**.

### Comprobación de las conexiones entrantes del firewall

Compruebe que el firewall permite las conexiones entrantes para los puertos TCP 5725, 5726, 8086 y 8090.

1. Inicie **Firewall de Windows con seguridad avanzada** (ubicado en Herramientas administrativas).

2. Haga clic en **Reglas de entrada**.

3. Compruebe que aparecen las dos reglas **Servicio Forefront Identity Manager (STS)** y **Servicio Forefront Identity Manager Service (Servicio web)**.

4. Haga clic en **Nueva regla**, seleccione **Puerto**, seleccione **TCP** y escriba los puertos locales específicos *8086, 8090*. Haga clic en el asistente y acepte los valores predeterminados, asigne un nombre a la regla y haga clic en **Finalizar**.

5. Después de completar el asistente cierre la aplicación **Windows Firewall**.

6. Inicie el **Panel de Control**.

7. Haga clic en **Ver estado de la red y las tareas**, que se encuentra en **Red e Internet**.

8. Compruebe que se muestre una red activa con el nombre *"priv.contoso.local"* como *"Red de dominios"*.

9. Cierre el **Panel de control**.

### Descarga de la aplicación web de ejemplo

Desde el archivo de aplicación web de ejemplo (descargue el archivo desde aquí), desempaquete el contenido de la carpeta *identity-management-samples-master\\Privileged-Access-Management-Portal\\src* en una nueva carpeta *Privileged Access Management Portal* dentro de la carpeta *C:\\Archivos de programa\\Microsoft Forefront Identity Manager\\2010*.

### Instalación y configuración de la aplicación web de ejemplo

Instale y configure la aplicación web de ejemplo para la API de REST de MIM PAM.

1. Cree un sitio web en IIS con el nombre de sitio *"Portal de ejemplo de MIM Privileged Access Management"*, la ruta de acceso física *"C:\\Archivos de programa\\Microsoft Forefront Identity Manager\\2010\\Privileged Access Management Portal"* y el puerto *8090*. Puede hacerlo mediante el siguiente comando de PowerShell:

`New-WebSite -Name "MIM Privileged Access Management Example Portal" -Port 8090 -PhysicalPath "C:\\Program Files\\Microsoft Forefront Identity Manager\\2010\\Privileged Access Management Portal\\"`

2. Permita que la aplicación web redirija a los usuarios a la API de REST de MIM PAM. Con un editor de texto como **Bloc de notas**, edite el archivo *"C:\\Archivos de programa\\Microsoft Forefront Identity Manager\\2010\\Privileged Access Management REST API\\web.config"*. En la sección **\<system.webServer\>**, agregue las siguientes líneas:


```
    <httpProtocol>
        <customHeaders>
         <add name="Access-Control-Allow-Credentials" value="true" />
         <add name="Access-Control-Allow-Headers" value="content-type" />
         <add name="Access-Control-Allow-Origin" value="http://pamsrv:8090" />
        </customHeaders>
     </httpProtocol>
```

3. Configure la aplicación web de ejemplo. Con un editor de texto como Bloc de notas, edite el archivo *"C:\\Archivos de programa\\Microsoft Forefront Identity Manager\\2010\\Privileged Access Management REST API\\js\\utils.js"*. En ese archivo, establezca el valor de **pamRespApiUrl** en *"http://pamsrv.priv.contoso.local:8086/api/pamresources/"*.

4.  Reinicie IIS para que estos cambios surtan efecto.

`iisreset`

5.  (Opcional) Compruebe que el usuario puede autenticarse con la API de REST. Abra un explorador web como administrador en *pamsrv*. Vaya a la dirección URL de sitio web *http://pamsrv.priv.contoso.local:8086/api/pamresources/pamroles/*. Autentíquese (si es necesario) y asegúrese de que se produzca una descarga.

### Instalación de los cmdlets de solicitante de MIM PAM

Instale los cmdlets de solicitante de MIM PAM en la estación de trabajo.

1. Inicie sesión en *CORPWKSTN* como administrador de dominio *PRIV\\Administrador*.

2. Descargue los **complementos y extensiones** en el equipo *CORPWKSTN*, si todavía no están presentes.

3. Desempaquete del archivo la carpeta **Complementos y extensiones** en una nueva carpeta.

4. Ejecute el instalador *setup.exe*.

5. En la instalación personalizada, especifique el **cliente de PAM** que se va a instalar, pero **no** el **complemento MIM para Outlook** ni las extensiones de **contraseña y autenticación de MIM**.

6. En la **dirección del servidor PAM**, especifique como nombre de host del servidor *PRIV MIM* **pamsrv.priv.contoso.local**.

7. Una vez finalizada la instalación, reinicie **CORPWKSTN** para completar el registro del nuevo módulo de **PowerShell**.




