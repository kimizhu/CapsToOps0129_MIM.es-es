---
title: Configurar la caracter&#237;stica de autoservicio de restablecimiento de contrase&#241;a y desbloqueo de cuenta
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
ms.assetid: c1ae1413-724c-491b-8dd8-18997f2a481a
robots: noindex,nofollow
---
# Configurar la caracter&#237;stica de autoservicio de restablecimiento de contrase&#241;a y desbloqueo de cuenta
MIM le permite ahora habilitar la autenticación multifactor (MFA) para el restablecimiento de las contraseñas de usuario.Esto significa que, si un usuario restablece su contraseña justo antes de marcharse de vacaciones y no recuerda cuál era al regresar, solo necesita su teléfono móvil para volver a la actividad casi al instante.

La puerta de autenticación recientemente añadida al autoservicio de restablecimiento de contraseña (SSPR) será muy bien recibida por los usuarios que siempre olvidan la contraseña y por sus administradores.MIM simplifica mucho la tarea de restablecer la contraseña, ya que los usuarios no tienen que llamar al departamento de soporte técnico ni recordar las respuestas para la puerta de preguntas y respuestas (algo que podía ser tan complicado como recordar la contraseña original).

Con la nueva puerta MFA, la autenticación puede depender de contestar el teléfono y, opcionalmente, haga clic en un código PIN.En este tema se proporciona instrucciones para configurarla y ponerla en marcha.

## Poner en funcionamiento la puerta MFA
Como ocurre con todas las puertas de MIM SSPR, el programa de instalación de la puerta MFA es muy simple e supone unos pocos pasos que se explican aquí.

> [!NOTE]
> Si no trabaja con Windows Azure, puede usar aplicaciones y directorios personalizados para configurar el proveedor de MFA y también puede utilizar la puerta MFA con aplicaciones locales mediante un servidor de autenticación multifactor, pero este tema solo proporciona instrucciones para trabajar con Azure Active Directory.

#### Configurar la puerta MFA

1.  En IDWeb, haga clic en **Flujos de trabajo** en el panel izquierdo.

    ![](../Image/MIM_SSPR_workflow.jpg)

2.  Seleccione **Flujo de trabajo de autenticación de restablecimiento de contraseña**.

    ![](../Image/MIM_SSPR_PwdResetAuthNworkflow.jpg)

3.  Haga clic en la pestaña **Actividades** y desplácese hacia abajo hasta **Agregar actividad**.

4.  Seleccione **Puerta MFA**, haga clic en **Seleccionar** y, a continuación, en **Aceptar**.

#### Registrar el proveedor de autenticación multifactor en Azure

1.  Configure el proveedor MFA en Microsoft Azure Active Directory.Al hacerlo, se genera un archivo con unas claves que debe actualizar en el archivo de configuración de MIM para proporciona información de MFA.

    Inicie sesión en el portal de Azure con sus credenciales.

2.  En la esquina inferior izquierda, haga clic en **Nuevo**.

3.  Haga clic en **Servicios de aplicaciones &gt; Active Directory &gt; Proveedor de autenticación multifactor &gt; Creación rápida**.

4.  En el campo **Nombre**, introduzca **SSPRMFA** y haga clic en **Crear**.

    ![](../Image/MIM_SSPR_Azureportal.png)

5.  Haga clic en **Active Directory** en el menú del portal de Azure y, a continuación, haga clic en la pestaña **Proveedores de autenticación multifactor**.

6.  Haga clic en **SSPRMFA** y, a continuación, haga clic en **Administrar**, en la parte inferior de la pantalla.

    ![](../Image/MIM_SSPR_ManageButton.png)

7.  En la ventana **Azure Multi-Factor Authentication** que aparece, haga clic en **SDK**, bajo **Descargas** en el menú de la izquierda.

8.  Haga clic en **Descargar** para el **SDK para ASP.net 2.0 C#**.

    ![](../Image/MIM_SSPR_Azure_MFA.png)

9. Guarde y abra el archivo zip.

#### Actualizar el archivo de configuración

1.  En el archivo zip del SDK, abra el archivo **pf_auth.cs** de la carpeta \pf.

2.  Busque estos tres parámetros: `LICENSE_KEY, GROUP_KEY, CERT_PASSWORD`.

    ![](../Image/MIM_SSPR_pFile.png)

3.  En **C:\Archivos de programa\Microsoft Forefront Identity Manager\2010\Service**, abra este archivo: **MfaSettings**.xml.

4.  Copie los valores de los parámetros `LICENSE_KEY, GROUP_KEY, CERT_PASSWORD` del archivo pf_aut.cs en los elementos xml correspondientes del archivo MfaSettings.xml.

5.  En el archivo zip del SDK, bajo \pf\certs, extraiga el archivo **cert_key.p12** y escriba la ruta de acceso completa en el archivo MfaSettings.xml del elemento xml `<CertFilePath>`.

6.  En el elemento `<username>`, escriba cualquier nombre de usuario.

7.  Guarde el archivo MfaSettings.xml con el mismo nombre y en la misma ubicación.

#### Hacer que los usuarios introduzcan números de teléfono

1.  A continuación, haga que los usuarios introduzcan su número de teléfono para que el sistema sepa cómo llamarlos.

    Deben visitar el portal de registro de contraseñas y autenticarse con su nombre de usuario y contraseña.

2.  En el campo **Número de teléfono**, deben escribir un código de país, un espacio y el número de teléfono, y hacer clic en **Siguiente**.

    ![](../Image/MIM_SSPR_PhoneVerification.JPG)

## Ahora que está en marcha, ¿cómo funciona?
Ahora que está todo configurado y funcionando, querrá saber lo que tienen que hacer los usuarios si restablecen la contraseña justo antes de las vacaciones y descubren a su vuelta que han olvidado la contraseña por completo.

#### Cómo restablece la contraseña un usuario

1.  El usuario entra en el portal de autoservicio de restablecimiento de contraseña, escribe su nombre de usuario y hace clic en **Siguiente**.

    ![](../Image/MIM_SSPR_PR1.JPG)

2.  En segundo plano, lo que sucede es que Azure MFA llama por teléfono al número que proporcionó el usuario al registrarse en junio, cuando esas fabulosas vacaciones en Hawái eran solo una posibilidad remota en un futuro lejano.

3.  Cuando el usuario responde al teléfono, se le pide que presione la tecla almohadilla # en el teléfono.A continuación, el usuario hace clic en **Siguiente** en el portal.

    ![](../Image/MIM_SSPR_PR2.jpg)

    Si configura también otras puertas, se pedirá al usuario que proporcione más información en las pantallas siguientes.

    > [!NOTE]
    > Si el usuario se impacienta y hace clic en **Siguiente** antes de presionar la tecla almohadilla #, se produce un error de autenticación.

4.  Después, el usuario debe escribir la contraseña nueva dos veces y se restablece la contraseña.

