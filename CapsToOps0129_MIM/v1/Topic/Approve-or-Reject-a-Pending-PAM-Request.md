---
title: Aprobar o rechazar una solicitud pendiente de PAM
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 0632656f-ecf4-4090-85a8-216d5638140a
---
# Aprobar o rechazar una solicitud pendiente de PAM
Lo usa una cuenta con privilegios para aprobar, cerrar o rechazar una solicitud de elevación a un rol de PAM.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `http://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 POST| /api/pamresources/pamrequeststoapprove({approvalId)/Approve <br/>/api/pamresources/pamrequeststoapprove({approvalId)/Reject
### Parámetros de URL

 Parámetro| Descripción
----------|-----------
 approvalId| Identificador (GUID) del objeto de aprobación en PAM especificado como se indica a continuación: `guid'xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx'`.
### Parámetros de consulta

 Parámetro| Descripción
----------|--------------
 v| Opcional.Versión de la API.Si no se incluye, se usará la versión actual (la más reciente) de la API.Para obtener más información, consulte [Control de versiones en Detalles de servicio de la API de REST de PAM](PAM-REST-API-Service-Details.md#Versioning).

### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](PAM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de PAM*.
### Cuerpo de la solicitud

Ninguno.

## Respuesta

### Códigos de respuesta

 Código| Descripción
---------|---------
 200| Aceptar
 401| Sin autorización
 403| prohibido
 408| Tiempo de espera de solicitud
 500| error interno del servidor
 503| servicio no disponible
### Encabezados de respuesta

Para los encabezados de respuesta comunes, consulte [Encabezados de solicitud y respuesta HTTP](PAM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de PAM*.
### Cuerpo de respuesta

ninguno
## Ejemplo

### Solicitud

```
POST /api/pamresources/pamrequeststoapprove(guid'5dbd9d0c-0a9d-4f75-8cbd-ff6ffdc00143')/Approve HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK
```





