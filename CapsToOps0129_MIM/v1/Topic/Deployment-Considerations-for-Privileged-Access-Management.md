---
title: Consideraciones de implementaci&#243;n de Privileged Access Management
ms.custom: na
ms.prod: identity-manager-2015
ms.reviewer: na
ms.service: active-directory
ms.suite: na
ms.technology: 
  - active-directory-domain-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c8fc547-1e3d-464a-b8ef-6efb51bade28
---
# Consideraciones de implementaci&#243;n de Privileged Access Management
## Introducción

La solución para la externalización de las cuentas administrativas está compuesta por bosques paralelos: los bosques y dominios de Active Directory existentes de la organización y, al menos, un bosque nuevo dedicado para Privileged Access Management (PAM). Este bosque, creado específicamente para el escenario de PAM, tiene un dominio que acomodará cuentas y grupos con privilegios que son duplicados a partir de uno o varios dominios existentes.

Además de los equipos que brindan Servicios de dominio de Active Directory (AD DS) para este bosque dedicado de administración del acceso con privilegios, el entorno bastión también incluye equipos que hospedan Microsoft Identity Manager (MIM 2016), al igual que SQL Server y sus otras dependencias. Además, los equipos de estaciones de trabajo administrativas con privilegios (PAW) se pueden unir a este dominio.

Los temas de esta sección describen:

- [Modelo de niveles para el particionamiento de los privilegios administrativos](Tier-model-for-partitioning-administrative-privileges.md)
- [*Planificación de un entorno bastión*](Planning-a-bastion-environment.md)

- [*Definición de roles para Privileged Access Management*](Defining-roles-for-Privileged-Access-Management.md)

Después de revisar este contenido, si desea comenzar a implementar PAM inmediatamente en un laboratorio de pruebas, siga leyendo la sección [*Introducción a Privileged Access Management*](https://technet.microsoft.com/en-us/library/mt345568.aspx).

Después de la implementación, los artículos que aparecen en la sección [*Operaciones de Privileged Access Management*](https://technet.microsoft.com/en-US/library/mt561422.aspx) brindan más instrucciones sobre cómo configurar y administrar PAM.




