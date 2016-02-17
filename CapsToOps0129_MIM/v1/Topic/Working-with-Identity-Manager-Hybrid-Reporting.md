---
title: Trabajar con la creaci&#243;n de informes h&#237;brida de Identity Manager
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
ms.assetid: 68df2817-2040-407d-b6d2-f46b9a9a3dbb
---
# Trabajar con la creaci&#243;n de informes h&#237;brida de Identity Manager
<?xml version="1.0" encoding="utf-8"?>
<caps:SxS xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
  <caps:SxSTarget locale="es-ES">
    <developerConceptualDocument xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xlink="http://www.w3.org/1999/xlink">
      <introduction></introduction>
      <section>
        <title>
          <caps:sentence sentenceid="b88f16bd65ba40727ce9ceaacb14c9d0" id="tgt1" class="tgtSentence">Informes híbridos disponibles</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence sentenceid="b8b2ab0a730b3cbc0c81fa403232ab16" id="tgt2" class="tgtSentence">Los primeros tres informes de Microsoft Identity Manager de Azure AD son <ui>Actividad de restablecimiento de contraseña</ui>, <ui>Registro para el restablecimiento de contraseña</ui> y <ui>Actividad de los grupos de autoservicio</ui>.</caps:sentence>
          </para>
          <list class="bullet">
            <listItem>
              <para>
                <caps:sentence sentenceid="cdd0691d1c77808e1720ce755aa50fdb" id="tgt3" class="tgtSentence">El informe de Actividad de restablecimiento de contraseña muestra cada instancia en la que un usuario restableció la contraseña mediante el autoservicio de restablecimiento de contraseña (SSPR) y proporciona las puertas o <ui>Métodos</ui> usados para la autenticación.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="ba5d10473d3447a9e638600f7ea7647d" id="tgt4" class="tgtSentence">El informe de Registro para el restablecimiento de contraseña muestra cada vez que un usuario se registra para el SSPR y los <ui>Métodos</ui> usados para la autenticación, como, por ejemplo, un número de teléfono móvil o preguntas y respuestas.</caps:sentence>
                <caps:sentence sentenceid="87c42ef2f89322700a40fa4b219d517a" id="tgt5" class="tgtSentence">
Tenga en cuenta que en el informe de Registro para el restablecimiento de contraseña no se diferencia entre la puerta SMS y la puerta MFA: las dos se consideran como <ui>Teléfono móvil</ui>.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="98ead5b2ce546d93e0aa1ca81840b5bb" id="tgt6" class="tgtSentence">El informe de Actividad de los grupos de autoservicio muestra cada vez que una persona ha intentado agregarse o eliminarse de un grupo y crear un grupo.</caps:sentence>
              </para>
              <mediaLink>
                <image xlink:href="735c6118-e996-4422-8375-b3710ee0e1e6"></image>
              </mediaLink>
            </listItem>
          </list>
          <alert class="note">
            <para>
              <caps:sentence sentenceid="dfae3408f7a6ad305090d2158e81812d" id="tgt7" class="tgtSentence">Los informes presentan actualmente datos de hasta un mes atrás.</caps:sentence>
            </para>
            <para>
              <caps:sentence sentenceid="925711814d9498faa85f5b073741805b" id="tgt8" class="tgtSentence">Si quiere desinstalar los informes híbridos, desinstale el agente MIMreportingAgent.msi.</caps:sentence>
            </para>
          </alert>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence sentenceid="b5b8e67d6a37d24ad73c89e4c7ac8c9e" id="tgt9" class="tgtSentence">Requisitos previos</caps:sentence>
        </title>
        <content>
          <list class="ordered">
            <listItem>
              <para>
                <caps:sentence sentenceid="e6f1d766faac900081c49c59a12bf65f" id="tgt10" class="tgtSentence">Instale Microsoft Identity Manager 2016 incluyendo el Servicio MIM.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="a4c27677c3492cc002b35b95429085cd" id="tgt11" class="tgtSentence">Asegúrese de que haya un inquilino de Azure AD Premium con un administrador con licencia en el directorio.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="e3216b34053889e289f41573a50ec92b" id="tgt12" class="tgtSentence">Asegúrese de tener conectividad a Internet saliente desde el servidor de Microsoft Identity Manager hasta Azure.</caps:sentence>
              </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence sentenceid="02842d1544feeabfcf491922408c02b0" id="tgt13" class="tgtSentence">Instalar Informes de Microsoft Identity Manager en Azure AD</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence sentenceid="a67aa0125bfa4039b643c964bf038e46" id="tgt14" class="tgtSentence">Una vez que se haya instalado el agente de informes, los datos de actividad de Microsoft Identity Manager se exportan desde Microsoft Identity Manager hasta el registro de eventos de Windows.</caps:sentence>
            <caps:sentence sentenceid="d92f99a22c15ad0d054ccfef25041882" id="tgt15" class="tgtSentence"> El agente de informes de Microsoft Identity Manager procesa los eventos y los carga en Azure.</caps:sentence>
            <caps:sentence sentenceid="214a2abc1d390de7c7b6e6ccb8c81081" id="tgt16" class="tgtSentence"> En Azure los eventos se analizan, descifran y filtran para los informes requeridos.</caps:sentence>
          </para>
          <list class="ordered">
            <listItem>
              <para>
                <caps:sentence sentenceid="8f3da1a4b22bb96c224d80449ac90035" id="tgt17" class="tgtSentence">Instale Microsoft Identity Manager 2016.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="bdb41f5bd2f7ca5bb937d955a6394674" id="tgt18" class="tgtSentence">Descargue los agentes de informes de Microsoft Identity Manager:</caps:sentence>
              </para>
              <list class="ordered">
                <listItem>
                  <para>
                    <caps:sentence sentenceid="cbaea5c81f78e6512d5940f101053af6" id="tgt19" class="tgtSentence">Inicie sesión en el portal de administración de Azure AD y haga clic en el icono de Active Directory.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="98ce0d9191fd32b4b2a00247b7ec6167" id="tgt20" class="tgtSentence">Haga doble clic en el directorio del que sea administrador global y para el que disponga de una suscripción de Azure AD Premium.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="6e1281216bd5ab5830f33b712fccf113" id="tgt21" class="tgtSentence">Haga clic en <ui>Configuración</ui> y descargue el agente de informes.</caps:sentence>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="53b1bdd8de6e1d33772f55e47ac10c30" id="tgt22" class="tgtSentence">Instale el agente de informes de Microsoft Identity Manager:
