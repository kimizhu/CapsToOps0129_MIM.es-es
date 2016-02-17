---
title: Obtener respuesta de autenticaci&#243;n de tarjeta inteligente
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: e05ec898-06cd-4c17-a4f4-8f3545af0f14
---
# Obtener respuesta de autenticaci&#243;n de tarjeta inteligente
Obtiene la respuesta a un desafío de autenticación de Base CSP.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/requests/{reqid}/smartcards/{scid}/authenticationresponse
### Parámetros de URL

 Parámetro| Descripción
---------|------------
 reqid| Obligatorio.Identificador de solicitud (específico de MIM CM).
 scid| Obligatorio.Identificador de la tarjeta inteligente (específico de MIM CM).Obtenido a partir del objeto [Microsoft.Clm.Shared.Smartcards.Smartcard](http://msdn.microsoft.com/en-us/library/microsoft.clm.shared.smartcards.smartcard(v=vs.100%29.aspx).
### Parámetros de consulta

 Parámetro| Descripción
---------|------------
 atr| Opcional.Cadena ATR de la tarjeta inteligente.
 cardid| Obligatorio.Identificador de la tarjeta.
 challenge| Obligatorio.Cadena codificada en base64 que representa el desafío emitido por la tarjeta inteligente.
 diversified| Obligatorio.Marca booleana que indica si la clave de administración de la tarjeta inteligente se diversificó.

### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM+REST+API+Service+Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de la solicitud

ninguno

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

Si se ejecuta correctamente, devuelve un BLOB de bytes que representa la respuesta del desafío.

## Ejemplo

### Solicitud

```
GET /certificatemanagement/api/v1.0/requests/a9b4b42c-cc50-4c9b-89d1-bbc0bcd5a099/smartcards/17cf063d-e337-4aa9-a822-346554ddd3c9/authenticationresponse?cardid=bc88f13f-83ba-4037-8262-46eba1291c6e&challenge=1hFD%2Bcz%2F0so%3D&diversified=False HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

"F0Zudm4wPLY="
```
## Consulte también

- [Método Microsoft.Clm.Provision.ExecuteOperations.GetBaseCspResponse](https://msdn.microsoft.com/en-us/library/microsoft.clm.provision.executeoperations.getbasecspresponse (v=vs.100%29.aspx)



