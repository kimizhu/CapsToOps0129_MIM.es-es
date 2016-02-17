---
title: Actualizaci&#243;n de Forefront Identity Manager 2010 R2 a Microsoft Identity Manager 2016
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
ms.assetid: 9471ccc1-bafe-46ee-b169-1464262380e1
---
# Actualizaci&#243;n de Forefront Identity Manager 2010 R2 a Microsoft Identity Manager 2016
Esta sección describe la actualización de un sistema de prueba FIM 2010 R2 existente a MIM 2016. Los instaladores de la actualización son los mismos que se utilizan para una implementación nueva.

En esta sección se supone que tiene una solución de FIM 2010 R2 implementada en un entorno de prueba. Los servidores ejecutan Windows Server 2012, Windows Server 2012 R2 o Windows Server 2008 R2, que son los sistemas operativos usuales para los servidores de FIM 2010 R2, y todos los requisitos locales y de entorno (SQL Server, Exchange Server, SharePoint Services, etc.) están configurados para FIM 2010 R2.

1.  El servicio de sincronización de MIM (Sync) se instalará y ejecutará primero en un servidor que esté unido al dominio de AD y reemplazará la instancia de Sync de FIM 2010 R2.

2.  A continuación, se instalará el servicio y portal de MIM, con la opción de incluir el portal de registro y el portal de servicio de autoservicio de restablecimiento de contraseña y sin incluir el conjunto de características de administración del acceso con privilegios.

3.  A continuación, se pueden implementar en un equipo cliente independiente complementos y extensiones de MIM 2016, como el cliente integrado de inicio de sesión de Windows para autoservicio de restablecimiento de contraseña.

## Preparación

1.  Realice una copia de la base de datos del servicio FIM, de la base de datos de FIM Sync y de la configuración y el software de FIM Sync y el servicio FIM.

2.  Inicie sesión como Contoso\Administrador en cada uno de los servidores que tengan instalados los componentes de FIM 2010 R2, como *CORPIDM*, por ejemplo. En este ejemplo de implementación, los se necesitan derechos administrativos para actualizar FIM 2010 R2 a **MIM**.

3.  Descargue o desempaquete el software de MIM.

## Actualización del servicio de sincronización de FIM

1.  Inicie sesión como administrador en un servidor en el que esté implementado el servicio de sincronización de FIM 2010 R2 ("Sync").

2.  Asegúrese de realizar una copia de la base de datos antes de iniciar este procedimiento.

3.  Abra la consola **Servicios**, busque el **servicio Sincronización de Forefront Identity Manager** y deténgalo.

    ![](../Image/MIM_UpgFIM1.PNG)

4.  Ejecute el **instalador del servicio de sincronización de MIM**. El programa de instalación detectará la versión de Sync existente y sugerirá una actualización. Haga clic en el botón **Actualizar** para continuar.

5.  Si acepta los términos de licencia, haga clic en **Siguiente** para continuar.

6.  Escriba la contraseña de la cuenta de servicio que utiliza Sync y haga clic en **Siguiente**.

    ![](../Image/MIM_UpgFIM3.png)

7.  Compruebe que los nombres del grupo de seguridad son correctos y haga clic en **Siguiente**.

    ![](../Image/MIM_UpgFIM4.png)

8.  Deje sin cambiar la casilla de las reglas de firewall para las comunicaciones RPC entrantes.

9. El instalador ya está preparado para actualizar Sync de FIM 2010 R2 a MIM. Haga clic en **Actualizar** para iniciar el proceso de actualización.

10. La actualización está en curso. No salga del instalador ni reinicie el equipo mientras la actualización esté en curso.

    ![](../Image/MIM_UpgFIM7.png)

11. Durante la actualización, se muestra una advertencia referente a la actualización de la base de datos de Sync. Se recomienda hacer una copia de seguridad de la base de datos antes de comenzar.

12. Cuando la actualización finalice correctamente, haga clic en **Finalizar**.

    ![](../Image/MIM_UpgSP1.png)

13. Observe que el **servicio de sincronización** se ha reiniciado.

## Instalar el servicio y portal de MIM

1.  Inicie sesión como administrador en un servidor en el que esté implementado el servicio y portal de FIM 2010 R2.

2.  Abra la consola **Servicios**, busque el **servicio Forefront Identity Manager** y deténgalo.

    ![](../Image/MIM_UpgFIM9.PNG)

3.  Ejecute el instalador del servicio y portal de MIM. Haga clic en el botón **Siguiente** para continuar.

    ![](../Image/MIM_UpgSP2.png)

4.  Si acepta los términos de licencia, haga clic en **Siguiente** para continuar.

5.  En la pantalla Programa para la mejora de la experiencia del usuario de MIM, haga clic en **Siguiente** para continuar.

6.  Seleccione las características y componentes de MIM que desea instalar.

    1.  **Servicio MIM:** Esta característica es obligatoria en al menos un servidor y requiere un servidor de base de datos SQL Server, ya sea en una ubicación compartida o en un servidor aparte.

    2.  **Portal MIM:** Esta característica es obligatoria en al menos un servidor y requiere SharePoint 2013 Foundation.

    3.  **Portal de registro de contraseñas de MIM:** Esta característica es necesaria para el autoservicio de restablecimiento de contraseña.

    4.  **Portal de restablecimiento de contraseñas de MIM:** Esta característica es necesaria para restablecer las contraseñas.

        ![](../Image/MIM_UpgSP4.png)

