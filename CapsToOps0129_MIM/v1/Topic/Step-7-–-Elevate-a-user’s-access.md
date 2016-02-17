---
title: Paso 7: Elevar los privilegios de acceso de un usuario
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5325fce2-ae35-45b0-9c1a-ad8b592fcd07
---
# Paso 7: Elevar los privilegios de acceso de un usuario
En este paso se demuestra que un usuario puede solicitar acceso a un rol a través de MIM.

## Comprobación de que Jen no acceder al recurso con privilegios

Compruebe que Jen no puede acceder al recurso con privilegios en el bosque CORP con su cuenta CONTOSO\Jen.

1. Cierre la sesión en *CORPWKSTN*. (De este modo se quitarán todas las conexiones abiertas en caché).
2. Inicie sesión en *CORPWKSTN* como *CONTOSO\Jen* y cambie a la vista **Escritorio**.
3. Abra un símbolo del sistema **DOS**.
4. Escriba el comando `dir \\corpwkstn\corpfs`. Aparecerá el mensaje de error "Acceso denegado".
5. Deje abierta la ventana de símbolo del sistema.

## Solicite acceso con privilegios a MIM.

1. En *CORPWKSTN* asegúrese de que haya iniciado sesión como *CONTOSO\Jen* y de que haya abierta una ventana Comandos de **DOS**.
2. Escriba el siguiente comando:

`runas /user:Priv.Jen@priv.contoso.local powershell`

3. Cuando se le pida, escriba la contraseña de la cuenta *PRIV.Jen*. Se mostrará una nueva ventana de símbolo del sistema.
4. Cuando aparezca la ventana PowerShell, cambie a esa ventana y escriba los comandos siguientes. **Nota**: Todas las interacciones subsiguientes están sujetas a limitación temporal.

```
    Import-module MIMPAM
    $r = Get-PAMRoleForRequest | ? { $_.DisplayName –eq "CorpAdmins" }
    New-PAMRequest –role $r
    klist purge
```
<br/>
5. Una vez que se haya completado, cierre la ventana de **PowerShell** abierta recientemente.
6. En la ventana Comandos de DOS, escriba el siguiente comando:

`runas /user:Priv.Jen@priv.contoso.local powershell`

7. Escriba la contraseña de la cuenta *PRIV.Jen*. Se mostrará una nueva ventana de símbolo del sistema.

## Valide el acceso con privilegios elevados.

En la ventana abierta recientemente, escriba el siguiente comando:

```
    whoami /groups
    dir \\corpwkstn\corpfs
```
<br/>
Si el comando dir produce un error con el mensaje "Acceso denegado", vuelva a comprobar la relación de confianza.

## (Opcional) Activación

Para realizar la activación, solicite acceso con privilegios mediante el portal de ejemplo de PAM.

1. En *CORPWKSTN* asegúrese de que haya iniciado sesión como *CORP\Jen* y de que haya abierta una ventana Comandos de DOS.
2. Escriba el siguiente comando:

`runas /user:Priv.Jen@priv.contoso.local "c:\program files\Internet Explorer\iexplore.exe"`

3. Cuando se le pida, escriba la contraseña de la cuenta *PRIV.Jen*. Se mostrará una nueva ventana del explorador web.
4. Vaya a *http://pamsrv.priv.contoso.local:8090* y asegúrese de que se vea una página web en el portal de ejemplo.
5. En Internet Explorer, seleccione **Herramientas** \> **Opciones de Internet** y haga clic en la pestaña **Seguridad**.
6. Haga clic en **Zona de intranet Local** \> **Sitios** \> **Opciones avanzadas** y, luego, agregue el sitio web a la zona.
7. Cierre el cuadro de diálogo **Opciones de Internet**.
8. En la pestaña de la izquierda, haga clic en **Activar**. Seleccione el *rol de PAM* y, luego, haga clic en **Activar**.

**Nota**: En este entorno, también puede aprender a desarrollar aplicaciones que usan la API de REST de PAM que se describe en la [Referencia de la API de REST de Privileged Access Management](https://msdn.microsoft.com/en-us/library/mt228271.aspx) para activarla.

## Resumen

Una vez que haya completado los pasos descritos en esta guía del laboratorio de pruebas, habrá demostrado un escenario de administración de acceso con privilegios, en el que los privilegios de usuario se elevan durante un período limitado de tiempo, lo que permite al usuario acceder a recursos protegidos con una cuenta con privilegios independiente. Desde el momento en que finalice la sesión de elevación, la cuenta con privilegios no podrá acceder al recurso protegido. El *administrador de PAM* es quien decide qué grupos de seguridad representan roles con privilegios. Una vez que los derechos de acceso se hayan migrado al sistema de administración de acceso con privilegios, el acceso que anteriormente era posible desde la cuenta de usuario original ahora solo es posible si se inicia sesión con una cuenta con privilegios especiales que se pondrá a disposición tras realizar una solicitud. Como resultado, las pertenencias a grupos para grupos con muchos privilegios están en vigor durante un período de tiempo limitado.




