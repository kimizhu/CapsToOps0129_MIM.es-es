---
title: Obtener operaciones de estado del perfil
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: f62c827b-5229-4b13-ad37-4f62ad231d30
---
# Obtener operaciones de estado del perfil
Obtiene una lista de las operaciones que el usuario actual puede realizar en el perfil especificado. Después, se puede iniciar una solicitud para cualquiera de las operaciones especificadas.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/profiles/{id}/operations <br/>/CertificateManagement/api/v1.0/smartcards/{id}/operations
### Parámetros de URL

 Parámetro| Descripción
---------|------------
 id| Identificador (GUID) del perfil o la tarjeta inteligente.
### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
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

Para los encabezados de respuesta comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de respuesta

Si se ejecuta correctamente, devuelve una lista de las operaciones que el usuario puede realizar en la tarjeta inteligente. Esta lista puede contener cualquier cantidad de las operaciones siguientes: *OnlineUpdate*, *Renew*, *Recover*, *RecoverOnBehalf*, *Retire*, *Revoke* y *Unblock*.

## Ejemplo

### Solicitud

```
GET /certificatemanagement/api/v1.0/smartcards/438d1b30-f3b4-4bed-85fa-285e08605ba7/operations HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

[
    "renew",
    "unblock",
    "retire"
]
```