7.  Una vez seleccionados todos los elementos que desea implementar, haga clic en **Siguiente**.

8.  Proporcione los detalles del servidor SQL Server que se utiliza para la base de datos del servicio FIM. Seleccione la opción de volver a usar la base de datos existente y conservar los datos.

9. Haga clic en **Siguiente** para continuar.

10. Si se ha seleccionado la opción de volver a usar la base de datos existente, aparece un aviso para realizar una copia de seguridad de la base de datos.

11. Escriba los detalles del servidor de correo. Si el servidor se encuentra en el servidor actual, escriba "localhost" como dirección del servidor de correo electrónico. Haga clic en **Siguiente** para continuar.

    ![](../Image/MIM_UpgSP6.png)

12. Seleccione un certificado para el servicio que se usará para validar clientes. Debe usar el certificado existente desde el almacén de certificados local que usaba el servicio FIM.

    ![](../Image/MIM_UpgSP7.png)

    1.  Si está seleccionada la opción de un certificado existente, haga clic en el botón **Seleccionar certificado** y seleccione un certificado en la lista de la ventana emergente. Haga clic en **Aceptar** y en **Siguiente**.

        ![](../Image/MIM_UpgSP8.PNG)

13. Configure las credenciales de la cuenta de servicio para el servicio MIM. Tenga en cuenta que la cuenta de servicio no puede ser la misma que utiliza el servicio de sincronización. Debe ser la misma cuenta que utiliza el servicio FIM.

    ![](../Image/MIM_UpgSP9.png)

14. Configure los detalles del servidor de sincronización de MIM según la implementación del servicio MIM que configuró en un paso anterior.

    ![](../Image/MIM_UpgSP10.png)

15. Al instalar el portal de MIM, proporcione la dirección del servidor del servicio MIM. Haga clic en **Siguiente**.

16. Al instalar el portal de MIM, proporcione la dirección URL de la colección de sitios de SharePoint en la que se aloja actualmente el portal de FIM. Haga clic en **Siguiente**.

17. Si va a instalar el portal de registro de contraseñas de MIM, proporcione la dirección URL solicitada para el portal de registro de contraseñas. Haga clic en **Siguiente**.

18. Configure la capacidad de los clientes y usuarios finales para utilizar el portal y el servicio.

    1.  Seleccione si desea **abrir los puertos 5725 y 5726 en el firewall**.

    2.  Seleccione si desea **permitir que los usuarios autenticados tengan acceso al sitio del portal de MIM**.

    3.  Haga clic en **Siguiente**.

19. Si va a instalar el portal de registro de contraseñas de MIM, proporcione los datos y las credenciales de acceso al registro de contraseñas de MIM.

    1.  Proporcione el nombre de la cuenta de servicio (incluido el dominio) y la contraseña para el registro de contraseñas de MIM.

    2.  Proporcione los detalles del host: nombre y puerto (por ejemplo, 8080) del portal de registro de contraseñas.

    3.  Seleccione la opción de **abrir puertos en el firewall**.

    4.  Haga clic en **Siguiente**.

        ![](../Image/MIM_UpgSP15.png)

20. En la siguiente pantalla de configuración del registro de contraseñas de MIM:

    1.  Indique al registro de contraseña de MIM dónde está instalado el servicio MIM; normalmente, en el mismo sistema.

    2.  Determine si pueden acceder a este portal los usuarios de la extranet y los de la intranet o solo los usuarios de la intranet, tal como lo configurara anteriormente para el restablecimiento de contraseñas de FIM.

        ![](../Image/MIM_UpgSP16.png)

21. Si va a instalar el portal de restablecimiento de contraseñas de MIM, proporcione los datos y las credenciales de acceso al restablecimiento de contraseñas de MIM.

    1.  Proporcione el nombre de la cuenta de servicio (incluido el dominio) y la contraseña para el restablecimiento de contraseñas de MIM.

    2.  Proporcione los detalles del host: nombre y puerto (por ejemplo, 8088) del portal de restablecimiento de contraseñas.

    3.  Seleccione la opción de **abrir puertos en el firewall**.

    4.  Haga clic en **Siguiente**.

        ![](../Image/MIM_UpgSP17.png)

22. En la siguiente pantalla de configuración del restablecimiento de contraseñas de MIM:

    1.  Indique al restablecimiento de contraseña de MIM dónde está instalado el servicio MIM.

    2.  Especifique si pueden acceder a este portal los usuarios de la extranet y los de la intranet o solo los usuarios de la intranet.

23. Cuando haya realizado correctamente todas las definiciones de configuración, aparecerá la siguiente pantalla. Haga clic en **Instalar** para comenzar la instalación y actualización del servicio y portal de MIM.

24. La instalación y la actualización del servicio y el portal de MIM están en curso. No cancele el programa de instalación ni reinicie el equipo durante la instalación.

25. Una vez completada la instalación (o actualización) del servicio y portal de MIM, aparecerá la siguiente pantalla. Haga clic en **Finalizar** para completar la instalación y salir del instalador.

26. Observe que el **servicio Forefront Identity Manager** se reinicia.

