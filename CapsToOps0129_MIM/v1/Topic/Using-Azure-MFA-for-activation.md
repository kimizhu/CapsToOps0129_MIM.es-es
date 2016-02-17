---
title: Uso de Azure MFA para la activaci&#243;n
ms.custom: 
  - inhenk
  - identity management
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.service: active-directory
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5134a112-f73f-41d0-a5a5-a89f285e1f73
---
# Uso de Azure MFA para la activaci&#243;n
Al configurar un rol de PAM, puede especificar los requisitos de autorización necesarios para que un usuario candidato active el rol. Las opciones que implementa la actividad de autorización de PAM son:

- Aprobación del propietario de rol
- Azure MFA

Si ninguna de las comprobaciones está habilitada, los usuarios candidatos se activan automáticamente para el rol correspondiente.

Microsoft Azure Multi-Factor Authentication (MFA) es un servicio de autenticación que requiere que los usuarios verifiquen sus intentos de inicio de sesión con una aplicación móvil, una llamada de teléfono o un mensaje de texto. Está disponible para su uso con Microsoft Azure Active Directory y como servicio para aplicaciones empresariales en la nube y locales. Para el escenario de PAM, Azure MFA ofrece un mecanismo de autenticación adicional que puede usarse en la autorización, independientemente de la forma en que un usuario candidato se haya autenticado previamente en el dominio de Windows PRIV.

## Requisitos previos

Para poder usar Azure MFA con MIM, necesitará:

- Acceso a Internet desde cada servicio MIM que proporcione PAM, para ponerse en contacto con el servicio Azure MFA.
- Una suscripción de Azure.
- Licencias de Azure Active Directory Premium para los usuarios candidatos o un medio de licencia alternativo para Azure MFA.
- Números de teléfono de todos los usuarios candidatos.

## Creación de un proveedor de Azure MFA

En la sección siguiente, vamos a configurar el proveedor de Azure MFA en Microsoft Azure Active Directory. Si ya usa Azure MFA, tanto de forma independiente como configurado con Azure Active Directory Premium, vaya a la sección siguiente.

