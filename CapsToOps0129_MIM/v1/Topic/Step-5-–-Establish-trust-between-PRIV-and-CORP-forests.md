---
title: Paso 5: Establecer la confianza entre bosques PRIV y CORP
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
ms.assetid: eef248c4-b3b6-4b28-9dd0-ae2f0b552425
---
# Paso 5: Establecer la confianza entre bosques PRIV y CORP
Los controladores de dominio *PRIV* y *CONTOSO* están enlazados mediante una relación de confianza que permite a los usuarios del dominio *PRIV* tener acceso a recursos en el dominio CORP.

1.  Antes de establecer la confianza, todos los controladores de dominio deben configurarse para la resolución de nombres DNS para su equivalente, en función de la dirección IP del otro controlador de dominio o servidor DNS.

    1.  Asegúrese de que no haya otros servidores DNS que estén proporcionando servicios de nombres de dominio a los equipos de ningún dominio.Si las máquinas virtuales tienen interfaces de red conectadas a redes públicas, puede ser necesario reemplazar la configuración de la interfaz de red de Windows para asegurarse de que las máquinas virtuales no utilizan una dirección de servidor DNS proporcionada por DHCP.

    2.  (Opcional) En *CORPDC*, inicie PowerShell y escriba el siguiente comando.

        ```
        nslookup -qt=ns priv.contoso.local.
        ```
        Asegúrese de que la salida indica un registro de servidor de nombres para este dominio.

    3.  (Opcional) Como alternativa, use el **Administrador de DNS** (ubicado en Inicio, Herramientas de aplicación, DNS) para confirmar el reenvío de nombres DNS del dominio *PRIV* a la dirección IP de *PRIVDC*.En este programa, expanda los nodos *CORPDC, Zonas de búsqueda directa, contoso.local* y asegúrese de que está presente una clave denominada *priv* como tipo de servidor de nombres (NS).

        ![](../Image/PAM_GS_DNS_Manager.png)

2.  En *PAMSRV*, establezca una confianza unidireccional con *CORPDC* para que el controlador de dominio CORP confíe en el bosque *PRIV*.

    1.  Asegúrese de haber iniciado sesión en *PAMSRV* como administrador del dominio *PRIV* (por ejemplo, como *PRIV\Administrador*).

    2.  Inicie PowerShell.

    3.  Escriba los siguientes comandos de PowerShell e introduzca las credenciales de administrador del dominio CORP (p. ej., *CONTOSO\Administrador*) cuando se le solicite, si es necesario.

        ```
        $ca = get-credential
        New-PAMTrust -SourceForest "contoso.local" -Credentials $ca
        New-PAMDomainConfiguration -SourceDomain "contoso" -Credentials $ca
        ```

3.  En *CORPDC*, habilite el acceso de lectura a Active Directory para los administradores de PRIV y el servicio de supervisión.

    1.  Asegúrese de haber iniciado sesión en *CORPDC* como administrador del dominio Contoso (por ejemplo, como *Contoso\Administrador*).

    2.  Inicie **Usuarios y equipos de Active Directory**.

    3.  Haga clic con el botón secundario en el dominio **contoso.local** y seleccione **Delegar control**.

    4.  En la pestaña Usuarios y grupos seleccionados, haga clic en **Agregar**.

    5.  En la ventana emergente para **seleccionar usuarios, equipos** o **grupos**, haga clic en **Ubicaciones** y cambie la ubicación a *priv.contoso.local*.Como nombre de objeto, escriba *Admins. del dominio* y haga clic en **Comprobar nombres**.   Cuando aparezca una ventana emergente, escriba *priv\administrador* como nombre de usuario y la contraseña.

    6.  Tras *Admins. del dominio*, escriba "*; MIMMonitor*".Cuando aparezcan subrayados los nombres Admins. del dominio y MIMMonitor, haga clic en **Aceptar** y, a continuación, haga clic en **Siguiente**.

    7.  En la lista de tareas comunes, seleccione "**Leer toda la información del usuario**" y, a continuación, haga clic en **Siguiente** y en **Finalizar**.

    8.  Cierre **Usuarios y equipos de Active Directory**.

4.  En *PAMSRV*, inicie los **servicios de supervisión y de componentes**.

    1.  Asegúrese de haber iniciado sesión en *PAMSRV* como administrador del dominio *PRIV* (por ejemplo, como *PRIV\Administrador*).

    2.  Inicie PowerShell.

    3.  Escriba los siguientes comandos de PowerShell.

        ```
        net start "PAM Component service"
        net start "PAM Monitoring service"
        ```

5.  (Opcional) Compruebe que el historial de SID está habilitado y que el filtrado de SID está deshabilitado en la confianza del dominio *CORP* al dominio *PRIV*.

    1.  Asegúrese de haber iniciado sesión en *CORPDC* como administrador del dominio (por ejemplo, como *CONTOSO\Administrador*).

    2.  Abra una ventana de PowerShell.

    3.  Utilice **netdom** para asegurarse de que el historial de SID está habilitado y el filtrado de SID deshabilitado.Tipo:

        ```
        netdom trust contoso.local /quarantine /enablesidhistory:yes /domain priv.contoso.local
        ```
        El resultado debe indicar "**Habilitando historial de SID para esta confianza**" o "**El historial de SID ya está habilitado para esta confianza**".

        El resultado debe indicar también "**No está habilitado el filtrado por SID para esta confianza**".Para obtener más información, vea [http://technet.microsoft.com/library/cc772816(v=WS.10).aspx](http://technet.microsoft.com/library/cc772816%28v=WS.10%29.aspx).

