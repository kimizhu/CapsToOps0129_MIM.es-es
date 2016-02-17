---
title: Obtener la directiva de tarjeta inteligente
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: a16d0084-3300-4391-875f-69d687054cbe
---
# Obtener la directiva de tarjeta inteligente
Obtiene la directiva de configuración de la tarjeta inteligente. El objeto SmartcardConfig devuelto por la solicitud contiene datos que determinarán qué operaciones de tarjeta inteligente deben realizarse durante la ejecución de la solicitud. La configuración determina lo siguiente:

- Si el usuario o el servidor proporciona el PIN del usuario.
- Si la clave de administración se debe diversificar.
- Si la tarjeta inteligente debe inicializarse (formatearse) antes de su uso.


**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/profiletemplates/{id}/configuration/smartcards
### Parámetros de URL

 Parámetro| Descripción
--------|-------------
 id| Obligatorio.GUID correspondiente a la plantilla de perfil de la que se va a extraer la directiva de tarjeta inteligente.
### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de la solicitud

ninguno

## Respuesta

### Códigos de respuesta

 Código| Descripción
---------|---------
 200| Aceptar
 403| prohibido
 204| Sin contenido
 500| Error interno
### Encabezados de respuesta

Para los encabezados de respuesta comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de respuesta

Si se ejecuta correctamente, devuelve un objeto [SmartcardConfig](http://msdn.microsoft.com/en-us/library/microsoft.clm.shared.profiletemplates.smartcardconfig(v=vs.100%29.aspx) con las siguientes propiedades.

 Nombre| Descripción
-----|-----------
 AdminPinPolicy| Directiva de PIN de administración de tarjetas inteligentes.
 AllowSmartcardReuse| Valor booleano que indica si se puede emitir para un nuevo usuario una tarjeta inteligente que se ha cancelado previamente.
 CardInitializationData| Datos de inicialización para el proveedor de inicialización de la tarjeta inteligente.
 CardInitializationType| Nombre completo del tipo de .NET Framework del proveedor de inicialización de tarjeta inteligente.
 CertificateLabel| Nombre descriptivo de certificado que se aplica a los certificados emitidos.
 DefaultAdminKeyHex| La clave de administrador predeterminada en formato hexadecimal.
 DiversifyAdminKey| Valor booleano que indica si la clave de administración de tarjetas inteligentes se diversifica.
 DoNotInstallCaCertificates| Valor booleano que indica si la cadena completa de certificados no se instalará en el cliente.
 EraseOnOverflow| Valor booleano que indica si la tarjeta inteligente se borrará al producirse un desbordamiento de la tarjeta inteligente.
 InitializeNewSmartcard| Valor booleano que indica si las nuevas tarjetas inteligentes se inicializan antes de utilizarse.
 MaxNumberOfCertificates| Número máximo de certificados que pueden almacenarse en una tarjeta inteligente.
 ProviderId| Identificador del proveedor de la tarjeta inteligente.
 ProviderName| Nombre del proveedor de la tarjeta inteligente.
 ProviderType| Tipo de proveedor de la tarjeta inteligente.
 SmartcardPrintPolicy| Directiva de impresión de la tarjeta inteligente.
 UserPinOption| Directiva de PIN inicial de usuario de la tarjeta inteligente.
 UserPinPolicy| Directiva de PIN de usuario de la tarjeta inteligente.
 UseSecureKeyInjection| Valor booleano que indica si se utilizará el protocolo de inyección de clave segura para la plantilla de perfil.
## Ejemplo

### Solicitud

```
GET /certificatemanagement/api/v1.0/profiletemplates/a039b4d0-5ce8-4eff-8651-181c6576fda3/configuration/smartcards HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

{
    "UserPinOption":3,
    "UserPinPolicy":{
        "MinLength":10,
        "MaxLength":10,
        "CharacterSet":1,
        "Rollover":false,
        "DefaultValue":"11111111"
    },
    "AdminPinPolicy":{
        "MinLength":10,
        "MaxLength":10,
        "CharacterSet":1,
        "Rollover":true,
        "DefaultValue":"11111111"
    },
    "DefaultAdminKeyHex":"",
    "ProviderName":"Contoso Smart Card Base CSP",
    "ProviderId":"ContosoCSP",
    "ProviderType":2,
    "DiversifyAdminKey":true,
    "CardInitializationType":"Microsoft.Clm.Custom.BusinessLayer.HSMCardInitialization,HSMCardInitialization",
    "CardInitializationData":"",
    "InitializeNewSmartcard":true,
    "UseSecureKeyInjection":false,
    "DoNotInstallCaCertificates":false,
    "CertificateLabel":"{Template!cn}",
    "MaxNumberOfCertificates":0,
    "AllowSmartcardReuse":false,
    "EraseOnOverflow":false,
    "UseVirtualSmartcards":true,
    "SmartcardPrintPolicy":{
        "FieldMapping":"",
        "ProjectName":"",
        "CardName":"",
        "Print":false
    }
}
```
## Consulte también

- [Microsoft.Clm.Shared.ProfileTemplates.SmartcardConfig Class](http://msdn.microsoft.com/en-us/library/microsoft.clm.shared.profiletemplates.smartcardconfig(v=vs.100%29.aspx)



