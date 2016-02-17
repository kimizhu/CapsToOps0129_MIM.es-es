---
title: Detalles de servicio de la API de REST de PAM
ms.custom: 
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54c78bbd-8da1-42ff-9edc-47d913011941
---
# Detalles de servicio de la API de REST de PAM
En las siguientes secciones se describen los detalles de la API de REST de Privileged Access Management (PAM) de Microsoft Identity Manager (MIM).

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
## Control de versiones

La versión actual de la API es 1.
La versión de la API se puede especificar mediante un parámetro de consulta en la dirección URL de solicitud, como en el siguiente ejemplo: `http://localhost:8086/api/pamresources/pamrequests?v=1`.
Si no se especifica la versión de la solicitud, la solicitud se ejecuta en la última versión publicada de la API.

## Seguridad

El acceso a la API requiere Autenticación integrada de Windows (IWA). Esta debe configurarse manualmente en IIS antes de instalar Microsoft Identity Manager (MIM).

Se ofrece compatibilidad con HTTPS (TLS), pero debe configurarse manualmente en IIS. Para obtener información, consulte: **Implementar Capa de sockets seguros (SSL) para el portal de FIM** en [Step 9: Perform FIM 2010 R2 Post-Installation Tasks](https://technet.microsoft.com/en-us/library/hh322875(v=ws.10%29.aspx) en la guía de laboratorio de prueba para la instalación de FIM 2010 R2.

Puede generar un nuevo certificado de servidor SSL ejecutando el siguiente comando en el símbolo del sistema de Visual Studio:
```
Makecert -r -pe -n CN="test.cwap.com" -b 05/10/2014 -e 12/22/2048 -eku 1.3.6.1.5.5.7.3.1 -ss my -sr localmachine -sky exchange -sp "Microsoft RSA SChannel Cryptographic Provider" -sy 12
```

Este comando crea un certificado autofirmado que se puede usar para probar una aplicación web que use SSL en un servidor web cuya dirección URL sea test.cwap.com. El OID definido mediante la opción -eku identifica el certificado como certificado SSL de servidor. El certificado se almacena en el almacén y está disponible en el nivel de equipo, por lo que puede exportarlo desde el complemento Certificados en mmc.exe.

## Acceso entre dominios (CORS)

Se ofrece compatibilidad con CORS, pero debe configurarse manualmente en IIS. Agregue los siguientes elementos al archivo web.config de la API implementada para configurar la API para que permita las llamadas entre dominios:

```
<system.webServer>       
    <httpProtocol> 
        <customHeaders> 
            <add name="Access-Control-Allow-Credentials" value="true"  /> 
            <add name="Access-Control-Allow-Headers" value="content-type" /> 
            <add name="Access-Control-Allow-Origin" value="http://<hostname>:8090" /> 
        </customHeaders> 
    </httpProtocol> 
</system.webServer> 
```
<br/>
<a name="ErrorHandling"></a>
## Control de errores

La API devuelve respuestas de error HTTP para indicar condiciones de error. Los errores son compatibles con OData. La siguiente tabla muestra los códigos de error que se pueden devolver a un cliente.

 Código de estado HTTP| Descripción
-----------------|------------
 401| Sin autorización
 403| prohibido
 408| Tiempo de espera de solicitud
 500| error interno del servidor
 503| servicio no disponible
<br/>
<a name="Filtering"></a>
## Filtrado

Las solicitudes de la API de REST de PAM pueden incluir filtros para especificar las propiedades que deben incluirse en la respuesta. La sintaxis de filtro se basa en expresiones de OData.

Los filtros pueden especificar cualquiera de las propiedades de las solicitudes de PAM, de los roles de PAM o de las solicitudes pendientes de PAM. Por ejemplo: *ExpirationTime*, *DisplayName* o cualquier otra propiedad válida de una solicitud de PAM, rol de PAM o solicitud pendiente de PAM.

La API es compatible con los siguientes operadores en las expresiones de filtros: *And*, *Equal*, *NotEqual*, *GreaterThan*, *LessThan*, *GreaterThanOrEqual* y *LessThanOrEqual*.

Las siguientes solicitudes de ejemplo incluyen filtros:

- Esta solicitud devuelve todas las solicitudes de PAM entre fechas específicas: `http://localhost:8086/api/pamresources/pamrequests?$filter=ExpirationTime gt datetime"2015-01-09T08:26:49.721Z" and ExpirationTime lt datetime"2015-02-10T08:26:49.722Z" `

- Esta solicitud devuelve el rol de PAM con el nombre para mostrar "Acceso a archivo SQL": `http://localhost:8086/api/pamresources/pamroles?$filter=DisplayName eq "Acceso a archivo SQL" `




