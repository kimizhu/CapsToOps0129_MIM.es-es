---
title: Obtener certificados de tarjeta inteligente o de perfil
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 206bde70-4af8-46fa-9c0b-f574745b0977
---
# Obtener certificados de tarjeta inteligente o de perfil
Obtiene una lista de certificados asociados al perfil específico de tarjeta inteligente o de software.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/profiles/{id}/certificates <br/>/CertificateManagement/api/v1.0/smartcards/{id}/certificates
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

Si se ejecuta correctamente, devuelve una lista de objetos JSON serializados [Microsoft.Clm.Shared.Certificates.X509ClmCertificate](https://msdn.microsoft.com/es-es/library/microsoft.clm.shared.certificates.x509clmcertificate(v=vs.100%29.aspx) con las siguientes propiedades:

 Nombre| Descripción
-----|------------
 ArchivedOnCa| Valor booleano que indica si el certificado se archiva en la entidad de certificación (CA).
 CertificateType| Tipo del certificado.
 IsKeyHistory| Valor booleano que indica si el certificado es un certificado de historial de claves.
 SerialNumber| Numero de serie del certificado.
 TemplateCommonName| Nombre común de la plantilla de certificado del certificado.
 Huella digital| Huella digital del certificado.
## Ejemplo

### Solicitud

```
GET /certificatemanagement/api/v1.0/smartcards/5badfea3-de31-4837-99f9-8249515a5473/certificates HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

[
    {
        "IsKeyHistory":false,
        "ArchivedOnCa":false,
        "CertificateType":1,
        "TemplateCommonName":"ContosoVirtualSmartCardLimitedRelease-KSP",
        "SerialNumber":"1B0000B01052AFA01313FB77AC00010000B010",
        "Thumbprint":"C52B0C5FB8AAD31A5B239FF2712ED14122D67D30"
    },
    {
        "IsKeyHistory":false,
        "ArchivedOnCa":false,
        "CertificateType":1,
        "TemplateCommonName":"ContosoVirtualSmartCardLimitedRelease-KSP",
        "SerialNumber":"1B0000B011AB48AE7D664ED5D900010000B011",
        "Thumbprint":"E7C4324896271BE869544FF28AA2B1BF3B3BDFCF"
    },
    {
        "IsKeyHistory":false,
        "ArchivedOnCa":false,
        "CertificateType":1,
        "TemplateCommonName":"ContosoVirtualSmartCardLimitedRelease-KSP",
        "SerialNumber":"1B0000B01ABCF2D38A0CCEAD8F00010000B01A",
        "Thumbprint":"D9293B5414C644888444541B64631E90F2612425"
    },
    {
        "IsKeyHistory":false,
        "ArchivedOnCa":false,
        "CertificateType":1,
        "TemplateCommonName":"ContosoVirtualSmartCardLimitedRelease-KSP",
        "SerialNumber":"1B0000B1F02865CF2C3A9DD96D00010000B1F0",
        "Thumbprint":"6615DDC8603DBA789D724502627682F37D0FC2D0"
    }
]
```
## Consulte también

- [Microsoft.Clm.Provision.FindOperations.FindCertificates Method](https://msdn.microsoft.com/es-es/library/microsoft.clm.provision.findoperations.findcertificates(v=vs.100%29.aspx)
- [Microsoft.Clm.Shared.Certificates.X509ClmCertificate Class](https://msdn.microsoft.com/es-es/library/microsoft.clm.shared.certificates.x509clmcertificate(v=vs.100%29.aspx)



