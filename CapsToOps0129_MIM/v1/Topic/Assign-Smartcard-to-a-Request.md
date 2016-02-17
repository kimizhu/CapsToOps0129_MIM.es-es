---
title: Asignar una tarjeta inteligente a una solicitud
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 20f0bf6e-9ae0-4d21-8117-ed63e29315e6
---
# Asignar una tarjeta inteligente a una solicitud
Enlaza la tarjeta inteligente especificada a la solicitud especificada. Una vez que se haya enlazado, la solicitud solo se podrá ejecutar con esta tarjeta.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 POST| /CertificateManagement/api/v1.0/smartcards
### Parámetros de URL

Ninguno.
### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de la solicitud

El cuerpo de la solicitud contiene las siguientes propiedades.

 Propiedad| Descripción
---------|-----------
 requestid| Identificador de la solicitud a la que se debe enlazar la tarjeta inteligente.
 cardid| cardid de la tarjeta inteligente.
 atr| Cadena ATR de la tarjeta inteligente.

## Respuesta

### Códigos de respuesta

 Código| Descripción
---------|---------
 201| Creado
 204| Sin contenido
 403| prohibido
 500| Error interno
### Encabezados de respuesta

Para los encabezados de respuesta comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de respuesta

Si se ejecuta correctamente, devuelve un URI al objeto de tarjeta inteligente recién creado.
## Ejemplo

### Solicitud

```
POST /CertificateManagement/api/v1.0/smartcards HTTP/1.1

{
    "requestid":"a9b4b42c-cc50-4c9b-89d1-bbc0bcd5a099",
    "cardid":"bc88f13f-83ba-4037-8262-46eba1291c6e",
    "atr":"3b8d0180fba000000397425446590301c8"
}
```
### Respuesta

```
HTTP/1.1 201 Created

"api/v1.0/smartcards/17cf063d-e337-4aa9-a822-346554ddd3c9"
```
## Consulte también

- [Microsoft.Clm.Provision.RequestOperations.CreateSmartcard Method (String, String, Request)](https://msdn.microsoft.com/es-es/library/windows/desktop/bb456812(v=vs.100%29.aspx)



