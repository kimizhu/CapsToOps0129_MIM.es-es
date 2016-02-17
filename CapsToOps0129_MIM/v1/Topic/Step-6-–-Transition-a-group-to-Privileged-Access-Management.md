---
title: Paso 6: Realizar la transici&#243;n de un grupo a Privileged Access Management
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
ms.assetid: 7b689eff-3a10-4f51-97b2-cb1b4827b63c
---
# Paso 6: Realizar la transici&#243;n de un grupo a Privileged Access Management
La creación de cuentas con privilegios en el bosque PRIV se realiza mediante varios cmdlets nuevos de PowerShell.Estos cmdlets realizan las siguientes funciones:

-   Crean un nuevo grupo en el bosque *PRIV* con el mismo *SID* (Identificador de seguridad) que un grupo del bosque *CORP* y que un objeto de la base de datos del Servicio MIM correspondiente al grupo del bosque *PRIV*.

-   Por cada cuenta de usuario, los cmdlets crean dos objetos en la base de datos del Servicio MIM, correspondientes al usuario del bosque *CORP* y a la nueva cuenta de usuario del bosque *PRIV*.

-   Crean un objeto de *rol de PAM* en la base de datos del Servicio MIM.

    En esta vista previa de la versión preliminar se deben ejecutar los cmdlets una vez por cada grupo y una vez por cada miembro de un grupo.(Tenga en cuenta que los cmdlets de migración no cambian ni modifican ningún usuario ni grupo del bosque *CORP*: eso debe hacerlo posteriormente y de forma manual el administrador de PAM).

    1.  Inicie sesión en *PAMSRV* como administrador de dominio y compruebe que los servicios se estén ejecutando.

        1.  Asegúrese de que haya iniciado sesión en *PAMSRV* como *PRIV\Administrador*.

        2.  Abra **Servicios**.

        3.  Compruebe que se esté ejecutando **Forefront Identity Manager**.Si no se está ejecutando el servicio, haga clic con el botón derecho en el servicio y seleccione **iniciar** para iniciar el servicio.

    2.  Ejecute los cmdlets de administración de grupos y usuarios de MIM PAM para copiar el grupo CorpAdmins y su miembro, Jen, del dominio *CONTOSO* en el dominio *PRIV*.

        1.  Inicie PowerShell y ejecute los siguientes comandos, especificando la contraseña de administrador (*CONTOSO\Administrador*) del dominio *CORP* cuando se le solicite:

            ```
            Import-Module MIMPAM
            Import-Module ActiveDirectory
            $ca = get-credential –UserName CONTOSO\Administrator –Message "CORP forest domain admin credentials"
            $pg = New-PAMGroup –SourceGroupName "CorpAdmins" –SourceDomain CONTOSO.local                 –SourceDC CORPDC.contoso.local –Credentials $ca 
            $sj = New-PAMUser –SourceDomain CONTOSO.local –SourceAccountName Jen 
            $jp = ConvertTo-SecureString "Pass@word1" –asplaintext –force
            Set-ADAccountPassword –identity priv.Jen –NewPassword $jp
            Set-ADUser –identity priv.Jen –Enabled 1 
            Add-ADGroupMember "Protected Users" priv.Jen
            $pr = New-PAMRole –DisplayName "CorpAdmins" –Privileges $pg –Candidates $sj
            ```
            Como referencia, el comando **New-PAMGroup** toma los siguientes parámetros:

            -   El nombre de dominio del bosque CORP en forma NetBIOS.

            -   El nombre del grupo a copiar desde ese dominio.

            -   El nombre NetBIOS del controlador de dominio del bosque CORP.

            -   Las credenciales de un usuario administrador de dominio del bosque CORP.

        Después realizará la transición de elevación a JIT de un usuario que actualmente es miembro de grupo y luego comprobará que los derechos de acceso entre bosques sean eficaces o la cuenta de administrador de usuario.

    3.  En *CORPDC* quite la cuenta de Jen del grupo *CONTOSO CorpAdmins*, si todavía pertenece a él.

        1.  Inicie sesión en *CORPDC* como *CONTOSO\Administrador*.

        2.  Inicie PowerShell, ejecute el siguiente comando y confirme el cambio.

            ```
            Remove-ADGroupMember -identity "CorpAdmins" -Members "Jen"
            ```

