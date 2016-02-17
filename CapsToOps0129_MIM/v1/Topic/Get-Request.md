---
title: Get Request
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: dcacf36c-0670-44d7-9f40-388667235271
---
# Get Request
Obtiene una o varias solicitudes de MIM CM especificadas.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/requests/{id}
### Parámetros de URL

 Propiedad| Descripción
---------|--------
 id| Opcional.GUID de una solicitud que se desea recuperar.
### Parámetros de consulta

 Propiedad| Descripción
---------|--------
 targetuser| Opcional.Usuario de destino de la solicitud.Si no se especifica ningún destino, se devolverán todas las solicitudes, independientemente del usuario de destino.<br/> **Nota**: Actualmente, solo se admite "current".
 estado| Opcional.Indica el estado de la solicitud que se va a recuperar.Los posibles tipos de estado son: *Aprobado*, *Cancelado*, *Completado*, *Denegado*, *Ejecutando*, *Error*, *Ninguno* y *Pendiente*.<br/>Si no se especifica ningún estado, se devolverán todas las solicitudes, independientemente de su estado.
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

En caso de éxito, devuelve uno o más objetos [Request](https://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.clm.shared.requests.request(v=vs.100%29.aspx) con las siguientes propiedades:

 Nombre| Descripción
-----|------------
 Comentario| Comentario que está asociado a la solicitud de MIM CM.
 Completed| Hora en que se completó la solicitud de MIM CM.
 DataCollection| Elementos de recopilación de datos que están asociados a la solicitud de MIM CM.
 DataCollectionFlags| Opciones de recopilación de datos para la solicitud de MIM CM.
 Flags| Opciones que están asociadas a la solicitud de MIM CM.
 IsDataCollectionComplete| Valor booleano que indica si se ha completado la recopilación de datos para la solicitud de MIM CM.
 IsEnrollmentAgent| Valor booleano que indica si se requiere un agente de inscripción para ejecutar la solicitud de MIM CM.
 IsSmartcard| Valor booleano que indica si la solicitud de MIM CM es una solicitud de tarjeta inteligente o una solicitud de perfil de software.
 NewProfileUuid| Identidad del nuevo perfil de software producido por la solicitud de MIM CM.
 NewSmartcardUuid| Identidad de la nueva tarjeta inteligente asignada por la solicitud de MIM CM.
 OldProfileUuid| Identidad del perfil de software para el que se creó la solicitud de MIM CM.
 OldSmartcardUuid| Identidad de la tarjeta inteligente para la que se creó la solicitud de MIM CM.
 OriginatorUserUuid| Identidad del usuario que originó la solicitud de MIM CM.
 Prioridad| Prioridad de la solicitud de MIM CM.
 ProfileTemplateUuid| Identidad de la plantilla de perfil para la que se creó la solicitud de MIM CM.
 RequestType| Tipo de la solicitud de MIM CM.
 SecurityDescriptor| Descriptor de seguridad para la solicitud de MIM CM.
 Estado| Estado de la solicitud de MIM CM.
 Submitted| Hora en que se envió la solicitud de MIM CM.
 TargetUserUuid| Identidad del usuario de destino para la solicitud de MIM CM.
 Uuid| Identificador de la solicitud de MIM CM.
## Ejemplo

### Solicitud 1

```
GET /certificatemanagement/api/v1.0/requests/a9b4b42c-cc50-4c9b-89d1-bbc0bcd5a099 HTTP/1.1
```
### Respuesta 1

```
HTTP/1.1 200 OK

{
    "Uuid":"a9b4b42c-cc50-4c9b-89d1-bbc0bcd5a099",
    "RequestType":1,
    "Status":3,
    "Flags":2,
    "DataCollection":[

    ],
    "DataCollectionFlags":32,
    "OriginatorUserUuid":"8f1590dc-d932-4b66-8e68-2e91c5880780",
    "TargetUserUuid":"8f1590dc-d932-4b66-8e68-2e91c5880780",
    "Submitted":"2015-07-07T23:36:21.93Z",
    "Completed":"0001-01-01T00:00:00",
    "NewProfileUuid":"00000000-0000-0000-0000-000000000000",
    "OldProfileUuid":"00000000-0000-0000-0000-000000000000",
    "NewSmartcardUuid":"00000000-0000-0000-0000-000000000000",
    "OldSmartcardUuid":"00000000-0000-0000-0000-000000000000",
    "Priority":0,
    "Comment":"",
    "ProfileTemplateUuid":"a039b4d0-5ce8-4eff-8651-181c6576fda3",
    "SecurityDescriptor":"O:S-1-5-21-2127521184-1604012920-1887927527-14134865D:(D;;LC;;;S-1-5-21-2127521184-1604012920-1887927527-14995557)(A;;DCSW;;;S-1-5-21-2127521184-1604012920-1887927527-5094533)(A;;DCSW;;;S-1-5-21-2127521184-1604012920-1887927527-5094534)(A;;DCSW;;;S-1-5-21-2127521184-1604012920-1887927527-5219125)(A;;SWRC;;;S-1-5-21-2127521184-1604012920-1887927527-5094533)(A;;RC;;;WD)(A;;CCDCLCSWSDRC;;;S-1-5-21-2127521184-1604012920-1887927527-14134865)(A;;DCSW;;;S-1-5-21-2127521184-1604012920-1887927527-14995557)(A;;CCDCSW;;;S-1-5-21-2127521184-1604012920-1887927527-14995557)\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000\u0000",
    "IsSmartcard":true,
    "IsEnrollmentAgent":false,
    "IsDataCollectionComplete":false
}```       
###Request 2
```
GET /certificatemanagement/api/v1.0/requests/0c96d73f-967b-420e-854a-43ad2a1504bc HTTP/1.1
```
###Response 2
```
HTTP/1.1 200 OK

{
"Uuid":"0c96d73f-967b-420e-854a-43ad2a1504bc",
"RequestType":5,
"Status":3,
"Flags":2,
"DataCollection":[
{
"Name":"Elemento de datos de ejemplo",
"Value":null
}
],
"DataCollectionFlags":32,
"OriginatorUserUuid":"8f1590dc-d932-4b66-8e68-2e91c5880780",
"TargetUserUuid":"8f1590dc-d932-4b66-8e68-2e91c5880780",
"Submitted":"2015-07-07T23:40:33.133Z",
"Completed":"0001-01-01T00:00:00",
"NewProfileUuid":"b99ff38c-6653-471f-ae3c-325bb351a6bc",
"OldProfileUuid":"b99ff38c-6653-471f-ae3c-325bb351a6bc",
"NewSmartcardUuid":"17cf063d-e337-4aa9-a822-346554ddd3c9",
"OldSmartcardUuid":"17cf063d-e337-4aa9-a822-346554ddd3c9",
"Priority":0,
"Comment":"",
"ProfileTemplateUuid":"a039b4d0-5ce8-4eff-8651-181c6576fda3",
"SecurityDescriptor":"O:S-1-5-21-2127521184-1604012920-1887927527-14134865D:(D;;LC;;;S-1-5-21-2127521184-1604012920-1887927527-14995557)(A;;SWRC;;;S-1-5-21-2127521184-1604012920-1887927527-5094533)(A;;RC;;;WD)(A;;CCDCLCSWSDRC;;;S-1-5-21-2127521184-1604012920-1887927527-14134865)(A;;DCSW;;;S-1-5-21-2127521184-1604012920-1887927527-14995557)(A;;CCDCSW;;;S-1-5-21-2127521184-1604012920-1887927527-14995557)\u0000\u0000\u0000\u0000\u0000\u0000",
"IsSmartcard":true,
"IsEnrollmentAgent":false,
"IsDataCollectionComplete":false
}
```

## Consulte también

- [Microsoft.Clm.Provision.FindOperations.FindRequest Method](http://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.clm.provision.findoperations.findrequests(v=vs.100%29.aspx)
- [Microsoft.Clm.Shared.RequestPermission Enumeration](http://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.clm.shared.requestpermission(v=vs.100%29.aspx)
- [Microsoft.Clm.Shared.Requests.Request Class](https://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.clm.shared.requests.request(v=vs.100%29.aspx)



