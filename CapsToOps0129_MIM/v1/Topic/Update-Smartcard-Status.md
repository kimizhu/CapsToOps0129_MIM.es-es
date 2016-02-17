---
title: Actualizar estado de tarjeta inteligente
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 598dace3-c6f2-447a-9301-c0b63ee38276
---
# Actualizar estado de tarjeta inteligente
Actualiza el estado de una tarjeta inteligente.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/requests/{reqid}/smartcards/{scid}
### Parámetros de URL

 Parámetro| Descripción
---------|------------
 reqid| Obligatorio.Identificador de solicitud (específico de MIM CM).
 scid| Obligatorio.Identificador de la tarjeta inteligente (específico de MIM CM).Esta es la propiedad "uuid" en el objeto [Microsoft.Clm.Shared.Smartcards.Smartcard](http://msdn.microsoft.com/es-es/library/microsoft.clm.shared.smartcards.smartcard(v=vs.100%29.aspx).
### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM+REST+API+Service+Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de la solicitud

El cuerpo de la solicitud contiene las siguientes propiedades.

 Propiedad| Descripción
---------|-----------
 estado| Estado en el que se debe establecer la solicitud.Por ejemplo, "Retirada".

## Respuesta

### Códigos de respuesta

 Código| Descripción
---------|---------
 200| Aceptar
 204| Sin contenido
 403| prohibido
 500| Error interno
### Encabezados de respuesta

Para los encabezados de respuesta comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM+REST+API+Service+Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de respuesta

Si se ejecuta correctamente, devuelve un objeto JSON serializado [Microsoft.Clm.Shared.Smartcards.Smartcard](http://msdn.microsoft.com/es-es/library/microsoft.clm.shared.smartcards.smartcard(v=vs.100%29.aspx) con las siguientes propiedades:

 Nombre| Descripción
-----|-----------
 AssignedUserUuid| Identificador del usuario al que está asignada la tarjeta inteligente.
 Atr| Cadena ATR de tarjeta inteligente de la tarjeta que se está inicializando actualmente.
 Comentario| Comentario que describe la tarjeta inteligente.
 Flags| Marcas que describen la tarjeta inteligente.
 Software intermedio| Middleware de la tarjeta inteligente.
 ParentSmartcardUuid| Identificador de la antigua tarjeta inteligente a la que ha reemplazado la nueva.
 PermanentSmartcardUuid| Identificador de la tarjeta inteligente permanente que está asociada a la tarjeta inteligente.
 PrimarySmartcardUuid| Identificador de la tarjeta inteligente principal.
 ProfileTemplateUuid| Identificador de la plantilla de perfil que contiene las directivas y la configuración que rigen la tarjeta inteligente.
 ProfileTemplateVersion| Versión de la plantilla de perfil en el momento en que se creó el perfil de tarjeta inteligente.
 SerialNumber| Número de serie de la tarjeta inteligente.
 Estado| Estado de la tarjeta inteligente.
 Uuid| Identificador del perfil de la tarjeta inteligente.
## Ejemplo

### Solicitud

```
PUT /certificatemanagement/api/v1.0/requests/b105403d-d021-41ea-9f11-be3d677d229e/smartcards/17cf063d-e337-4aa9-a822-346554ddd3c9 HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

{
    "Uuid":"17cf063d-e337-4aa9-a822-346554ddd3c9",
    "Status":6,
    "Flags":1,
    "ParentSmartcardUuid":"00000000-0000-0000-0000-000000000000",
    "PrimarySmartcardUuid":"00000000-0000-0000-0000-000000000000",
    "PermanentSmartcardUuid":"00000000-0000-0000-0000-000000000000",
    "AssignedUserUuid":"8f1590dc-d932-4b66-8e68-2e91c5880780",
    "ProfileTemplateUuid":"a039b4d0-5ce8-4eff-8651-181c6576fda3",
    "ProfileTemplateVersion":46,
    "Comment":"",
    "SerialNumber":"{bc88f13f-83ba-4037-8262-46eba1291c6e}",
    "Middleware":"MSBaseCSP",
    "Atr":"3b8d0180fba000000397425446590301c8"
}
```
## Consulte también

- [Microsoft.Clm.Shared.Smartcards.Smartcard Class](https://msdn.microsoft.com/es-es/library/microsoft.clm.shared.smartcards.smartcard(v=vs.100%29.aspx)



