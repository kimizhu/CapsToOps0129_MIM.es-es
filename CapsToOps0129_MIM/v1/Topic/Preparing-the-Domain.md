---
title: Preparar el dominio
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
ms.assetid: 50345fda-56d7-4b6e-a861-f49ff90a8376
---
# Preparar el dominio

## Actualizar el dominio

1.  MIM requiere que Active Directory ya esté instalado. Asegúrese de que tiene un controlador de dominio en su entorno para un dominio que pueda administrar.

2.  Inicie sesión en el controlador de dominio como el administrador del dominio (*p. ej., Contoso\Administrador*) y cree las siguientes cuentas de usuario para los servicios de MIM.

    1.  Inicie PowerShell.

    2.  Escriba el siguiente script de PowerShell para actualizar el dominio.

        > [!NOTE]
        > En todos los ejemplos siguientes, **mimservername** representa el nombre del controlador de dominio, **domain** representa el nombre de dominio y **Pass@word1** representa una contraseña de ejemplo.

        ```
        import-module activedirectory
        $sp = ConvertTo-SecureString "Pass@word1" –asplaintext –force
        New-ADUser –SamAccountName MIMMA –name MIMMA 
        Set-ADAccountPassword –identity MIMMA –NewPassword $sp
        Set-ADUser –identity MIMMA –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName MIMSync –name MIMSync 
        Set-ADAccountPassword –identity MIMSync –NewPassword $sp
        Set-ADUser –identity MIMSync –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName MIMService –name MIMService 
        Set-ADAccountPassword –identity MIMService –NewPassword $sp
        Set-ADUser –identity MIMService –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName MIMSSPR –name MIMSSPR 
        Set-ADAccountPassword –identity MIMSSPR –NewPassword $sp
        Set-ADUser –identity MIMSSPR –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName SharePoint –name SharePoint 
        Set-ADAccountPassword –identity SharePoint –NewPassword $sp
        Set-ADUser –identity SharePoint –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName SqlServer –name SqlServer 
        Set-ADAccountPassword –identity SqlServer –NewPassword $sp
        Set-ADUser –identity SqlServer –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName BackupAdmin –name BackupAdmin 
        Set-ADAccountPassword –identity BackupAdmin –NewPassword $sp
        Set-ADUser –identity BackupAdmin –Enabled 1 -PasswordNeverExpires 1
        ```

3.  Cree grupos de seguridad para todos los grupos.

    1.  Ejecute el siguiente script de PowerShell:

    ```
    New-ADGroup –name MIMSyncAdmins –GroupCategory Security –GroupScope Global 		–SamAccountName MIMSyncAdmins
    New-ADGroup –name MIMSyncOperators –GroupCategory Security –GroupScope Global 		–SamAccountName MIMSyncOperators
    New-ADGroup –name MIMSyncJoiners –GroupCategory Security –GroupScope Global 		–SamAccountName MIMSyncJoiners
    New-ADGroup –name MIMSyncBrowse –GroupCategory Security –GroupScope Global 		–SamAccountName MIMSyncBrowse
    New-ADGroup –name MIMSyncPasswordReset –GroupCategory Security –GroupScope Global          –SamAccountName MIMSyncPasswordReset 
    Add-ADGroupMember -identity MIMSyncAdmins -Members Administrator
    Add-ADGroupmember -identity MIMSyncAdmins -Members MIMService
    ```

4.  Mediante PowerShell, agregue SPN para habilitar la autenticación Kerberos de las cuentas de servicio.

    ```
    setspn -S http/mimservername.domain.local Domain\SharePoint
    setspn -S http/mimservername Domain\SharePoint
    setspn -S FIMService/mimservername.domain.local Domain\MIMService
    setspn -S FIMSync/mimservername.domain.local Domain\MIMSync
    ```

