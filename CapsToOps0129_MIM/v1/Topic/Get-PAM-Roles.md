---
title: Obtener roles de PAM
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: d3c4f528-c3c8-41c1-905e-7eb84f074ce4
---
# Obtener roles de PAM
Usado por una cuenta con privilegios, enumera los roles de PAM para los que es candidata la cuenta.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `http://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /api/pamresources/pamroles
### Parámetros de consulta

 Parámetro| Descripción
----------|--------------
 $filter| Opcional.Especifique cualquiera de las propiedades de PAM Role en una expresión de filtro para devolver una lista filtrada de respuestas.Para obtener más información sobre los operadores compatibles, consulte [Filtrado en Detalles de servicio de la API de REST de PAM](PAM-REST-API-Service-Details.md#Filtering).
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

Una respuesta correcta contiene una colección de uno o varios roles de PAM, cada uno de los cuales tiene las siguientes propiedades.

 Propiedad| Descripción
--------|-------------
 RoleID| Identificador único (GUID) del rol de PAM.
 DisplayName| Nombre para mostrar del rol de PAM en el servicio MIM.
 Descripción| Descripción del rol de PAM en el servicio MIM.
 TTL| Tiempo de espera máximo, en segundos, para la caducidad de los derechos de acceso del rol.
 AvailableFrom| Primera hora del día en que se activará una solicitud.
 AvailableTo| Última hora del día en que se activará una solicitud.
 MFAEnabled| Valor booleano que indica si las solicitudes de activación para este rol requieren un desafío MFA.
 ApprovalEnabled| Valor booleano que indica si las solicitudes de activación para este rol requieren la aprobación de un propietario del rol.
 AvailibitlyWindowEnabled| Valor booleano que indica si el rol solo puede activarse durante un intervalo de tiempo especificado.
## Ejemplo

### Solicitud

```
GET /api/pamresources/pamroles HTTP/1.1
```
### Respuesta

```
HTTP/1.1 200 OK

{
    "odata.metadata":"http://localhost:8086/api/pamresources/%24metadata#pamroles",
    "value":[
        {
            "RoleId":"8f5cec1a-ecba-42ec-b76d-e6e0e4bf4c62",
            "DisplayName":"Allow AD Access ",
            "Description":null,
            "TTL":"3600",
            "AvailableFrom":"0001-01-01T00:00:00",
            "AvailableTo":"0001-01-01T00:00:00",
            "MFAEnabled":false,
            "ApprovalEnabled":false,
            "AvailabilityWindowEnabled":false
        },
        {
            "RoleId":"c28eab4a-95cf-4c08-a153-d5e8a9e660cd",
            "DisplayName":"ApprovalRole",
            "Description":null,
            "TTL":"3600",
            "AvailableFrom":"0001-01-01T00:00:00",
            "AvailableTo":"0001-01-01T00:00:00",
            "MFAEnabled":false,
            "ApprovalEnabled":true,
            "AvailabilityWindowEnabled":false
        }
    ]
}
```





