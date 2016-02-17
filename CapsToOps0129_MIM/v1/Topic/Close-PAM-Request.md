---
title: Cerrar solicitud de PAM
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: ca3a1a68-9a2b-47da-bfc1-eaa360cbe609
---
# Cerrar solicitud de PAM
Usada por una cuenta con privilegios, aprueba, cierra o rechaza una solicitud de elevación a un rol de PAM iniciada por esa cuenta.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `http://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 POST| /api/pamresources/pamrequests({requestId)/Close
### Parámetros de URL

 Parámetro| Descripción
----------|-----------
 requestId| Identificador (GUID) de la solicitud de PAM que se desea cerrar, especificado como se indica a continuación: `guid'xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx'`.
### Parámetros de consulta

 Parámetro| Descripción
----------|--------------
 v| Opcional.Versión de la API.Si no se incluye, se usará la versión actual (la más reciente) de la API.Para obtener más información, consulte [Control de versiones en Detalles de servicio de la API de REST de PAM](PAM-REST-API-Service-Details.md#Versioning).
### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](PAM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de PAM*.
### Cuerpo de la solicitud

ninguno

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
POST /api/pamresources/pamrequests(guid'5ec10e61-cdd1-404e-a18e-740467d87dbf')/Close HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK
```