</caps:sentence>
              </para>
              <list class="ordered">
                <listItem>
                  <para>
                    <caps:sentence sentenceid="25b769d7e33c42ddde267cdc72faaa13" id="tgt23" class="tgtSentence">Cree un directorio en el equipo.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="d17cb97f63711006043e52a4879f0076" id="tgt24" class="tgtSentence">
Extraiga los archivos <codeInline>MIMHybridReportingAgent.msi</codeInline> y <codeInline>tenant.cert</codeInline> en el directorio.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="eeb2ffd895db10a8987fd640a80e32df" id="tgt25" class="tgtSentence">Ejecute el instalador del agente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="49b318bd12faa04b0c45a635eb94d2b8" id="tgt26" class="tgtSentence">Asegúrese de que se está ejecutando el servicio del agente de informes de Microsoft Identity Manager. 
</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="b12773f7b659ea4aaf17c5f5dbda211d" id="tgt27" class="tgtSentence">Reinicie el Servicio Microsoft Identity Manager.</caps:sentence>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="e32939d2e17f1834cf9cc69beb8dce8f" id="tgt28" class="tgtSentence">Compruebe que Informes de Microsoft Identity Manager funcione en Azure.</caps:sentence>
              </para>
              <para>
                <caps:sentence sentenceid="d44caa8a1f78e1c3985b160ebb959dd1" id="tgt29" class="tgtSentence">Puede crear datos de informes mediante el Portal de autoservicio de restablecimiento de contraseña de Microsoft Identity Manager para restablecer la contraseña de un usuario.</caps:sentence>
                <caps:sentence sentenceid="dfa7ce6337e5f9e0b180175c26239716" id="tgt30" class="tgtSentence"> Asegúrese de que el restablecimiento de la contraseña se completó correctamente y compruebe después que los datos se muestran en el portal de administración de Azure AD.</caps:sentence>
              </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence sentenceid="7250cc9c02de3df68bfec3c94bf4df80" id="tgt31" class="tgtSentence">Ver informes híbridos en el portal de administración de Azure</caps:sentence>
        </title>
        <content>
          <list class="ordered">
            <listItem>
              <para>
                <caps:sentence sentenceid="d05ca22d33e52f097ef3cd1749cb1491" id="tgt32" class="tgtSentence">Inicie sesión en Azure con su cuenta de administrador global para el inquilino.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="bc90cd6da1d1f78729cf8d3240dc19a9" id="tgt33" class="tgtSentence">Haga clic en el icono de <ui>Active Directory</ui>.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="a5e42a2c13e994e6963fa7792cff573e" id="tgt34" class="tgtSentence">Seleccione el directorio del inquilino de la lista de directorios disponibles para su suscripción.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="c3e52e1caddc93e6370fc2ce1a89de91" id="tgt35" class="tgtSentence">Haga clic en <ui>Informes</ui> y después en <ui>Actividad de restablecimiento de contraseña</ui>.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence sentenceid="b55ad8d923d43b23d1a45dc5839a472a" id="tgt36" class="tgtSentence">Asegúrese de seleccionar <ui>Identity Manager</ui> en el menú desplegable de origen.</caps:sentence>
              </para>
            </listItem>
          </list>
          <alert class="warning">
            <para>
              <caps:sentence sentenceid="07a4049d4e105f0bbc2c3b79d77ea6db" id="tgt37" class="tgtSentence">Puede que tarden un poco en mostrarse los datos de Microsoft Identity Manager en Azure AD.</caps:sentence>
            </para>
          </alert>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence sentenceid="7f61e3cd2a6f14d6c90d96dd16c8e536" id="tgt38" class="tgtSentence">Detener el envío de eventos de Microsoft Identity Manager a Azure</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence sentenceid="71778242c953b1afe3bb4170fbd1d848" id="tgt39" class="tgtSentence">Si quiere que se dejen de cargar datos de informes de Microsoft Identity Manager en Azure Active Directory, debe desinstalar al agente de informes híbridos.</caps:sentence>
            <caps:sentence sentenceid="8115380d9e121168a25ab9cadeae8754" id="tgt40" class="tgtSentence"> Mediante la herramienta <ui>Agregar o quitar programas</ui>, desinstale la herramienta de creación de informes híbrida de Identity Manager de Microsoft.</caps:sentence>
          </para>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence sentenceid="6be07d7d99bfcb18e0f36a57b3f65460" id="tgt41" class="tgtSentence">Eventos de Windows usados para Informes de Microsoft Identity Manager en Azure AD</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence sentenceid="853901da30ddd10396c86202813b8fa1" id="tgt42" class="tgtSentence">Los eventos que genera Microsoft Identity Manager se registran en el Registro de eventos de Windows y se pueden ver en el Visor de eventos en: Registros de aplicaciones y servicios-&gt;<legacyBold>Registro de solicitudes de Identity Manager</legacyBold>.</caps:sentence>
            <caps:sentence sentenceid="a0f3a2253771ef91ff0bb6f168d2390a" id="tgt43" class="tgtSentence"> Cada solicitud de Microsoft Identity Manager se exporta como un evento en el Registro de eventos de Windows en la estructura de JSON.</caps:sentence>
            <caps:sentence sentenceid="8669ead90420132fc1793187b5cae209" id="tgt44" class="tgtSentence"> Esto se puede exportar a su SIEM.</caps:sentence>
          </para>
          <table border="1">
            <thead>
              <tr>
                <TD>
                  <para>
                    <caps:sentence sentenceid="4ffebde418c1a6eef90be141993a39d0" id="tgt45" class="tgtSentence">Tipo de evento</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence sentenceid="b80bb7740288fda1f201890375a60c8f" id="tgt46" class="tgtSentence">ID</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence sentenceid="3b2b15b3f5458a210183d84462d6f894" id="tgt47" class="tgtSentence">Detalles del evento</caps:sentence>
                  </para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <caps:sentence sentenceid="bb3ccd5881d651448ded1dac904054ac" id="tgt48" class="tgtSentence">Información de</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence sentenceid="c79ec57a8e72a87d8a69d2c6b8a2a8d4" id="tgt49" class="tgtSentence">4121</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence sentenceid="2367f555f46eee5ee8c32a6e5d9d83a8" id="tgt50" class="tgtSentence">Datos de evento de FIM que incluyen todos los datos de solicitud.</caps:sentence>
                  </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <caps:sentence sentenceid="bb3ccd5881d651448ded1dac904054ac" id="tgt51" class="tgtSentence">Información de</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence sentenceid="6734fa703f6633ab896eecbdfad8953a" id="tgt52" class="tgtSentence">4137</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence sentenceid="939ff29be3d8d2595963f78ebe0fad95" id="tgt53" class="tgtSentence">Extensión 4121 de evento de FIM, en caso de que haya demasiados datos para un evento único.</caps:sentence>
                    <caps:sentence sentenceid="6a46763018ac18000585533c71f66bbd" id="tgt54" class="tgtSentence"> El encabezado de este evento tiene la siguiente forma:<codeInline>"Request: &lt;GUID&gt; , message &lt;xxx&gt; out of &lt;xxx&gt;</codeInline></caps:sentence>
                  </para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <relatedTopics></relatedTopics>
    </developerConceptualDocument>
  </caps:SxSTarget>
  <caps:SxSSource locale="en-US">
    <developerConceptualDocument xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xlink="http://www.w3.org/1999/xlink">
      <introduction></introduction>
      <section>
        <title>
          <caps:sentence id="src1" class="srcSentence">Available hybrid reports</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence id="src2" class="srcSentence">The first three Microsoft Identity Manager reports available in Azure AD are <ui>Password reset activity</ui>, <ui>Password reset registration</ui> and <ui>Self-service groups activity</ui>.</caps:sentence>
          </para>
          <list class="bullet">
            <listItem>
              <para>
                <caps:sentence id="src3" class="srcSentence">Password reset activity displays each instance when a user performed password reset using the SSPR and provides the gates or <ui>Methods</ui> used for authentication.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src4" class="srcSentence">Password reset registration displays each time a user registers for the SSPR and the <ui>Methods</ui> used to authenticate, for example a mobile phone number or questions and answers.</caps:sentence>
                <caps:sentence id="src5" class="srcSentence">
