---
title: Implementar MIM
ms.custom: 
  - Identity Management
  - MIM
ms.prod: identity-manager-2015
ms.reviewer: na
ms.suite: na
ms.technology: 
  - security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa0af422-b5e9-4599-9d9b-cb6c18ea07f9
---
# Implementar MIM
Esta sección proporciona instrucciones paso a paso para implementar Microsoft Identity Manager 2016 en dos escenarios.

## Opciones de implementación de MIM 2016
Si es principiante y desea conocer mejor MIM, hay dos formas habituales de implementar una solución de MIM 2016, descritas ambas en esta sección:

-   Implementar el software MIM para escenarios de autoservicio de usuario final en un servidor nuevo en el que no se ha implementado FIM o MIM previamente

-   Actualizar un sistema de prueba existente de FIM 2010 R2 a MIM 2016

> [!NOTE]
> La topología de implementación descrita en esta sección está pensada solo para la iniciación y el aprendizaje de MIM.  La [guía de planificación de capacidad](https://technet.microsoft.com/en-us/library/ff400279%28v=ws.10%29.aspx) proporciona más información sobre topologías para implementaciones de producción.  Se recomienda revisar esa documentación antes de implementar MIM en un entorno o uso de producción.

El escenario de administración de acceso con privilegios se implementa de forma diferente que en los demás escenarios de MIM, ya que requiere un entorno de bosque bastión dedicado.  Si desea obtener más información acerca de la implementación de MIM para Privileged Identity Management, vea [Introducción a administración de acceso con privilegios](../Topic/Getting-Started-with-Privileged-Access-Management.md).

