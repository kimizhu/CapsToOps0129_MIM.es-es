---
title: Crear solicitud
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 80fe0656-6fb2-400c-9ef8-5f62b61b2a1b
---
# Crear solicitud
Cree una solicitud de MIM CM.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 POST| /CertificateManagement/api/v1.0/requests
### Parámetros de URL

ninguno

### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de la solicitud

El cuerpo de la solicitud contiene las siguientes propiedades.

 Propiedad| Descripción
---------|-----------
 profiletemplateuuid| Obligatorio.GUID de la plantilla de perfil para el que el usuario está creando la solicitud.
 datacollection| Obligatorio.Recopilación de pares nombre-valor que representan los datos que debe proporcionar el inscrito.La recopilación de datos necesarios que deben proporcionarse se puede recuperar a partir de la directiva de flujo de trabajo de la plantilla de perfil.Se puede especificar una recopilación vacía.
 target| Opcional.GUID del usuario de destino para el que se va a crear la solicitud.Si no se especifica, el valor predeterminado es el usuario actual.
 tipo| Obligatorio.El tipo de solicitud que se está creando.Los tipos de solicitud disponibles son: "Enroll", "Duplicate", "OfflineUnblock", "OnlineUpdate", "Renew", "Recover", "RecoverOnBehalf", "Reinstate", "Retire", "Revoke", "TemporaryCards" y "Unblock".<br/>**Nota**: No todos los tipos de solicitud son compatibles con todas las plantillas de perfil.Por ejemplo, no puede especificar una operación de desbloqueo en una plantilla de perfil de software.
 comment| Obligatorio.Cualquier comentario que pueda escribir el usuario.La directiva de flujo de trabajo definirá si esto es necesario.Se puede especificar una cadena vacía.
 priority| Opcional.Prioridad de la solicitud.Si no se especifica, se usará la prioridad de solicitud predeterminada según lo determinado por la configuración de la plantilla de perfil.

## Respuesta

### Códigos de respuesta

 Código| Descripción
---------|---------
 201| Creado
 403| prohibido
 500| Error interno
### Encabezados de respuesta

Para los encabezados de respuesta comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de respuesta

Si se ejecuta correctamente, devuelve el URI de la solicitud recién creada.
## Ejemplo

### Solicitud 1

```
POST /CertificateManagement/api/v1.0/requests HTTP/1.1

{
    "datacollection":"[]",
    "type":"Enroll",
    "profiletemplateuuid":"a039b4d0-5ce8-4eff-8651-181c6576fda3",
    "comment":""
}
```
### Respuesta 1

```
HTTP/1.1 201 Created

"api/v1.0/requests/a9b4b42c-cc50-4c9b-89d1-bbc0bcd5a099"
```
### Solicitud 2

```
POST /CertificateManagement/api/v1.0/requests HTTP/1.1

{  
    "datacollection":"[]",
    "type":"Unblock",
    "smartcard":"17cf063d-e337-4aa9-a822-346554ddd3c9",
    "comment":""
}
```
### Respuesta 2

```
HTTP/1.1 201 Created

"api/v1.0/requests/0c96d73f-967b-420e-854a-43ad2a1504bc"
```

### Solicitud 3

```
POST /CertificateManagement/api/v1.0/requests HTTP/1.1

{
    "profiletemplateuuid" : "97CD65FA-AF4B-4587-9309-0DD6BFD8B4E1",
    "datacollection":
    [
        {"name" : "pavle"},
        {"city" : "seattle"}
    ],
    "target" : "97CC3493-F556-4C9B-9D8B-982434201527",
    "type" : "Enroll",
    "comment" : "LALALALA",
    "priority" :  "4"
}
```
## Consulte también

- [Microsoft.Clm.Provision.RequestOperations.InitiateEnroll Method](https://msdn.microsoft.com/es-es/library/windows/desktop/microsoft.clm.provision.requestoperations.initiateenroll(v=vs.100%29.aspx)
- [Microsoft.Clm.Provision.RequestOperations.InitiateOfflineUnblock Method](https://msdn.microsoft.com/es-es/library/windows/desktop/microsoft.clm.provision.requestoperations.initiateofflineunblock(v=vs.100%29.aspx)
- [Microsoft.Clm.Provision.RequestOperations.InitiateRecover Method](https://msdn.microsoft.com/es-es/library/windows/desktop/microsoft.clm.provision.requestoperations.initiaterecover(v=vs.100%29.aspx)
- [Microsoft.Clm.Provision.RequestOperations.InitiateRetire Method](https://msdn.microsoft.com/es-es/library/windows/desktop/microsoft.clm.provision.requestoperations.initiateretire(v=vs.100%29.aspx)
- [Microsoft.Clm.Provision.RequestOperations.InitiateUnblock Method](https://msdn.microsoft.com/es-es/library/windows/desktop/microsoft.clm.provision.requestoperations.initiateunblock(v=vs.100%29.aspx)