Note that for Password reset registration, no differentiation is made between SMS gate and MFA gate – both are considered <ui>Mobile Phone</ui>.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src6" class="srcSentence">Self-service groups activity displays each attempt made by someone to add themselves to or delete themselves from a group and group creation.</caps:sentence>
              </para>
              <mediaLink>
                <image xlink:href="735c6118-e996-4422-8375-b3710ee0e1e6"></image>
              </mediaLink>
            </listItem>
          </list>
          <alert class="note">
            <para>
              <caps:sentence id="src7" class="srcSentence">The reports currently present data for up to one month back.</caps:sentence>
            </para>
            <para>
              <caps:sentence id="src8" class="srcSentence">If you want to uninstall hybrid reports, uninstall the MIMreportingAgent.msi agent.</caps:sentence>
            </para>
          </alert>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence id="src9" class="srcSentence">Prerequisites</caps:sentence>
        </title>
        <content>
          <list class="ordered">
            <listItem>
              <para>
                <caps:sentence id="src10" class="srcSentence">Install Microsoft Identity Manager 2016 including the MIM service.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src11" class="srcSentence">Make sure you have an Azure AD Premium tenant with a licensed administrator in your directory.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src12" class="srcSentence">Make sure you have outgoing Internet connectivity from the Microsoft Identity Manager server to Azure.</caps:sentence>
              </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence id="src13" class="srcSentence">Installing Microsoft Identity Manager Reporting in Azure AD</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence id="src14" class="srcSentence">After the reporting agent is installed, the data from Microsoft Identity Manager activity is exported from Microsoft Identity Manager to windows event log.</caps:sentence>
            <caps:sentence id="src15" class="srcSentence"> The Microsoft Identity Manager reporting agent processes the events, and uploads to Azure.</caps:sentence>
            <caps:sentence id="src16" class="srcSentence"> In Azure, the events are parsed, decrypted, and filtered for the required reports.</caps:sentence>
          </para>
          <list class="ordered">
            <listItem>
              <para>
                <caps:sentence id="src17" class="srcSentence">Install Microsoft Identity Manager 2016.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src18" class="srcSentence">Download the Microsoft Identity Manager reporting agents:</caps:sentence>
              </para>
              <list class="ordered">
                <listItem>
                  <para>
                    <caps:sentence id="src19" class="srcSentence">Log into the Azure AD management portal and click on the Active Directory icon.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src20" class="srcSentence">Double click on the directory for which you are a Global Administrator and you have an Azure AD Premium subscription.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src21" class="srcSentence">Click <ui>Configuration</ui> and download the reporting agent.</caps:sentence>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src22" class="srcSentence">Install the Microsoft Identity Manager reporting agent:
