---
title: Introducci&#243;n a administraci&#243;n de acceso con privilegios
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
ms.assetid: ebf516a1-0a1d-4f28-959b-8de4a8f5d4e1
---
# Introducci&#243;n a administraci&#243;n de acceso con privilegios

## En esta guía
Esta guía contiene instrucciones para mostrar el Administrador de identidades de Microsoft y las características de servicios de dominio de Active Directory para la administración de acceso con privilegios en la administración entre bosques.

## Contexto
En muchos ciberataques sofisticados contra empresas de todo el mundo, los atacantes centran su atención en obtener privilegios administrativos.  En concreto, pueden usar técnicas como "Pass-the-Hash", suplantación de identidad (phishing) dirigida y otras para obtener los derechos de acceso de un usuario que tenga privilegios administrativos en un dominio o un bosque.  Estos ataques ven agravados por el hecho de que muchos usuarios tienen privilegios de administrador permanentes asociados a su cuenta de Active Directory.  Si un atacante obtiene la cuenta de cualquiera de esos usuarios y, en consecuencia, puede iniciar sesión o ejecutar un programa suplantando a ese usuario, el atacante tendrá privilegios administrativos. Las organizaciones que se preocupan por la posibilidad de ataques internos y restringen el acceso subcontratando la TI, están también motivados para mejorar los controles o los usuarios con privilegios de acceso elevados.  El documento de prácticas recomendadas para proteger Active Directory resalta la necesidad de eliminar la pertenencia permanente a grupos con muchos privilegios e implementar controles para conceder la pertenencia temporal a grupos con privilegios cuando sea necesario. Esta guía muestra cómo conseguir estos controles con Windows Server Active Directory y Microsoft Identity Manager.

La arquitectura de la solución para la administración de acceso con privilegios (PAM) se basa en dos conceptos:

-   Mantener el control mediante la administración del acceso del usuario, no de sus credenciales, y aprovechar los grupos de Active Directory para proporcionar ese acceso.

-   Extraer y aislar las cuentas administrativas de los bosques de Active Directory existentes.

Esta solución se centra principalmente en las cuentas de dominio en las que un usuario final estará autenticado y autorizado para actuar como un administrador de aplicación o de roles de una colección concreta de sistemas, o en varios servicios que dependen de Kerberos (o ADFS) con grupos de seguridad alojados en Active Directory.  Esta guía de laboratorio de pruebas no pretende abarcar escenarios para cuentas de servicio, cuentas de administrador local, cuentas compartidas o entornos distintos de AD.

