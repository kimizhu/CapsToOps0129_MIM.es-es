---
title: Obtener opciones de generaci&#243;n de solicitud de certificado
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 36bd1fc9-3443-4028-90e7-a24fef0ec0ae
---
# Obtener opciones de generaci&#243;n de solicitud de certificado
Obtiene los parámetros para la generación de solicitud de certificado del lado cliente.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/requests/{requestid}/certificaterequestgenerationoptions
### Parámetros de URL

 Parámetro| Descripción
--------|--------------
 requestid| Obligatorio.Identificador GUID de la solicitud de MIM CM para la que se deben recuperar los parámetros de generación de solicitud de certificado.
### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de la solicitud

Ninguno.


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

Si se ejecuta correctamente, devuelve la lista de objetos CertificateRequestGenerationOptions. Cada objeto CertificateRequestGenerationOptions corresponde a una única solicitud de certificado que el cliente tiene que generar y tiene las siguientes propiedades:

 Propiedad| Descripción
--------|-----------
 Exportable| Valor que especifica si se puede exportar la clave privada creada para la solicitud.
 FriendlyName| Nombre para mostrar del certificado inscrito.
 HashAlgorithmName| Algoritmo hash usado al crear la firma de la solicitud de certificado.
 KeyAlgorithmName| Algoritmo de clave pública.
 KeyProtectionLevel| Nivel de protección de clave de alta seguridad.
 KeySize| Tamaño en bits de la clave privada que se va a generar.
 KeyStorageProviderNames| Lista con los proveedores de almacenamiento de claves (KSP) aceptables que se pueden usar para generar la clave privada.En caso de que el primer KSP no se pueda usar para generar la solicitud de certificado, se puede usar cualquiera de los KSP especificados hasta que uno de ellos lo consiga.
 KeyUsages| Operación que puede realizar la clave privada creada para esta solicitud de certificado.El valor predeterminado es Firma.
 Firmante| Nombre del firmante.
**Nota**: Puede encontrar más información sobre estas propiedades en la descripción de la [clase Windows.Security.Cryptography.Certificates.CertificateRequestProperties](https://msdn.microsoft.com/en-us/library/windows/apps/br212079.aspx), pero tenga en cuenta que no hay una correspondencia exacta entre esta clase y los objetos CertificateRequestGenerationOptions.

## Ejemplo

### Solicitud

```
GET /certificatemanagement/api/v1.0/requests/a9b4b42c-cc50-4c9b-89d1-bbc0bcd5a099/certificaterequestgenerationoptions HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

[
    {
        "Subject":"",
        "KeyAlgorithmName":"RSA",
        "KeySize":2048,
        "FriendlyName":"",
        "HashAlgorithmName":"SHA1",
        "KeyStorageProviderNames":[
            "Contoso Smart Card Key Storage Provider"
        ],
        "Exportable":0,
        "KeyProtectionLevel":0,
        "KeyUsages":3
    }
]
```