</caps:sentence>
              </para>
              <list class="ordered">
                <listItem>
                  <para>
                    <caps:sentence id="src23" class="srcSentence">Create a directory on the computer.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src24" class="srcSentence">
Extract the files <codeInline>MIMHybridReportingAgent.msi</codeInline> and <codeInline>tenant.cert</codeInline> into the directory.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src25" class="srcSentence">Run the agent installer.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src26" class="srcSentence">Make sure that the Microsoft Identity Manager reporting agent service is running 
</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src27" class="srcSentence">Restart the Microsoft Identity Manager Service.</caps:sentence>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src28" class="srcSentence">Validate that Microsoft Identity Manager Reporting is working in Azure.</caps:sentence>
              </para>
              <para>
                <caps:sentence id="src29" class="srcSentence">You can create report data by using the Microsoft Identity Manager Self Service Password Reset Portal to reset a user’s password.</caps:sentence>
                <caps:sentence id="src30" class="srcSentence"> Make sure that the password reset completed successfully and then check that the data is displayed in the Azure AD management portal.</caps:sentence>
              </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence id="src31" class="srcSentence">Viewing hybrid reports in the Azure management portal</caps:sentence>
        </title>
        <content>
          <list class="ordered">
            <listItem>
              <para>
                <caps:sentence id="src32" class="srcSentence">Log into Azure with your global admin account for the tenant.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src33" class="srcSentence">Click the <ui>Active Directory</ui> icon.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src34" class="srcSentence">Select the tenant directory from the list of available directories for your subscription.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src35" class="srcSentence">Click <ui>Reports</ui> and then <ui>Password Reset Activity</ui>.</caps:sentence>
              </para>
            </listItem>
            <listItem>
              <para>
                <caps:sentence id="src36" class="srcSentence">Make sure you select <ui>Identity Manager</ui> in the source drop down menu.</caps:sentence>
              </para>
            </listItem>
          </list>
          <alert class="warning">
            <para>
              <caps:sentence id="src37" class="srcSentence">It can take some time for Microsoft Identity Manager data to appear in Azure AD.</caps:sentence>
            </para>
          </alert>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence id="src38" class="srcSentence">Stop sending Microsoft Identity Manager events to Azure</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence id="src39" class="srcSentence">If you want to stop uploading reporting data from Microsoft Identity Manager to Azure Active Directory, you should uninstall the hybrid reporting agent.</caps:sentence>
            <caps:sentence id="src40" class="srcSentence"> Using the Windows <ui>Add or Remove Programs </ui>tool, uninstall Microsoft Identity Manager Hybrid Reporting.</caps:sentence>
          </para>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence id="src41" class="srcSentence">Windows Events Used for Microsoft Identity Manager Reporting in Azure AD</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence id="src42" class="srcSentence">Events generated by Microsoft Identity Manager are logged in the Windows Event Log, and are visible in the Event Viewer under: Application and Services logs-&gt; <legacyBold>Identity Manager Request Log</legacyBold>.</caps:sentence>
            <caps:sentence id="src43" class="srcSentence"> Each Microsoft Identity Manager request is exported as an event in the Windows Event Log in JSON structure.</caps:sentence>
            <caps:sentence id="src44" class="srcSentence"> This can be exported to your SIEM.</caps:sentence>
          </para>
          <table border="1">
            <thead>
              <tr>
                <TD>
                  <para>
                    <caps:sentence id="src45" class="srcSentence">Event type</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence id="src46" class="srcSentence">ID</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence id="src47" class="srcSentence">Event details</caps:sentence>
                  </para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <caps:sentence id="src48" class="srcSentence">Information</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence id="src49" class="srcSentence">4121</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence id="src50" class="srcSentence">FIM event data that includes all the request data.</caps:sentence>
                  </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <caps:sentence id="src51" class="srcSentence">Information</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence id="src52" class="srcSentence">4137</caps:sentence>
                  </para>
                </TD>
                <TD>
                  <para>
                    <caps:sentence id="src53" class="srcSentence">FIM event 4121 extension, in the case there is too much data for a single event.</caps:sentence>
                    <caps:sentence id="src54" class="srcSentence"> The header in this event is in the following form: <codeInline>"Request: &lt;GUID&gt; , message &lt;xxx&gt; out of &lt;xxx&gt;</codeInline></caps:sentence>
                  </para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <relatedTopics></relatedTopics>
    </developerConceptualDocument>
  </caps:SxSSource>
</caps:SxS>