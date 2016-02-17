---
title: Obtener la directiva de flujo de trabajo
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: be636205-c1f0-457c-982e-e17478cf0889
---
# Obtener la directiva de flujo de trabajo
Obtiene la directiva de plantilla de perfil para el flujo de trabajo especificado. Estos datos se usan durante la creación de la solicitud. La directiva de flujo de trabajo especifica los datos que necesita el cliente para crear una solicitud. Estos datos pueden incluir: diversos elementos de recopilación de datos, comentarios de la solicitud y directiva de contraseña de un solo uso.

**Nota**: Las direcciones URL que se muestran en este tema están relacionadas con el nombre de host elegido durante la implementación de la API, como, por ejemplo: `https://api.contoso.com`.
## Solicitud

 Método| URL de solicitud
---------|---------
 GET| /CertificateManagement/api/v1.0/profiletemplates/{id}/policy/workflow/{tipo}
### Parámetros de URL

 Parámetro| Descripción
--------|-------------
 id| Obligatorio.GUID correspondiente a la plantilla de perfil de la que se va a extraer la directiva.
 tipo| Obligatorio.Tipo de directiva que se solicita.Los valores posibles son: *Enroll*, *Duplicate*, *OfflineUnblock*, *OnlineUpdate*, *Renew*, *Recover*, *RecoverOnBehalf*, *Reinstate*, *Retire*, *Revoke*, *TemporaryEnroll* y *Unblock*.
### Encabezados de solicitud

Para los encabezados de solicitud comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de la solicitud

ninguno

## Respuesta

### Códigos de respuesta

 Código| Descripción
---------|---------
 200| Aceptar
 403| prohibido
 204| Sin contenido
 500| Error interno
### Encabezados de respuesta

Para los encabezados de respuesta comunes, consulte [Encabezados de solicitud y respuesta HTTP](CM-REST-API-Service-Details.md#HttpHeaders) en *Detalles de servicio de la API de REST de CM*.
### Cuerpo de respuesta

Si se ejecuta correctamente, devuelve un objeto de directiva basado en [ProfileTemplatePolicy](https://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.clm.shared.profiletemplates.profiletemplatepolicy (v=vs.100%29.aspx). Como mínimo, el objeto de directiva contiene las propiedades de la tabla siguiente, pero puede contener propiedades adicionales según la directiva solicitada. Por ejemplo, una solicitud para una directiva de inscripción devolverá un objeto [EnrollPolicy](https://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.clm.shared.profiletemplates.enrollpolicy (v=vs.100%29.aspx). Para obtener más información, consulte la documentación para el objeto de directiva asociada al parámetro de {tipo} en la solicitud. La documentación para los distintos tipos de objetos de directiva se encuentra en la documentación [Microsoft.Clm.Shared.ProfileTemplates Namespace](https://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.clm.shared.profiletemplates (v=vs.100%29.aspx).

 Propiedad| Descripción
---------|------------
 ApprovalsNeeded| Número de aprobaciones necesarias para las solicitudes de FIM CM para la directiva.
 AuthorizedApprover| Descriptor de seguridad de los usuarios que tienen autorización para aprobar las solicitudes de FIM CM para la directiva.
 AuthorizedEnrollmentAgent| Descriptor de seguridad para los usuarios que pueden actuar como agentes de inscripción para la directiva.
 AuthorizedInitiator| Descriptor de seguridad para los usuarios que pueden iniciar solicitudes de FIM CM para la directiva.
 CollectComments| Valor booleano que indica si está habilitada la recopilación de comentarios para las solicitudes de FIM CM para la directiva.
 CollectRequestPriority| Valor booleano que indica si está habilitada la recopilación de prioridad para las solicitudes de FIM CM para la directiva.
 DefaultRequestPriority| Prioridad predeterminada para las solicitudes de FIM CM para la directiva.
 Documentos| Documentos de directivas que están configurados para la directiva.
 Habilitada| Valor booleano que indica si la directiva está habilitada.
 EnrollAgentRequired| Valor booleano que indica si se necesitan agentes de inscripción para las solicitudes de FIM CM para la directiva.
 OneTimePasswordPolicy| Obtiene la forma en que se distribuyen las contraseñas de un solo uso para las solicitudes de FIM CM para la directiva.
 Personalization| Opciones de personalización de tarjeta inteligente para la directiva.
 PolicyDataCollection| Elementos de recopilación de datos que están asociados a la directiva.
 SelfServiceEnabled| Valor booleano que indica si está habilitada la iniciación de autoservicio para las solicitudes de FIM CM para la directiva.
## Ejemplo

### Solicitud 1

```
GET /CertificateManagement/api/v1.0/profiletemplates/97CD65FA-AF4B-4587-9309-0DD6BFD8B4E1/policies/enroll HTTP/1.1
```
### Respuesta 1

```
HTTP/1.1 200 OK

... body coming soon
```
### Solicitud 2

```
GET /CertificateManagement/api/v1.0/profiletemplates/97CD65FA-AF4B-4587-9309-0DD6BFD8B4E1/policies/renew HTTP/1.1
```
### Respuesta 2

```
HTTP/1.1 200 OK

... body coming soon
```
## Consulte también

- [Microsoft.Clm.Shared.ProfileTemplates.ProfileTemplatePolicy Class](https://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.clm.shared.profiletemplates.profiletemplatepolicy(v=vs.100%29.aspx)
- [Microsoft.Clm.Shared.ProfileTemplates Namespace](https://msdn.microsoft.com/en-us/library/windows/desktop/microsoft.clm.shared.profiletemplates(v=vs.100%29.aspx)