1.  Abra un explorador web y conéctese al Portal de administración de Azure en [https://manage.windowsazure.com](https://manage.windowsazure.com) como usuario administrador de suscripciones de Azure.

2.  En la esquina inferior izquierda, haga clic en **Nuevo**.

3.  Haga clic en **Servicios de aplicaciones \> Active Directory \> Proveedor de autenticación multifactor \> Creación rápida**.

4.  En el campo **Nombre**, escriba **PAM** y, en el campo Modelo de uso, seleccione Por usuario habilitado. Si ya tiene un directorio de Azure AD, seleccione ese directorio. Por último, haga clic en **Crear**.

## Descarga de las credenciales del servicio Azure MFA

A continuación, vamos a generar un archivo que incluye el material de autenticación requerido por MFA para poder establecer contacto con Azure MFA.

1. Abra un explorador web y conéctese al Portal de administración de Azure en [https://manage.windowsazure.com](https://manage.windowsazure.com) como administrador de suscripciones de Azure.

2.  Haga clic en **Active Directory** en el menú del Portal de Azure y, luego, haga clic en la pestaña **Proveedores de autenticación multifactor**.

3.  Haga clic en el proveedor de Azure MFA que va a usar para PAM y, a continuación, haga clic en **Administrar**.

4.  En el panel izquierdo de la ventana nueva, bajo **Configurar**, haga clic en **Configuración**.

5.  En la ventana **Azure Multi-Factor Authentication**, haga clic en **SDK** bajo **Descargas**.

6.  Haga clic en el vínculo **Descargar** en la columna ZIP del archivo con lenguaje **SDK para ASP.net 2.0 C#**.

![Activación de Azure MFA](../Image/PAM-Azure-MFA-Activation-Image-1.png)

7.  Copie el archivo ZIP resultante en cada sistema donde esté instalado el servicio de MIM.


--------------------------------------------------


NOTA: tenga en cuenta que el archivo ZIP contiene el material de claves que se usa para autenticarse en el servicio Azure MFA.

--------------------------------------------------


## Configuración del servicio MIM para Azure MFA

1.  Inicie sesión en el equipo donde está instalado el servicio MIM, como administrador o como el usuario que ha instalado MIM.

2.  Cree una nueva carpeta de directorio en el directorio donde se instaló el servicio MIM, como *C:\\Archivos de programa\\Microsoft Forefront Identity Manager\\2010\\Service\\MfaCerts*.

3.  Con el Explorador de Windows, navegue a la carpeta "pf\\certs" del archivo ZIP que descargó en la sección anterior y copie el archivo *cert\_key.p12* en el nuevo directorio.

4.  Con el Explorador de Windows, navegue a la carpeta "pf" del archivo ZIP y abra el archivo *pf\_auth.cs* en un editor de texto. Si no tiene instalado un editor de texto, use Wordpad para ver el archivo.

5.  Busque estos tres parámetros: LICENSE\_KEY, GROUP\_KEY, CERT\_PASSWORD.

![Activación de MFA](../Image/PAM-Azure-MFA-Activation-Image-2.png)

6.  Con el Bloc de notas, abra el archivo *MfaSettings.xml* ubicado en *C:\\Archivos de programa\\Microsoft Forefront Identity Manager\\2010\\Service*.

7.  Copie los valores de los parámetros LICENSE\_KEY, GROUP\_KEY, CERT\_PASSWORD del archivo *pf\auth.cs* en los elementos xml correspondientes del archivo *MfaSettings.xml*.

8.  En el elemento XML &lt;CertFilePath&gt;, especifique el nombre completo de la ruta de acceso del archivo*cert\_key.p12* extraído anteriormente.

9.  En el elemento &lt;username&gt;, escriba un nombre de usuario cualquiera.

10.  En el elemento &lt;DefaultCountryCode&gt;, escriba el código de país para llamar a los usuarios; por ejemplo, 1 para Estados Unidos y Canadá. Este valor se utiliza en caso de que los usuarios se registren con números de teléfono que no tengan código de país. Si el número de teléfono de un usuario tiene un código de país internacional distinto del configurado para la organización, ese código de país debe incluirse en el número de teléfono que se va a registrar.

11.  Guarde y sobrescriba el archivo *MfaSettings.xml* en la carpeta del servicio MIM *C:\\Archivos de programa\\Microsoft Forefront Identity Manager\\2010\\Service*.


--------------------------------------------------


Nota: Al final del proceso, asegúrese de que el archivo *MfaSettings.xml*, o cualquier copia de este o del archivo ZIP, no se puedan leer públicamente.

--------------------------------------------------



## Habilitación de un usuario de PAM para Azure MFA

Para que un usuario active un rol que requiere Azure MFA, el número de teléfono del usuario debe estar almacenado en MIM. Hay dos formas de establecer este atributo.

Con la primera, el comando New-PAMUser copia un atributo de número de teléfono de la entrada de directorio del usuario en el dominio CORP a la base de datos del servicio MIM. Tenga en cuenta que se trata de una operación única.

Con la segunda, el comando Set-PAMUser actualiza el atributo de número de teléfono en la base de datos del servicio MIM. Por ejemplo,el código siguiente reemplaza un número de teléfono existente de un usuario de PAM en el servicio MIM. La entrada de directorio no se modifica.

```
Set-PAMUser (Get-PAMUser -SourceDisplayName Jen) -SourcePhoneNumber 12135551212
```


## Habilitación de un rol de PAM para Azure MFA

Una vez almacenados los números de teléfono de todos los usuarios candidatos para un rol de PAM en la base de datos del servicio MIM, el rol puede habilitarse para Azure MFA. Para ello, se usa el comando New-PAMRole o Set-PAMRole. Por ejemplo,

```
Set-PAMRole (Get-PAMRole -DisplayName "R") -MFAEnabled 1
```



Azure MFA puede deshabilitarse para un rol si se especifica el parámetro "-MFAEnabled 0" en el comando Set-PAMRole.

## Solucionar problemas

Los siguientes eventos pueden encontrarse en el registro de eventos de Privileged Access Management:

| ID| Gravedad| Generado por| Descripción|
|-----|-------------|------------------------|------------------------------------------------------------------|
| 101| Error| Servicio MIM| El usuario no completó Azure MFA (por ejemplo, no respondió al teléfono).|
| 103| Información de| Servicio MIM| El usuario completó Azure MFA durante la activación.|
| 825| Advertencia| Servicio de supervisión de PAM| El número de teléfono ha cambiado.|
Para obtener más información sobre las llamadas telefónicas con errores (evento 101), también puede ver o descargar un informe de Azure MFA.

1.  Abra un explorador web y conéctese al portal de administración de Azure en [https://manage.windowsazure.com](https://manage.windowsazure.com) como administrador global de Azure AD.

2.  Haga clic en **Active Directory** en el menú del Portal de Azure y, luego, haga clic en la pestaña **Proveedores de autenticación multifactor**.

3.  Haga clic en el proveedor de Azure MFA que usa para PAM y, luego, haga clic en **Administrar**.

4.  En la nueva ventana, haga clic en **Uso** y, luego, en **Detalles de usuario**.

5.  Seleccione el intervalo de tiempo y active la casilla por el **Nombre** en la columna del informe adicional. Haga clic en **Exportar a CSV**.

6.  Una vez generado el informe, podrá verlo en el portal. En caso de que el informe de MFA sea extenso, descárguelo en un archivo CSV. Los valores "**SDK**" de la columna **TIPO DE AUTENT.** indican las filas que son relevantes como solicitudes de activación de PAM: se trata de eventos procedentes de MIM o de otro software local. El campo **NOMBRE DE USUARIO** es el GUID del objeto de usuario en la base de datos del servicio MIM. Si una llamada no se ha realizado correctamente, el valor de la columna **AUTHD** será "**No**" y el valor de la columna **RESULTADO DE LLAMADA** contendrá los detalles del motivo del error.




