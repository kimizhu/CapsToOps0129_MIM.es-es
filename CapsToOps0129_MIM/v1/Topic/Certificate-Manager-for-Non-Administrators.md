---
title: Administrador de certificados para usuarios no administradores
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
ms.assetid: bfabc562-a2f0-4cff-ac31-36927f41e102
---
# Administrador de certificados para usuarios no administradores
Si un usuario no es un administrador local en su equipo, no podrá inscribir una tarjeta inteligente en sus propios equipos de forma predeterminada.El siguiente procedimiento permite evitar esta limitación.

## Habilitar renovación de tarjetas inteligentes para usuarios que no son administradores en el Administrador de certificados de MIM 2016

1.  **Desempaquetar el archivo appx**

    Obtenga un certificado de firma.Puede seguir [aquí](http://blogs.technet.com/b/deploymentguys/archive/2013/06/14/signing-windows-8-applications-using-an-internal-pki.aspx) los pasos para crear uno mediante AD CS.Deténgase cuando llegue a "Firmar la aplicación".Dé nombre al archivo pfx exportado.Exporte también a un archivo .cer e impórtelo al cliente utilizando el archivo .cer del certificado de firma nuevo.

    Ejecute lo siguiente para desempaquetar el archivo appx:

    `makeappx unpack /l /p <app package name>.appx /d ./appx`

    `ren <app package name>.appx <app package name>.appx.old`

    `cd appx`

2.  **Modificar el archivo de configuración**

    Cambie el nombre del archivo llamado `CustomDataExample.xml custom.data`.CM buscará el nombre de este archivo.

    Edite el archivo custom.data y modifique lo siguiente:

    1.  En el elemento &lt;NonAdmin&gt;, cambie el valor del atributo Valor a "True"

    2.  Guarde el archivo y salga del editor

    3.  Elimine el archivo denominado AppxSignature.p7x

    4.  Edite el archivo denominado AppxManifest.xml

    5.  En el elemento &lt;Identity&gt;, modifique el valor del atributo Publicador para que sea el Firmante que aparece en el certificado de firma, como, por ejemplo, "CN = ABCD"

        El firmante aquí debe ser el mismo que el del certificado de firma que se utiliza para firmar la aplicación.

    6.  Guarde el archivo y salga del editor.

3.  **Volver a empaquetar y firmar el paquete de aplicación (archivo appx)**

    Ejecute lo siguiente para empaquetar y firmar el archivo appx:

    `cd ..`

    `makeappx pack /l /d .\appx /p <app package name>.appx`

    s`igntool sign /f <path\>mysign.pfx /p <pfx password> /fd "sha256" <app package name>.appx`

4.  Duplique la plantilla de perfil y agregue la clave de administración inicial para configurar el servidor MIM:

    1.  Inicie sesión en el portal de CM como usuario con privilegios administrativos.

    2.  Vaya a **Administración** &gt; **Administrar plantillas de perfil** y asegúrese de que esté marcada la casilla situada junto a la plantilla del perfil que creó; después, haga clic en Copiar una plantilla de perfil seleccionada.

    3.  Escriba el nombre de la plantilla de perfil, agregue "nonAdmin" y haga clic en **Aceptar**.

    4.  Cuando aparezca la configuración general de la plantilla de perfil, desplácese completamente hacia abajo y, en **Configuración de tarjeta inteligente**, haga clic en **Cambiar configuración**.

    5.  En **Valor inicial de clave de administración (hexadecimal)**, escriba la clave de administración predeterminada: "010203040506070801020304050607080102030405060708"

    6.  Desplácese hacia abajo y haga clic en **Aceptar**.

5.  **Crear una cuenta sin derechos administrativos en el equipo cliente**

    Los usuarios sin privilegios de administrador no pueden crear la tarjeta inteligente virtual en el TPM, por lo que es necesario creársela.

6.  **Crear una tarjeta inteligente virtual mediante TpmVscMgr**

    Realice lo siguiente (todavía como administrador) para crear una tarjeta inteligente virtual vacía en un equipo.Puede hacerlo mediante Intune, SCCM o directivas de grupo.

    `TpmVscMgr create /name MyVSC /pin default /adminkey default /generate`

7.  **Instale la aplicación CM en la cuenta sin derechos administrativos**

8.  **Inicie la aplicación CM e inscriba una tarjeta inteligente virtual**

