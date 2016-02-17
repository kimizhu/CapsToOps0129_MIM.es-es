---
title: Implementar el servicio de notificaci&#243;n de cambio de contrase&#241;a de MIM (PCNS) en un controlador de dominio
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
ms.assetid: 97edae12-6f86-4f9f-8620-a95a096e482a
---
# Implementar el servicio de notificaci&#243;n de cambio de contrase&#241;a de MIM (PCNS) en un controlador de dominio

## Instalar PCNS
PCNS es un servicio que se instala en los controladores de dominio y permite que MIM sincronice las contraseñas a otros sistemas, como un servidor de directorio de otro fabricante.Para la sincronización de contraseña, instale PCNS en cada servidor de controlador de dominio.

1.  Inicie sesión como administrador de dominio en un servidor que ejecute en Windows Server con el rol de Servicios de dominio de Active Directory.

2.  Copie la carpeta de instalación del servicio de notificación de cambio de contraseña en el equipo.

3.  Busque el archivo *Password Change Notification Service.msi*, haga clic en él con el botón secundario y cree un acceso directo.

4.  Busque el archivo de acceso directo, haga clic con el botón secundario y abrirá sus **Propiedades**.

5.  En el campo Destino, agregue el prefijo *msiexec.exe /i* antes de la ruta de acceso del archivo msi y el sufijo *SCHEMAONLY=TRUE* después de la ruta del archivo msi.Por ejemplo, si la carpeta de instalación es *C:\PCNS*, el comando tendría este aspecto (todo en una sola línea):

    ```
    msiexec.exe /i "C:\PCNS\x64\Password Change Notification Service.msi" SCHEMAONLY=TRUE
    ```

6.  Guarde los cambios en el archivo de acceso directo.

7.  Ejecute el archivo de acceso directo para iniciar la instalación de PCNS en modo de extensión de esquema.Cuando aparezca la pantalla siguiente, haga clic en **Siguiente**.

8.  Se le notificará que el programa de instalación actualizará ahora el esquema de Active Directory para el servicio de notificación de cambio de contraseña.Haga clic en **Aceptar** para continuar con la actualización del esquema.

9. Cuando se complete el proceso de extensión de esquema y aparezca la siguiente pantalla, haga clic en **Finalizar**.

10. Ejecute el archivo *Password Change Notification Service.msi* de nuevo, esta vez directamente (no se necesita ninguna cadena de ejecución).Cuando aparezca la pantalla siguiente, haga clic en **Siguiente**.

11. Acepte los términos del contrato de licencia y haga clic en **Siguiente**.

12. Haga clic para iniciar la instalación.

13. Cuando aparezca la pantalla de instalación finalizada correctamente, haga clic en **Finalizar**.

14. Reinicie el equipo para que surtan efecto los cambios de configuración realizados en el servicio de notificación de cambio de contraseña de MIM.Puede hacer clic en **Sí** en el menú emergente que aparece o puede reiniciar más tarde.

## Configurar PCNS
Cuando vuelva a conectarse al servidor de controlador de dominio como administrador de dominio, vaya a *C:\Program Files\Microsoft Password Change Notification*. Ejecute *pcnscfg.exe*.

