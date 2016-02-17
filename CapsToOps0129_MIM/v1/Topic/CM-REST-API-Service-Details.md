---
title: Detalles de servicio de la API de REST de CM
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 530047f1-e43b-4a69-9542-75bc1da57bf7
---
# Detalles de servicio de la API de REST de CM
En las siguientes secciones se describen los detalles de la API de REST de Certificate Management (CM) de Microsoft Identity Manager (MIM).

## En este tema

- [Arquitectura](#Architecture)
- [Encabezados de solicitud y respuesta HTTP](#HttpHeaders)
- [Control de versiones de la API](#Versioning)
- [Habilitar la API](#APIConfig)
- [Habilitar el seguimiento y el registro](#TracingConfig)
- [Control de errores y solución de problemas](#ErrorHandling)

<a name="Architecture"></a>
## Arquitectura

Las llamadas a la API de REST de CM de MIM se controlan mediante controladores. En la siguiente tabla se muestra la lista completa de controladores y ejemplos del contexto en el que pueden usarse.

 Controlador| Ruta de ejemplo
----------|-------------
 CertificateDataController| /api/v1.0/requests/{requestid}/certificatedata /
 CertificateRequestGenerationOptionsController| /api/v1.0/requests/{requestid}/certificaterequestgenerationoptions
 CertificatesController| /api/v1.0/smartcards/{smartcardid}/certificates <br/> /api/v1.0/profiles/{profileid}/certificates
 OperationsController| /api/v1.0/smartcards/{smartcardid}/operations <br/> /api/v1.0/profiles/{profileid}/operations
 PoliciesController| /api/v1.0/profiletemplates/{profiletemplateid}/policies/{id}
 ProfilesController| /api/v1.0/profiles/{id} <br/> /api/v1.0/Profiles <br/> /api/v1.0/requests/{requestid}/profiles/{id}
 ProfileTemplatesController| /api/v1.0/profiletemplates/{id} <br/> /api/v1.0/profiletemplates <br/> /api/v1.0/profiletemplates/{profiletemplateid}/policies/{id}
 RequestsController| /api/v1.0/requests/{id} <br/> /api/v1.0/requests
 SmartcardsController| /api/v1.0/requests/{requestid}/smartcards/{id}/diversifiedkey <br/> /api/v1.0/requests/{requestid}/smartcards/{id}/serverproposedpin <br/> /api/v1.0/requests/{requestid}/smartcards/{id}/authenticationresponse <br/> /api/v1.0/requests/{requestid}/smartcards/{id} <br/> /api/v1.0/smartcards/{id} <br/> /api/v1.0/smartcards
 SmartcardsConfigurationController| /api/v1.0/profiletemplates/{profiletemplateid}/configuration/smartcards
<br/>
<a name="HttpHeaders"></a>
## Encabezados de solicitud y respuesta HTTP

Las solicitudes HTTP enviadas a la API deben incluir los siguientes encabezados (esta lista no es exhaustiva):

 Encabezado| Descripción
-------|------------
 Autorización| Obligatorio.El contenido dependerá del método de autenticación, que es configurable y puede basarse en WIA (Autenticación integrada de Windows) o ADFS.
 Content-Type| Obligatorio si la solicitud tiene un cuerpo.Debe ser "application/json".
 Content-Length| Obligatorio si la solicitud tiene un cuerpo.
 Cookie| Cookie de la sesión.Puede ser obligatorio en función del método de autenticación.
<br/>
Las respuestas HTTP incluirán los siguientes encabezados (esta lista no es exhaustiva):

 Header| Descripción
-------|------------
 Content-Type| La API siempre devuelve "application/json".
 Content-Length| Longitud del cuerpo de la solicitud en bytes si es que está presente.
<a name="Versioning"></a>
## Control de versiones de la API

La versión actual de la API de REST de CM es 1.0. La versión se especifica en el segmento que se encuentra justo después del segmento `/api` del URI: `/api/v1.0`. Más adelante el número de la versión cambiará si se producen cambios importantes en la interfaz de la API.

<a name="APIConfig"></a>
## Habilitar la API

La sección `<ClmConfiguration>` del archivo Web.config se ha extendido con una clave nueva:

```
<add key="Clm.WebApi.Enabled" value="false" />
```
<br/>

Esta clave determina si la API de REST de CM se expone a los clientes. Si la clave se establece en "false", la asignación de ruta de la API no se realiza al iniciar la aplicación. Esto significa que todas las solicitudes realizadas posteriormente a los extremos de API devolverán un código de error HTTP 404. De forma predeterminada, la clave se establece en "disabled".
Después de cambiar este valor a "true", acuérdese de ejecutar **iisreset** en el servidor.

<a name="TracingConfig"></a>
## Habilitar el seguimiento y el registro

La API de REST de CM de MIM emite los datos de seguimiento de cada solicitud HTTP que se le envía. Puede establecer el nivel de detalle de la información de seguimiento emitida estableciendo el siguiente valor de configuración:

```
<add name="Microsoft.Clm.Web.API" value="0" />
```
<br/>
<a name="ErrorHandling"></a>
## Control de errores y solución de problemas

Cuando se producen excepciones al procesar una solicitud, la API de REST de CM de MIM devuelve un código de estado HTTP al cliente web. Si se trata de errores comunes, la API devuelve un código de estado HTTP adecuado y un código de error.

Las excepciones no controladas se convierten en `HttpResponseException` con el código de estado HTTP 500 ("Error interno") y se incluyen en el registro de eventos y en el archivo de seguimiento de CM de MIM. Cada excepción no controlada se incluye en el registro de eventos con un identificador de correlación correspondiente. El identificador de correlación también se envía al consumidor de la API en el mensaje de error. Para solucionar el error, un administrador puede buscar en el registro de eventos el identificador de correlación correspondiente y los detalles del error.

Por motivos de seguridad, los seguimientos de pila correspondientes a errores generados como resultado del consumo de la API de REST de CM de MIM no se envían de vuelta al cliente.




