---
title: Obtener datos de perfil
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 3eba062b-7adf-4766-9b94-cba1c7be2fd3
---
# Obtener datos de perfil
Obtiene una lista de perfiles de certificado de software de un usuario con una lista de las posibles operaciones que puede realizar el usuario actual. Después, se puede iniciar una solicitud para cualquiera de las operaciones especificadas.

**Nota**: El servidor establecerá el PIN solo si la directiva de plantilla de perfil indica que se debe hacer. De lo contrario, deberá proporcionarlo el usuario.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/profiles<br/>/CertificateManagement/api/v1.0/profiles/{id} <br/>/CertificateManagement/api/v1.0/requests/{requestid}/profiles
### Parámetros de URL

 Parámetro| Descripción
---------|------------
 id| Identificador (GUID) del perfil que se va a devolver.
 requestId| Identificador de la solicitud a la que se van a devolver los perfiles.
### Parámetros de consulta

 Parámetro| Descripción
---------|------------
 estado| Opcional.Indica el estado de los perfiles para los que se van a recuperar datos.Los posibles tipos de estado son: "Activo", "Aprobado", "Cancelado", "Completado", "Denegado", "Ejecutando", "Error", "Ninguno" y "Pendiente".<br/>Si no se especifica ningún estado, se devolverán todos los perfiles, independientemente de su estado.
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

Si se ejecuta correctamente, devuelve una lista de objetos JSON serializados [Microsoft.Clm.Shared.Profiles.Profile](https://msdn.microsoft.com/es-es/library/microsoft.clm.shared.profiles.profile(v=vs.100%29.aspx) con las siguientes propiedades:

 Propiedad| Descripción
---------|------------
 AssignedUserUuid| Identificador del usuario al que está asignado el perfil.
 Comentario| Comentario que describe el perfil.
 Flags| Marcas que describen el perfil.
 ParentProfileUuid| Identificador del perfil antiguo al que ha reemplazado el perfil.
 PrimaryProfileUuid| Identificador del perfil principal.
 ProfileOperations| Lista de las operaciones posibles que el usuario actual puede realizar en el perfil.
 ProfileTemplateUuid| Identificador de la plantilla de perfil que contiene las directivas y la configuración que rigen el perfil.
 ProfileTemplateVersion| Versión de la plantilla de perfil en el momento en que se creó el perfil.
 Estado| Estado del perfil.
 Uuid| Identificador del perfil.

## Ejemplo

### Solicitud

```
GET /certificatemanagement/api/v1.0/profiles?status=Active HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

[
    {
        "Uuid":"c0dd5c7d-ec35-4346-baca-3ad711e9722f",
        "Status":2,
        "Flags":1,
        "ParentProfileUuid":"1c9e2606-fea2-4048-a6ac-b014e54c22df",
        "PrimaryProfileUuid":"00000000-0000-0000-0000-000000000000",
        "AssignedUserUuid":"0378a33b-8650-4713-a727-efd233903643",
        "ProfileTemplateUuid":"8f31803f-8afc-49bb-911d-402ec264b589",
        "ProfileTemplateVersion":8,
        "Comment":"",
        "ProfileOperations":[
            "renew",
            "disable",
            "recover"
        ]
    },
    {
        "Uuid":"5ad77b40-aa42-4533-9396-c9c59fd021a8",
        "Status":2,
        "Flags":1,
        "ParentProfileUuid":"00000000-0000-0000-0000-000000000000",
        "PrimaryProfileUuid":"00000000-0000-0000-0000-000000000000",
        "AssignedUserUuid":"0378a33b-8650-4713-a727-efd233903643",
        "ProfileTemplateUuid":"8f31803f-8afc-49bb-911d-402ec264b589",
        "ProfileTemplateVersion":8,
        "Comment":"",
        "ProfileOperations":[
            "renew",
            "disable",
            "recover"
        ]
    },
    {
        "Uuid":"ff342953-c444-4dc7-b144-f5515d6460c6",
        "Status":2,
        "Flags":1,
        "ParentProfileUuid":"00000000-0000-0000-0000-000000000000",
        "PrimaryProfileUuid":"00000000-0000-0000-0000-000000000000",
        "AssignedUserUuid":"0378a33b-8650-4713-a727-efd233903643",
        "ProfileTemplateUuid":"1e3a31fe-699b-4a6b-945c-18b83c985bc1",
        "ProfileTemplateVersion":9,
        "Comment":"",
        "ProfileOperations":[
            "renew",
            "disable"
        ]
    }
]
```
## Consulte también

- [Microsoft.Clm.Shared.Profiles.Profile Class](https://msdn.microsoft.com/es-es/library/microsoft.clm.shared.profiles.profile(v=vs.100%29.aspx)



