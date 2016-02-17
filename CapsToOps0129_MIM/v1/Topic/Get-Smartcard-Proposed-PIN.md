---
title: Get Smartcard Proposed PIN
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: ced93932-9912-4b32-9586-ada69b38a796
---
# Get Smartcard Proposed PIN
Obtiene el PIN de usuario generado por el servidor.

**Nota**: El servidor establecerá el PIN solo si la directiva de plantilla de perfil indica que se debe hacer. De lo contrario, deberá proporcionarlo el usuario.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/smartcards/{id}/serverproposedpin
### Parámetros de URL

 Parámetro| Descripción
---------|------------
 id| Identificador de la tarjeta inteligente (específico de MIM CM).Obtenido del objeto Microsft.Clm.Shared.Smartcard.
### Parámetros de consulta

 Parámetro| Descripción
---------|------------
 atr| Cadena ATR de la tarjeta.
 cardid| Identificador de la tarjeta.
 challenge| Cadena codificada en base64 que representa el desafío emitido por la tarjeta inteligente.
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

Si se ejecuta correctamente, devuelve una cadena que representa el código PIN propuesto por el servidor.

## Ejemplo

### Solicitud

```
GET GET /CertificateManagement/api/v1.0/smartcards/C6BAD97C-F97F-4920-8947-BE980C98C6B5/serverproposedpin HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

... body coming soon
```




