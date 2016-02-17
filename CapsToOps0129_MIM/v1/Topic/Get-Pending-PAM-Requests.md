---
title: Obtener solicitudes pendientes de PAM
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 005dc8fd-d73e-4557-b485-5566f16537eb
---
# Obtener solicitudes pendientes de PAM
Lo usa una cuenta con privilegios para devolver una lista de solicitudes pendientes que necesitan aprobación.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `http://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /api/pamresources/pamrequeststoapprove
### Parámetros de consulta

 Parámetro| Descripción
----------|--------------
 $filter| Opcional.Especifique cualquiera de las propiedades de solicitud pendiente de PAM en una expresión de filtro para devolver una lista filtrada de respuestas.Para obtener más información sobre los operadores compatibles, consulte [Filtrado en Detalles de servicio de la API de REST de PAM](PAM-REST-API-Service-Details.md#Filtering).
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

Una respuesta correcta contiene una lista de objetos de aprobación de solicitudes de PAM con las siguientes propiedades.

 Propiedad| Descripción
---------|-------------
 RoleName| Nombre para mostrar del rol para el que se necesita aprobación.
 Solicitante| Nombre de usuario del solicitante que se debe aprobar.
 Justification| Justificación proporcionada por el usuario.
 RequestedTTL| Tiempo de expiración solicitado en segundos.
 RequestedTime| Tiempo solicitado para la elevación.
 CreationTime| Hora de creación de la solicitud.
 FIMRequestID| Contiene un único elemento, "Valor", con el identificador único (GUID) de la solicitud de PAM.
 RequestorID| Contiene un único elemento, "Valor", con el identificador único (GUID) para la cuenta de Active Directory que creó la solicitud de PAM.
 ApprovalObjectID| Contiene un único elemento, "Valor", con el identificador único (GUID) del Objeto de aprobación.
## Ejemplo

### Solicitud

```
GET /api/pamresources/pamrequeststoapprove HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

{
    "odata.metadata":"http://localhost:8086/api/pamresources/%24metadata#pamrequeststoapprove",
    "value":[
        {
            "RoleName":"ApprovalRole",
            "Requestor":"PRIV.Jen",
            "Justification":"Justification Reason",
            "RequestedTTL":"3600",
            "RequestedTime":"2015-07-11T22:25:00Z",
            "CreationTime":"2015-07-11T22:24:52.51Z",
            "FIMRequestID":{
                "Value":"9802d7b7-b4e9-4fe4-8f5c-649cda127e49"
            },
            "RequestorID":{
                "Value":"73257e5e-00b3-4309-a330-f1e607ff113a"
            },
            "ApprovalObjectID":{
                "Value":"5dbd9d0c-0a9d-4f75-8cbd-ff6ffdc00143"
            }
        }
    ]
}
```





