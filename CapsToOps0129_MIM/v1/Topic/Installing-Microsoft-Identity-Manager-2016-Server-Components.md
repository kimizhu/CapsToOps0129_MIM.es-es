---
title: Instalar componentes de servidor de Microsoft Identity Manager 2016
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
ms.assetid: 901e3634-38b1-421e-a995-049e763c7672
---
# Instalar componentes de servidor de Microsoft Identity Manager 2016
<?xml version="1.0" encoding="utf-8"?>
<caps:SxS xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
  <caps:SxSTarget locale="es-ES">
    <developerConceptualDocument xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xlink="http://www.w3.org/1999/xlink">
      <introduction>
        <para></para>
      </introduction>
      <section>
        <title></title>
        <content>
          <para></para>
          <procedure>
            <title></title>
            <steps class="ordered">
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="3bd96fd3b5536262eb8e6d879e36bb0c" id="tgt1" class="tgtSentence">En el servidor corpidm que use para la administración de identidades, inicie sesión como <legacyItalic>contoso\Administrador</legacyItalic>.</caps:sentence>
                    <caps:sentence sentenceid="06c956efde4ae43dde912428995ef658" id="tgt2" class="tgtSentence"> Los derechos de administrador se usan para instalar <legacyBold>el Servicio de sincronización de MIM, el Servicio MIM y el Portal de MIM</legacyBold> en este entorno.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="27d43572c156f808aa171843b5603ca5" id="tgt3" class="tgtSentence">Desempaquete el paquete de instalación de MIM o monte el DVD con la imagen de MIM.</caps:sentence>
                  </para>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence sentenceid="70a1acee6b9218307eb4450b3fcbccc2" id="tgt4" class="tgtSentence">Instalar el Servicio de sincronización de MIM 2016</caps:sentence>
        </title>
        <content>
          <para></para>
          <procedure>
            <title></title>
            <steps class="ordered">
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="a8bb504d2ac94def7565c4255f193e37" id="tgt5" class="tgtSentence">En la carpeta de instalación de MIM, vaya a la carpeta <legacyBold>Synchronization Service</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="c0746126cc3abd381ac9590344710911" id="tgt6" class="tgtSentence">Ejecute el <legacyBold>instalador del servicio de sincronización de MIM</legacyBold>.</caps:sentence>
                    <caps:sentence sentenceid="d50cd0a6fec622e30a90d57fd11261ba" id="tgt7" class="tgtSentence"> Siga las instrucciones del instalador y complete la instalación.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="efa41ce0e6883f1c8bc0f9abe3c0f444" id="tgt8" class="tgtSentence">En la pantalla de bienvenida, haga clic en <legacyBold>Siguiente</legacyBold>.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="7fce56b4-c389-487b-92cf-86a4ef8e9015"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="ccd4a051e53ff17bcf47ed949b03ad4e" id="tgt9" class="tgtSentence">Revise los términos de licencia y si los acepta, haga clic en <legacyBold>Siguiente</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="3ee09419b32ef263f22cd67326ce5e9c" id="tgt10" class="tgtSentence">En la pantalla de selección de características, haga clic en <legacyBold>Siguiente</legacyBold>.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="cebd3544-d6f2-45d3-9fdb-129f8c5ad39b"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="bc7e5b4d511b6ba295196ae33191cb6b" id="tgt11" class="tgtSentence">En la pantalla de configuración de la base de datos de sincronización, seleccione:</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="d91eb8278fc5a728f85f4eca85b2f7e1" id="tgt12" class="tgtSentence">El SQL Server se encuentra en: <legacyBold>Este equipo</legacyBold>.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="6dd88bc9165bb9dc84d240e614253ea7" id="tgt13" class="tgtSentence">La instancia de SQL Server es: <legacyBold>La instancia predeterminada</legacyBold>.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="8847f245-3dce-4bd0-a561-a78ebc8c1bad"></image>
                      </mediaLink>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="6dddaabb42d6e842b60fc3245555e666" id="tgt14" class="tgtSentence">Configure la cuenta de Servicio de sincronización de acuerdo con la cuenta que creó anteriormente:</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="cdc3d9231ef4098f9094661d726af8a6" id="tgt15" class="tgtSentence">Cuenta de servicio: <legacyItalic>MIMSync</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="42378112f27339b64f9da9a7647ce557" id="tgt16" class="tgtSentence">Contraseña: <legacyItalic>Pass@word1</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="86798269b847ff00d68c8c73efc64a75" id="tgt17" class="tgtSentence">Dominio de la cuenta de servicio o nombre del equipo local: <legacyItalic>contoso</legacyItalic></caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="3efe7f1f-6b57-459c-b161-aa255d604c74"></image>
                      </mediaLink>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="389c089c0267d127537ecde11ae43dee" id="tgt18" class="tgtSentence">Proporcione al instalador del Servicio de sincronización de MIM los grupos de seguridad pertinentes:</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="c3b02f672c9a89dc1c2068f8d108c49c" id="tgt19" class="tgtSentence">Administrador = <legacyItalic>contoso\MIMSyncAdmins</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="e4f1975276a61da1019e5fa5a9468ab0" id="tgt20" class="tgtSentence">Operador= <legacyItalic>contoso\MIMSyncOperators</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="4ee8a7cccc480ed6b62e11bad9caad81" id="tgt21" class="tgtSentence">Objeto de unión = <legacyItalic>contoso\MIMSyncJoiners</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="5326a8cfa0eb692d44c8a35688dd1f1a" id="tgt22" class="tgtSentence">Cuadro de búsqueda de conector = <legacyItalic>contoso\MIMSyncBrowse</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="ac32908a450dba7fbae1b461f1a6d276" id="tgt23" class="tgtSentence">Administración de contraseñas de WMI = <legacyItalic>contoso\MIMSyncPasswordReset</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="5e948f17587957ae97b1ab677cacfcc7" id="tgt24" class="tgtSentence">En la pantalla de configuración de seguridad, active Habilitar reglas de firewall para las comunicaciones RPC entrantes y haga clic en <legacyBold>Siguiente</legacyBold>.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="98412dd2-9cb0-48dd-aa6b-75810c401a4d"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="83a2af8bedf6942da2aa7ceb1ffa01fd" id="tgt25" class="tgtSentence">Haga clic en <legacyBold>Instalar</legacyBold> para empezar la instalación del Servicio de sincronización de MIM.</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="ac98a9feca62221e0f85e3bc60772869" id="tgt26" class="tgtSentence">Puede que se muestre una advertencia relacionada con la cuenta del Servicio de sincronización de MIM. Si se muestra, haga clic en <legacyBold>Aceptar</legacyBold>.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="ce87edd4a289404b564572a532cb1a85" id="tgt27" class="tgtSentence">El Servicio de sincronización de MIM se instalará ahora.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="213ed09f-ae3a-4bc4-a45a-696b5cfcd165"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="1a9dedc98b2e17f4ae07e4963fa4b02f" id="tgt28" class="tgtSentence">Se mostrará un aviso sobre la creación de una copia de seguridad de la clave de cifrado. Haga clic en Aceptar y seleccione una carpeta para almacenar la copia de seguridad de la clave de cifrado.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="46ad2a92-20f5-4912-a9ed-0d4897846f18"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="3f3a960f6b7f755c63f340f550d9386e" id="tgt29" class="tgtSentence">Cuando el instalador complete la instalación correctamente, haga clic en <legacyBold>Finalizar</legacyBold>.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="3089e9b6-e243-420b-8d0d-b9d1ca4e34a3"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="23c02763b1f4167814f102415f0d3f3c" id="tgt30" class="tgtSentence">Se le pedirá que cierre la sesión y la vuelva a iniciar para que se apliquen los cambios de pertenencia a grupos.</caps:sentence>
                        <caps:sentence sentenceid="61df744af53a7b4b8ce9e4f47be51ae5" id="tgt31" class="tgtSentence"> Haga clic en <legacyBold>Sí</legacyBold> para cerrar la sesión.</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence sentenceid="fc1037d0d3014afc355998a3f4f15706" id="tgt32" class="tgtSentence">Instalar el Servicio y el Portal de MIM</caps:sentence>
        </title>
        <content>
          <para></para>
          <procedure>
            <title></title>
            <steps class="ordered">
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="c17d3fde0680ba5af895284281a21e84" id="tgt33" class="tgtSentence">Ejecute el <legacyBold>instalador del Servicio y el Portal de MIM</legacyBold> desde la subcarpeta desempaquetada <legacyBold>Service and Portal</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="05c882d7df681da5799eaa63102b5dd1" id="tgt34" class="tgtSentence">En la pantalla de bienvenida, haga clic en <legacyBold>Siguiente</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="68551b98c2b6a9d6591fedcefc828241" id="tgt35" class="tgtSentence">Lea los términos de licencia y si acepta los términos de licencia, haga clic en <legacyBold>Siguiente</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="f929bdd87157212b059e702caaeffc77" id="tgt36" class="tgtSentence">En la pantalla Programa para la mejora de la experiencia del usuario de MIM, haga clic en <legacyBold>Siguiente</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="0c12652a031719dacdd30181e8f131c5" id="tgt37" class="tgtSentence">Para esta implementación, al seleccionar las características del componente, es necesario incluir las características Servicio MIM (salvo para los Informes de MIM) y Portal de MIM.</caps:sentence>
                    <caps:sentence sentenceid="ef5582c46361bc7e421ddca89ce6b26b" id="tgt38" class="tgtSentence"> También puede seleccionar el Portal de restablecimiento de contraseña de MIM y el Portal de restablecimiento de contraseña de MIM.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="1ca33eb40edfd126dbec0a4aaa64c7f8" id="tgt39" class="tgtSentence">Al configurar los servicios comunes y la conexión a la base de datos de MIM, especifique "Crear una nueva base de datos".</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="5a2dd439-674d-43ae-ad84-8ad37cf7e973"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="7a299d5fd1b92d25229ca985c2c6dd5c" id="tgt40" class="tgtSentence">Al configurar una conexión de servidor de correo, establezca como servidor de correo su servidor Exchange.</caps:sentence>
                    <caps:sentence sentenceid="ea92295f8fb775d7755f4c38121e2cfc" id="tgt41" class="tgtSentence"> Si no tiene configurado un servidor de correo, especifique localhost como el nombre del servidor de correo y desactive las dos casillas superiores.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="dfc22772-a353-457e-b402-949c90d715ed"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="9460a74f6c9a7f690971957896e27e4a" id="tgt42" class="tgtSentence">Especifique que quiere generar un nuevo certificado autofirmado o seleccione el certificado correspondiente.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="64abbf3323e86f94b823c4bb4df4e82d" id="tgt43" class="tgtSentence">Especifique el nombre de la cuenta de servicio que se debe usar, como, por ejemplo, <legacyItalic>MIMService</legacyItalic> y la contraseña de la cuenta de servicio, como, por ejemplo, <legacyItalic>Pass@word1</legacyItalic> (la contraseña especificada anteriormente en el primer paso), el dominio de la cuenta de servicio, como puede ser contoso, y la cuenta de correo electrónico de servicio, como, por ejemplo, contoso.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="fbcbcc15-410b-4a2e-a65d-f8f6a8a46fe7"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="471a78841efaedf704207bcbdd7fe554" id="tgt44" class="tgtSentence">Tenga en cuenta que puede aparecer una advertencia que indique que la cuenta de servicio no es segura en su configuración actual.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="0cee5cf5231d02e51d3f22f141e4d2f1" id="tgt45" class="tgtSentence">Acepte los valores predeterminados para la ubicación del servidor de sincronización y especifique la cuenta del agente de administración de MIM como <legacyItalic>contoso\MIMsync</legacyItalic>.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="8596cfda-8058-421f-abb7-3769bf4399f7"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="ab196476ea348cae13f2f4e35324cf52" id="tgt46" class="tgtSentence">Especifique <legacyItalic>CorpIDM (nombre de este equipo)</legacyItalic> como dirección del servidor del Servicio MIM para el Portal de MIM.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="26bb67f11439345cd3bba7f425a83bd6" id="tgt47" class="tgtSentence">Especifique <legacyItalic>http://CorpIDM.contoso.local:82</legacyItalic> como la dirección URL de la colección de sitios de SharePoint.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="4eb74e38f0ee918a205414cacb161c1e" id="tgt48" class="tgtSentence">Especifique <legacyItalic>http://CorpIDM.contoso.local:8080</legacyItalic> como la dirección URL de registro de contraseñas.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="beda581058e0bcd1cf02886813bf6608" id="tgt49" class="tgtSentence">Especifique <legacyItalic>http://CorpIDM.contoso.local:8088</legacyItalic> como la dirección URL de restablecimiento de contraseñas.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="09a1b503f0cf6356cf6b9cee0c007a96" id="tgt50" class="tgtSentence">Seleccione la casilla para abrir los puertos 5725 y 5726 en el firewall y la casilla para conceder acceso al Portal de MIM a todos los usuarios autenticados.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="38ca94a9690cd36830ae49b96e4a5b04" id="tgt51" class="tgtSentence">En la pantalla de configuración del Portal de registro de contraseñas de MIM</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="c9d1b209f6c98e189aa2172b376e1ea8" id="tgt52" class="tgtSentence">Especifique <legacyItalic>contoso\MIMSSPR</legacyItalic> como el nombre de la cuenta de servicio para el registro de SSPR y <legacyItalic>Pass@word1</legacyItalic> como la contraseña.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="0ff8831f36f5ed3d0c60c1602e0d1790" id="tgt53" class="tgtSentence">Especifique CORPIDM como el nombre de host para el registro de contraseñas de MIM y establezca el puerto en <legacyBold>8080</legacyBold>.</caps:sentence>
                        <caps:sentence sentenceid="30a20e82989258606c3f3b9462eb1523" id="tgt54" class="tgtSentence"> Habilite la apertura del puerto en el firewall.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="c4b77ce2-61b6-4f56-9fcc-53097b5a272f"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="c7a948cdc78e8081754cf34c307f3a72" id="tgt55" class="tgtSentence">Se mostrará una advertencia, léala y haga clic en <legacyBold>Siguiente</legacyBold>.</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="358d8e7659c8c915fe5203ee953fe8a0" id="tgt56" class="tgtSentence">En la siguiente pantalla de configuración del Portal de registro de contraseñas de MIM, especifique <legacyItalic>http://CorpIDM.contoso.local</legacyItalic> como la dirección del servidor del Servicio MIM para el Portal de registro de contraseñas.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="df00b5adff79bc238351bd4d310395d5" id="tgt57" class="tgtSentence">En la pantalla de configuración del Portal de restablecimiento de contraseñas de MIM</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="24998b528f2effb733b1f6012c31c953" id="tgt58" class="tgtSentence">Especifique <legacyItalic>Domain\MIMSSPRService</legacyItalic> como el nombre de la cuenta de servicio para el registro de SSPR y <legacyItalic>Pass@word1</legacyItalic> como la contraseña.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="b9632b3e8387373d2bb0a0ae3d6af779" id="tgt59" class="tgtSentence">Especifique <legacyItalic>CorpIDname http://CorpIDname.domain.local</legacyItalic> como el nombre de host para el registro de contraseñas de MIM y <legacyBold>8088</legacyBold> como el puerto.</caps:sentence>
                        <caps:sentence sentenceid="30a20e82989258606c3f3b9462eb1523" id="tgt60" class="tgtSentence"> Habilite la apertura del puerto en el firewall.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="7f1735ac-058c-4fc0-b99e-dc7bf02a8bf4"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="c7a948cdc78e8081754cf34c307f3a72" id="tgt61" class="tgtSentence">Se mostrará una advertencia, léala y haga clic en <legacyBold>Siguiente</legacyBold>.</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="8ae7d5586272116efb1ad79871b4a2ff" id="tgt62" class="tgtSentence">En la siguiente pantalla de configuración del Portal de registro de contraseñas de MIM, especifique <legacyItalic>CorpIDname http://CorpIDname.domain.local</legacyItalic> como la dirección del servidor del Servicio MIM para el Portal de registro de contraseñas.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="005bd8b0c8e34e43af231e9489e6f404" id="tgt63" class="tgtSentence">Cuando estén listas todas las definiciones de preinstalación, haga clic en <legacyBold>Instalar</legacyBold> para empezar a instalar los componentes de <legacyBold>Servicio y Portal</legacyBold> seleccionados.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="a31e66b0-0c47-4c3b-840d-30fc521298e8"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence sentenceid="a8864887692f97a04be75c5c536e8451" id="tgt64" class="tgtSentence">Una vez finalizada la instalación, compruebe que el Portal de MIM esté activo.</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="4fe798c802fff7617edd9bf689b1eaf4" id="tgt65" class="tgtSentence">Inicie Internet Explorer y establezca una conexión con el Portal de MIM en <legacyItalic>http://corpidm.contoso.local:82/identitymanagement</legacyItalic>.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="a6ff94801134b73cb3b4cdd8e78353e6" id="tgt66" class="tgtSentence">Tenga en cuenta que puede haber un breve retraso la primera vez que se visite esta página.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="c8c6dc75281a3109705debbda1f37bde" id="tgt67" class="tgtSentence">Si fuese necesario, autentíquese como <legacyItalic>contoso\Administrador</legacyItalic> en Internet Explorer.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="624a9f0499dd3b265f0ab6c8029e41bd" id="tgt68" class="tgtSentence">En Internet Explorer, abra el cuadro de diálogo <legacyBold>Opciones de Internet</legacyBold>, vaya a la pestaña <legacyBold>Seguridad</legacyBold> y agregue el sitio a la zona <legacyBold>Intranet local</legacyBold> si todavía no está en ella.</caps:sentence>
                        <caps:sentence sentenceid="8cd193af6c41dc2d464b00c38b217496" id="tgt69" class="tgtSentence">  Cierre el cuadro de diálogo <legacyBold>Opciones de Internet</legacyBold>.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="caad7b8b96c4cb06edf87721562f0a23" id="tgt70" class="tgtSentence">Permita a los usuarios ver su propia entrada en MIM.</caps:sentence>
                      </para>
                      <list class="ordered">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="9dcdfc8ce2f15808f4ef1dfe7816be44" id="tgt71" class="tgtSentence">Mediante Internet Explorer, en <legacyBold>Portal de MIM</legacyBold>, haga clic en <legacyBold>Reglas de directiva de administración</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="6b69fa5e4c4efbaeb695e315311f9865" id="tgt72" class="tgtSentence">Busque la regla de directivas de administración:
</caps:sentence>
                          </para>
                          <para>
                            <caps:sentence sentenceid="06eeba256708207cff7466abb3182d0c" id="tgt73" class="tgtSentence">Administración de usuarios: Los usuarios pueden leer sus propios atributos.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="8c04d7704d9c8800354fa1c3505fad69" id="tgt74" class="tgtSentence">Seleccione esta regla de directiva de administración, desactive la opción La directiva está deshabilitada. </caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="ef56dc2f216f9b5205da28cfe55e33fb" id="tgt75" class="tgtSentence">Haga clic en <legacyBold>Aceptar</legacyBold> y después en <legacyBold>Guardar</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="44a5918613c5c5470fca8a3108e2bbd2" id="tgt76" class="tgtSentence">Compruebe que el firewall permita conexiones entrantes para el puerto TCP 5725 y 5726.</caps:sentence>
                      </para>
                      <list class="ordered">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="665526e7222f84e05cead6e697df8128" id="tgt77" class="tgtSentence">Inicie <legacyBold>Herramientas administrativas » Firewall de Windows</legacyBold> con <legacyBold>Seguridad avanzada</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="9cb87a2a1694b1eedba0d38f8ee1871a" id="tgt78" class="tgtSentence">Haga clic en <legacyBold>Reglas de entrada</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="eb4f9600108cc03272e55c8d53d817db" id="tgt79" class="tgtSentence">Compruebe que aparecen las dos reglas siguientes:</caps:sentence>
                          </para>
                          <list class="bullet">
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="25a38a7588679255cf152e9027cce3d2" id="tgt80" class="tgtSentence">Servicio Forefront Identity Manager (STS).</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="8ad698964cdeff2c0311352c5112e530" id="tgt81" class="tgtSentence">Servicio Forefront Identity Manager (Servicio web).</caps:sentence>
                              </para>
                            </listItem>
                          </list>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="c1cf80c4ae6f2cd135bfa0855a286d6e" id="tgt82" class="tgtSentence">Complete el asistente y cierre la aplicación <legacyBold>Firewall de Windows</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="e21123b994a1863e114b41bf9f3f9d85" id="tgt83" class="tgtSentence">Inicie el <legacyBold>Panel de control »</legacyBold> Red e Internet <legacyBold>»</legacyBold> Ver el estado y las tareas de red.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="28e9d6faf2b3761f3337d4edf3b7f838" id="tgt84" class="tgtSentence">Compruebe que se muestre una red activa como contoso.local como red de dominios.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="9e900d92e4fbb19696f316ac882733a1" id="tgt85" class="tgtSentence">Cierre el <legacyBold>Panel de control</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </listItem>
                  </list>
                </content>
              </step>
            </steps>
          </procedure>
          <alert class="note">
            <para>
              <caps:sentence sentenceid="0cf34fdc40d4c57bcc30bafb5c4d7eac" id="tgt86" class="tgtSentence">Opcional: Ahora puede instalar complementos y extensiones de MIM.</caps:sentence>
            </para>
          </alert>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence sentenceid="7d4d9ee368e93a7b7e1020c35eeffa8c" id="tgt87" class="tgtSentence">Configurar el Servicio de sincronización de MIM para sincronizar desde Active Directory al Servicio MIM</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence sentenceid="db973789b59b809b88375b08a7a4c03a" id="tgt88" class="tgtSentence">De forma predeterminada, el Servicio de sincronización de MIM no tiene ningún conector configurado.</caps:sentence>
            <caps:sentence sentenceid="31558ef2cdf429ca37518efcfd0f465c" id="tgt89" class="tgtSentence">   Un primer paso típico consiste en usar el Servicio de sincronización de MIM para rellenar la base de datos del Servicio FIM con cuentas de Active Directory existentes.</caps:sentence>
            <caps:sentence sentenceid="521d9996f7af81d3ea36a2adc68d235c" id="tgt90" class="tgtSentence">  Para ello, usará la aplicación del Servicio de sincronización de MIM.</caps:sentence>
          </para>
        </content>
        <sections>
          <section>
            <title>
              <caps:sentence sentenceid="612e1d5aea914f0859ff4b8f7ae4aaff" id="tgt91" class="tgtSentence">Crear el agente de administración (MA) de MIM</caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence sentenceid="cb15d1609e508d187c81bfaa6c864b43" id="tgt92" class="tgtSentence">El MA de MIM es un conector que conecta el Servicio de sincronización de MIM con el Servicio MIM.</caps:sentence>
                <caps:sentence sentenceid="a6f9d8380e60f68d96b8e7430735d9fc" id="tgt93" class="tgtSentence"> Para crear este conector, use el Asistente para crear el agente de administración.</caps:sentence>
              </para>
              <para>
                <caps:sentence sentenceid="c4f1ac7e743cbba53c73f29eba9835a2" id="tgt94" class="tgtSentence">Al configurar un agente de administración de MIM, debe especificar una cuenta de usuario.</caps:sentence>
                <caps:sentence sentenceid="18a474edea3a0908a63910ebe1e8d57e" id="tgt95" class="tgtSentence"> Este documento usa mimma como nombre para esta cuenta.</caps:sentence>
              </para>
              <alert class="caution">
                <para>
                  <caps:sentence sentenceid="26d92ec9380d4e30155c87a09778bb69" id="tgt96" class="tgtSentence">La cuenta que use para el agente de administración de MIM debe ser la misma que la que haya especificado durante la instalación del Servicio MIM.</caps:sentence>
                </para>
              </alert>
              <para>
                <caps:sentence sentenceid="16a0a981b53f0b0a25d08df0bd374ede" id="tgt97" class="tgtSentence">Para crear el MA de MIM</caps:sentence>
              </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <caps:sentence sentenceid="86b882e9cb02b369feb5da13c32fcb32" id="tgt98" class="tgtSentence">Abra el Synchronization Service Manager.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="bc96e33d4ecff1d5096d1abce358c874" id="tgt99" class="tgtSentence">Para abrir el Asistente para crear el agente de administración, haga clic en <ui>Crear</ui> en el menú Acciones.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="a09f2f4b2c1b5a6b85420eed74876b1e" id="tgt100" class="tgtSentence">En la página Crear agente de administración, proporcione la siguiente configuración y después haga clic en <ui>Siguiente</ui>.</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="8b8e61ad99ceae2c0a2b6012ada209c6" id="tgt101" class="tgtSentence">Agente de administración para: Agente de administración del Servicio FIM
</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="6bd6c9ae4862fdf4a8ba57faa44639e0" id="tgt102" class="tgtSentence">Nombre: MIMMA</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="2730ee382873e4fff4bc2c31a1950f80" id="tgt103" class="tgtSentence">En la página Conectar con base de datos, proporcione la siguiente configuración y después haga clic en Siguiente.</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="5c3e0df9feae347da35becba4eafd7c9" id="tgt104" class="tgtSentence">Servidor: localhost</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="12d100775799e94e52f269767e6216ac" id="tgt105" class="tgtSentence">Base de datos: FIMService</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="e46d7151c4cf752649e694ec2c4ca7f8" id="tgt106" class="tgtSentence">Dirección base del Servicio FIM: http://localhost:5725</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="78e2cb94fd23f8e383ee861c0a1a62ce" id="tgt107" class="tgtSentence">Modo de autenticación: Autenticación integrada de Windows</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="d94948fa457953187473edfe454c84fe" id="tgt108" class="tgtSentence">Nombre de usuario: mimma
</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="900725ea1ccd47e6a25512a23e32dc6e" id="tgt109" class="tgtSentence">Contraseña: Pass@word</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="6572acfc2cd134e262b66e6ba7eefa4d" id="tgt110" class="tgtSentence">	Dominio: contoso</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="225bb02c17bf00d46111c9a0b3fd87ae" id="tgt111" class="tgtSentence">
En la página Tipos de objetos seleccionados, compruebe que estén seleccionados los tipos de objeto que se enumeran debajo y después haga clic en Siguiente.</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="01488bccaf0f5e1dd5d43e0c6609d5a1" id="tgt112" class="tgtSentence">	ExpectedRuleEntry</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="551e5b6c3352e8ef855a1e05e1e62ffb" id="tgt113" class="tgtSentence">DetectedRuleEntry</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="436c74569484b85cdeeb3484f8c17cfe" id="tgt114" class="tgtSentence">SynchronizationRule</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="8b0a44048f58988b486bdd0d245b22a8" id="tgt115" class="tgtSentence">Person</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="db0f6f37ebeb6ea09489124345af2a45" id="tgt116" class="tgtSentence">Grupo</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="f1d4ec3205f0290bba8d93ce19ad4c40" id="tgt117" class="tgtSentence">En la página Atributos seleccionados, compruebe que estén seleccionados todos los atributos enumerados y después haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="36cc4cae2907dbbdf485050850703d83" id="tgt118" class="tgtSentence">	En la página Configurar filtro de conector haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="1e3f0baf3f61a6999e6864c1e181bd5c" id="tgt119" class="tgtSentence">En la página Configurar asignaciones de tipo de objeto, agregue la siguiente asignación y después haga clic en Siguiente.</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="7fea6c4d94061384c59426b951f8e374" id="tgt120" class="tgtSentence">En la lista Tipo de objeto de Origen de datos, seleccione Person.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="84f00f14bbe57074c14fcd11c938525b" id="tgt121" class="tgtSentence">Para abrir el cuadro de diálogo Asignación, haga clic en Agregar asignación.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="088345f94b22814d036f889219c7a39e" id="tgt122" class="tgtSentence">En la lista de tipo de objeto Metaverso, seleccione person.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="747bd22c97d3a0a8c868629c4eaeb41a" id="tgt123" class="tgtSentence">Para cerrar el cuadro de diálogo Asignación, haga clic en Aceptar.</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="aaf16a48fe68d44ef7f3efd20bb12cf9" id="tgt124" class="tgtSentence">En la página Configurar el flujo de atributos, aplique las siguientes asignaciones de flujo de atributos y luego haga clic en Siguiente.</caps:sentence>
                  </para>
                  <table border="1">
                    <tbody>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="8e935af484b0207b12c939af49affeba" id="tgt125" class="tgtSentence">Dirección del flujo</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="407605cf3dffdd20f5f702bb43b30a9f" id="tgt126" class="tgtSentence">Atributo de origen de datos</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="9c42212ffcc9cfa74b59315eb9dd7295" id="tgt127" class="tgtSentence">Atributo de metaverso</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt128" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt129" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="375dcd3c9efd582a7c09a2a694dee321" id="tgt130" class="tgtSentence">accountName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt131" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt132" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93c731f1c3a84ef05cd54d044c379eaa" id="tgt133" class="tgtSentence">company</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt134" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt135" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="8d38cbc95c2cfb65c3ae913d1b1410b1" id="tgt136" class="tgtSentence">displayName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt137" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt138" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="0b8b667e7722bc7e363b601ce584259d" id="tgt139" class="tgtSentence">employeeID</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt140" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt141" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="cd2d171d7836aa13e1f51444e201ea79" id="tgt142" class="tgtSentence">employeeType</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt143" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt144" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="342f5c77ed008542e78094607ce1f7f3" id="tgt145" class="tgtSentence">firstName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt146" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt147" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="8ad75c5a8821cc294f189181722acb56" id="tgt148" class="tgtSentence">lastName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt149" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt150" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="1d0258c2440a8d19e716292b231e3190" id="tgt151" class="tgtSentence">Manager</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt152" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93473a7344419b15c4219cc2b6c64c6f" id="tgt153" class="tgtSentence">Importe</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="6381c8768508bc58d1e5d1539f373995" id="tgt154" class="tgtSentence">objectSid</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt155" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt156" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="375dcd3c9efd582a7c09a2a694dee321" id="tgt157" class="tgtSentence">accountName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt158" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt159" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="93c731f1c3a84ef05cd54d044c379eaa" id="tgt160" class="tgtSentence">company</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt161" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt162" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="8d38cbc95c2cfb65c3ae913d1b1410b1" id="tgt163" class="tgtSentence">displayName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt164" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt165" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="ad5f82e879a9c5d6b5b442eb37e50551" id="tgt166" class="tgtSentence">dominio</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt167" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt168" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="0b8b667e7722bc7e363b601ce584259d" id="tgt169" class="tgtSentence">employeeID</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt170" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt171" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="cd2d171d7836aa13e1f51444e201ea79" id="tgt172" class="tgtSentence">employeeType</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt173" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt174" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="342f5c77ed008542e78094607ce1f7f3" id="tgt175" class="tgtSentence">firstName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt176" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt177" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="8ad75c5a8821cc294f189181722acb56" id="tgt178" class="tgtSentence">lastName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt179" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt180" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="1d0258c2440a8d19e716292b231e3190" id="tgt181" class="tgtSentence">manager</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt182" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt183" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="6381c8768508bc58d1e5d1539f373995" id="tgt184" class="tgtSentence">objectSid</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="238a03d243f0acf9c67a8c4995e409d7" id="tgt185" class="tgtSentence">	Seleccione Person como tipo de objeto de Origen de datos.</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="fc4dd62ee4d8df18e847725cb4f345c3" id="tgt186" class="tgtSentence">Seleccione person como tipo de objeto de Metaverso.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="116fa65661f97e75452783c707ed717c" id="tgt187" class="tgtSentence">Seleccione Directo como el Tipo de asignación.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="fb5ded03845252907c76b918496b6549" id="tgt188" class="tgtSentence">Por cada fila de la tabla anterior, realice los siguientes pasos:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="4b50f2a0a6de121bdba7e48314982edb" id="tgt189" class="tgtSentence">Seleccione la Dirección del flujo que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="b6134c5af590e74cc092381eee757dcd" id="tgt190" class="tgtSentence">Seleccione el atributo Origen de datos que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="6a0b10ecc4b4717020c6fc39b0806046" id="tgt191" class="tgtSentence">Seleccione el atributo metaverso que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="9a4ba562796fb46f62a9062bdda9e071" id="tgt192" class="tgtSentence">Para aplicar la asignación de flujo, haga clic en Nuevo.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="34b187d6b4fe94802434d0c40a16ab02" id="tgt193" class="tgtSentence">Seleccione Group como el tipo de origen de datos y como el tipo de objeto de Metaverso.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="116fa65661f97e75452783c707ed717c" id="tgt194" class="tgtSentence">Seleccione Directo como el Tipo de asignación.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="6e252907ddb401229005c97ee5e95a26" id="tgt195" class="tgtSentence">Por cada fila de la siguiente tabla, realice los siguientes pasos:
</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="4b50f2a0a6de121bdba7e48314982edb" id="tgt196" class="tgtSentence">Seleccione la Dirección del flujo que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="b6134c5af590e74cc092381eee757dcd" id="tgt197" class="tgtSentence">Seleccione el atributo Origen de datos que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="6a0b10ecc4b4717020c6fc39b0806046" id="tgt198" class="tgtSentence">Seleccione el atributo metaverso que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="9a4ba562796fb46f62a9062bdda9e071" id="tgt199" class="tgtSentence">Para aplicar la asignación de flujo, haga clic en Nuevo.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </listItem>
                  </list>
                  <table border="1">
                    <tbody>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="8e935af484b0207b12c939af49affeba" id="tgt200" class="tgtSentence">Dirección del flujo</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="407605cf3dffdd20f5f702bb43b30a9f" id="tgt201" class="tgtSentence">Atributo de origen de datos</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="9c42212ffcc9cfa74b59315eb9dd7295" id="tgt202" class="tgtSentence">Atributo de metaverso</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt203" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="375dcd3c9efd582a7c09a2a694dee321" id="tgt204" class="tgtSentence">AccountName</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="375dcd3c9efd582a7c09a2a694dee321" id="tgt205" class="tgtSentence">accountName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt206" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="8d38cbc95c2cfb65c3ae913d1b1410b1" id="tgt207" class="tgtSentence">DisplayName</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="8d38cbc95c2cfb65c3ae913d1b1410b1" id="tgt208" class="tgtSentence">displayName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt209" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="ad5f82e879a9c5d6b5b442eb37e50551" id="tgt210" class="tgtSentence">Dominio</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="ad5f82e879a9c5d6b5b442eb37e50551" id="tgt211" class="tgtSentence">dominio</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt212" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="31a1fd140be4bef2d11e121ec9a18a58" id="tgt213" class="tgtSentence">Ámbito</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="31a1fd140be4bef2d11e121ec9a18a58" id="tgt214" class="tgtSentence">scope</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt215" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="599dcce2998a6b40b1e38e8c6006cb0a" id="tgt216" class="tgtSentence">Tipo</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="599dcce2998a6b40b1e38e8c6006cb0a" id="tgt217" class="tgtSentence">tipo</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt218" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="aa08769cdcb26674c6706093503ff0a3" id="tgt219" class="tgtSentence">Miembro</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="aa08769cdcb26674c6706093503ff0a3" id="tgt220" class="tgtSentence">miembro</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt221" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="bcd2970d595b4cf6da2b0bb8d830f596" id="tgt222" class="tgtSentence">MembershipLocked</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="bcd2970d595b4cf6da2b0bb8d830f596" id="tgt223" class="tgtSentence">membershipLocked</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt224" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="2b2c7e505c4e0acdfeb0b9465f1b3efb" id="tgt225" class="tgtSentence">MembershipAddWorkflow</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="2b2c7e505c4e0acdfeb0b9465f1b3efb" id="tgt226" class="tgtSentence">membershipAddWorkflow</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt227" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="1d0258c2440a8d19e716292b231e3190" id="tgt228" class="tgtSentence">Manager</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence sentenceid="1d0258c2440a8d19e716292b231e3190" id="tgt229" class="tgtSentence">manager</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="3f5270c57907dd45fcb77fbd6859650d" id="tgt230" class="tgtSentence">En la página Configurar el desaprovisionamiento, haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="5439a0a52cd7c0b4b67e2723a5119342" id="tgt231" class="tgtSentence">Para crear al agente de administración, haga clic en Finalizar en la página Configurar extensiones.</caps:sentence>
                  </para>
                </listItem>
              </list>
            </content>
          </section>
          <section>
            <title>
              <caps:sentence sentenceid="7a0d486f45e892d68cd3644812fa722e" id="tgt232" class="tgtSentence">Crear el agente de administración (MA) de AD </caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence sentenceid="3acbbc29ac649c37a0b51753c8a8cf82" id="tgt233" class="tgtSentence">El MA de Active Directory (AD) es un conector para AD DS.</caps:sentence>
                <caps:sentence sentenceid="a6f9d8380e60f68d96b8e7430735d9fc" id="tgt234" class="tgtSentence"> Para crear este conector, use el Asistente para crear el agente de administración.</caps:sentence>
              </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <caps:sentence sentenceid="797f58fc5dc31be12af3cea77ee055e8" id="tgt235" class="tgtSentence">Para abrir el Asistente para crear el agente de administración, haga clic en Crear en el menú Acciones.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="33dd18b8c7acc13a3a4dba457eddb54b" id="tgt236" class="tgtSentence">En la página Crear agente de administración, proporcione la siguiente configuración y después haga clic en Siguiente:</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="5161bebce818ab249ece791e104f9f08" id="tgt237" class="tgtSentence">Agente de administración para: Servicios de dominio de Active Directory</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="abd86c4037b6c59ad3adbfc321bf4d0d" id="tgt238" class="tgtSentence">Nombre: ADMA
</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="fc6423ec78f842c5a1f8fc3d379b3375" id="tgt239" class="tgtSentence">En la página Conectar con el bosque de Active Directory, proporcione la siguiente configuración y después haga clic en Siguiente:
</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="914982970d30b7afed1b6fbb2754896e" id="tgt240" class="tgtSentence">	Nombre de bosque: contoso.local
</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="47ca0c705c28b872e24778a18d7a2019" id="tgt241" class="tgtSentence">Nombre de usuario: administrador
</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="2c7abb99871d685f1531addbd2c11471" id="tgt242" class="tgtSentence">Contraseña: &lt;la contraseña de la cuenta&gt;</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="7c7a9cde48aac77972745828406dd060" id="tgt243" class="tgtSentence">Dominio: contoso
</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="f1a1d46fd3d28a84c0afc9ad912f0d1e" id="tgt244" class="tgtSentence">En la página Configurar particiones de directorio, proporcione la siguiente configuración y después haga clic en Siguiente:
</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="dd1d96c4e59c78a202259b17d670dea9" id="tgt245" class="tgtSentence">En la lista Seleccionar particiones de directorio, seleccione DC=CONTOSO, DC=local.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="f0e25b269256051ebeda139f2a38ea29" id="tgt246" class="tgtSentence">Para abrir el cuadro de diálogo Seleccionar contenedores, haga clic en Contenedores.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="3c47c79db4d7ff551e6afabf2bb49427" id="tgt247" class="tgtSentence">Si quiere cambiar el contenedor para que solo MIM administre los objetos de un determinado contenedor, haga clic en DC=CONTOSO, DC=nodo local y después haga clic en el nodo del contenedor en cuestión.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="b1c07ce8110fee89c7fb6b2158c5f17d" id="tgt248" class="tgtSentence">Para cerrar el cuadro de diálogo Seleccionar contenedores, haga clic en Aceptar.</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="241eeef67497498c22bf78828bd4bcb8" id="tgt249" class="tgtSentence">En la página Configurar jerarquía de aprovisionamiento, haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="e9aeea813b9db11a3db622722ebb7f0b" id="tgt250" class="tgtSentence">En la página Seleccionar tipos de objeto, proporcione la siguiente configuración y después haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="b51c4a5d4aaa7abd80a0d181fbdc524b" id="tgt251" class="tgtSentence">En la lista Tipos de objeto, seleccione el usuario y el grupo.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="3950a83d76a01cf853622f1c803297e4" id="tgt252" class="tgtSentence">En la página Seleccionar atributos, proporcione la siguiente configuración y después haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="846b68337fa1d3a15b20c2ba71eeb3ae" id="tgt253" class="tgtSentence">Seleccione Mostrar todos.</caps:sentence>
                  </para>
                  <para>
                    <caps:sentence sentenceid="b329b74a3981596bd45661c0b79dc64a" id="tgt254" class="tgtSentence">En la lista Atributos, seleccione los siguientes atributos:</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="93c731f1c3a84ef05cd54d044c379eaa" id="tgt255" class="tgtSentence">company</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="8d38cbc95c2cfb65c3ae913d1b1410b1" id="tgt256" class="tgtSentence">displayName</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="0b8b667e7722bc7e363b601ce584259d" id="tgt257" class="tgtSentence">employeeID</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="cd2d171d7836aa13e1f51444e201ea79" id="tgt258" class="tgtSentence">employeeType</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="6ce8ba046cf55cca086ac00e80859815" id="tgt259" class="tgtSentence">givenName</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="7ad4509a0ac176b0eaf3f02326510e42" id="tgt260" class="tgtSentence">groupType</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="1d0258c2440a8d19e716292b231e3190" id="tgt261" class="tgtSentence">manager</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="cb2ef9b975c7016e9949d60973928387" id="tgt262" class="tgtSentence">managedBy</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="aa08769cdcb26674c6706093503ff0a3" id="tgt263" class="tgtSentence">miembro</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="6381c8768508bc58d1e5d1539f373995" id="tgt264" class="tgtSentence">objectSid</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="7f5ac5ed292277dd0f8367d612bbe974" id="tgt265" class="tgtSentence">sAMAccountName</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="0b3f37af195dd7b8cad31591b247908f" id="tgt266" class="tgtSentence">sAMAccountType</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="afbe94cdbe69a93efabc9f1325fc7dff" id="tgt267" class="tgtSentence">sn</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="e82cfaad3eed4950aef716ff044e2aaa" id="tgt268" class="tgtSentence">unicodePwd</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="4a550062a78fd30120ca083bf8a4292a" id="tgt269" class="tgtSentence">userAccountControl</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="36cc4cae2907dbbdf485050850703d83" id="tgt270" class="tgtSentence">	En la página Configurar filtro de conector haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="ed944f77030b537cab58a0cfdac059eb" id="tgt271" class="tgtSentence">En la página Configurar reglas de unión y proyección, haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="b2ec640bf82892f45840fc04383af315" id="tgt272" class="tgtSentence">En la página Configurar el flujo de atributos, haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="270c26afbb23afca523bbe4b86556344" id="tgt273" class="tgtSentence">	En la página Configurar el desaprovisionamiento, haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="6b4fba7c232df1abe2a62d52f8e8b1aa" id="tgt274" class="tgtSentence">En la página Configurar extensiones, haga clic en Siguiente.</caps:sentence>
                  </para>
                </listItem>
              </list>
            </content>
          </section>
          <section>
            <title>
              <caps:sentence sentenceid="2e291238acdb43ed80f83e236c5cef2a" id="tgt275" class="tgtSentence">Crear perfiles de ejecución</caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence sentenceid="e080a0467ab9452717d4a0071c90f6a3" id="tgt276" class="tgtSentence">Cree perfiles de ejecución para los conectores ADMA y MIMMA.</caps:sentence>
              </para>
            </content>
            <sections>
              <section>
                <title>
                  <caps:sentence sentenceid="c0c151f48a96ea48d5625da372ff6808" id="tgt277" class="tgtSentence">Crear perfiles de ejecución para el conector ADMA</caps:sentence>
                </title>
                <content>
                  <para>
                    <caps:sentence sentenceid="00565cdd7aa76ac00c30e677d79de49d" id="tgt278" class="tgtSentence">Cree los siguientes perfiles para el conector ADMA:</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="e9dc8b7f62f3134aec90a4f763e67180" id="tgt279" class="tgtSentence">Perfil1: Importación completa (solo etapa)</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="4481ca6f8ea182b57debde3557b78b3d" id="tgt280" class="tgtSentence">Perfil2: Sincronización completa</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="3a18f7e11e9dbf6254e9555c5e181253" id="tgt281" class="tgtSentence">Perfil3: Importación diferencial (solo etapa)</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="71989f4fa965759e5dc8609a2f949fda" id="tgt282" class="tgtSentence">Perfil4: Sincronización diferencial</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="5019f5d6198c520f49ecf7d89208fd3e" id="tgt283" class="tgtSentence">Perfil5: Exportar</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                  <procedure>
                    <title>
                      <caps:sentence sentenceid="2a1f61c0752e4db971d939b30d86043e" id="tgt284" class="tgtSentence">Para crear perfiles de ejecución para el conector ADMA:</caps:sentence>
                    </title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="703826ac42a49db169ad41b625280d7b" id="tgt285" class="tgtSentence">Abra el Synchronization Service Manager y en el menú Herramientas haga clic en Agentes de administración.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="5a387cd38f5183440fe795ecb655c96c" id="tgt286" class="tgtSentence">En la lista Agentes de administración, seleccione ADMA.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="2ed61ee7dd489cc24ba820ac2f806e75" id="tgt287" class="tgtSentence">Para abrir el cuadro de diálogo de Configurar perfiles de ejecución para, haga clic en Configurar perfiles de ejecución en el menú Acciones.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="7ddf71170974bb2c61228b5196baea30" id="tgt288" class="tgtSentence">	Por cada perfil de ejecución de la tabla que se encuentra justo encima de este procedimiento, complete los siguientes pasos:
</caps:sentence>
                          </para>
                          <list class="bullet">
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="39a23da5f288163f48a91ccce626150f" id="tgt289" class="tgtSentence">Para abrir el asistente para Configurar perfiles de ejecución, haga clic en Nuevo perfil.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="f0478091223aa8d0fc8a0e86e26a5ab5" id="tgt290" class="tgtSentence">En el cuadro Nombre escriba el nombre de perfil que se muestra en la tabla y haga clic en Siguiente.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="cf9868e352de949016081bfef6415279" id="tgt291" class="tgtSentence">En la lista Tipo, seleccione el tipo de paso que se muestra en la tabla y después haga clic en Siguiente.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="93770c5f1404dcc8bfc210d2784983ce" id="tgt292" class="tgtSentence">Haga clic en Finalizar para crear el perfil de ejecución.</caps:sentence>
                              </para>
                            </listItem>
                          </list>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="5cc2b2e642565a57fc95e668423de85c" id="tgt293" class="tgtSentence">Para cerrar el cuadro de diálogo Configurar perfiles de ejecución, haga clic en Aceptar.</caps:sentence>
                          </para>
                        </content>
                      </step>
                    </steps>
                  </procedure>
                </content>
              </section>
              <section>
                <title>
                  <caps:sentence sentenceid="609e62661e548b77e81cd43e68e26094" id="tgt294" class="tgtSentence">Crear perfiles de ejecución para el conector MIMMA</caps:sentence>
                </title>
                <content>
                  <para>
                    <caps:sentence sentenceid="b3a9c820213d6a4d18f46f3a0ad306c7" id="tgt295" class="tgtSentence">Cree los siguientes perfiles para el conector MIMMA:</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="e9dc8b7f62f3134aec90a4f763e67180" id="tgt296" class="tgtSentence">Perfil1: Importación completa (solo etapa)</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="4481ca6f8ea182b57debde3557b78b3d" id="tgt297" class="tgtSentence">Perfil2: Sincronización completa</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="3a18f7e11e9dbf6254e9555c5e181253" id="tgt298" class="tgtSentence">Perfil3: Importación diferencial (solo etapa)</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="71989f4fa965759e5dc8609a2f949fda" id="tgt299" class="tgtSentence">Perfil4: Sincronización diferencial</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence sentenceid="5019f5d6198c520f49ecf7d89208fd3e" id="tgt300" class="tgtSentence">Perfil5: Exportar</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                  <procedure>
                    <title>
                      <caps:sentence sentenceid="23f0b755fa7d3f6e5937a87984569303" id="tgt301" class="tgtSentence">Para crear perfiles de ejecución para el conector MIMMA:</caps:sentence>
                    </title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="703826ac42a49db169ad41b625280d7b" id="tgt302" class="tgtSentence">Abra el Synchronization Service Manager y en el menú Herramientas haga clic en Agentes de administración.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="bf10d72cbd4b01451c7e1e4028d0c680" id="tgt303" class="tgtSentence">En la lista Agentes de administración, seleccione MIMMA.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="2ed61ee7dd489cc24ba820ac2f806e75" id="tgt304" class="tgtSentence">Para abrir el cuadro de diálogo de Configurar perfiles de ejecución para, haga clic en Configurar perfiles de ejecución en el menú Acciones.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="7ddf71170974bb2c61228b5196baea30" id="tgt305" class="tgtSentence">	Por cada perfil de ejecución de la tabla que se encuentra justo encima de este procedimiento, complete los siguientes pasos:
</caps:sentence>
                          </para>
                          <list class="bullet">
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="39a23da5f288163f48a91ccce626150f" id="tgt306" class="tgtSentence">Para abrir el asistente para Configurar perfiles de ejecución, haga clic en Nuevo perfil.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="f0478091223aa8d0fc8a0e86e26a5ab5" id="tgt307" class="tgtSentence">En el cuadro Nombre escriba el nombre de perfil que se muestra en la tabla y haga clic en Siguiente.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="cf9868e352de949016081bfef6415279" id="tgt308" class="tgtSentence">En la lista Tipo, seleccione el tipo de paso que se muestra en la tabla y después haga clic en Siguiente.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence sentenceid="93770c5f1404dcc8bfc210d2784983ce" id="tgt309" class="tgtSentence">Haga clic en Finalizar para crear el perfil de ejecución.</caps:sentence>
                              </para>
                            </listItem>
                          </list>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence sentenceid="5cc2b2e642565a57fc95e668423de85c" id="tgt310" class="tgtSentence">Para cerrar el cuadro de diálogo Configurar perfiles de ejecución, haga clic en Aceptar.</caps:sentence>
                          </para>
                        </content>
                      </step>
                    </steps>
                  </procedure>
                </content>
              </section>
            </sections>
          </section>
          <section>
            <title>
              <caps:sentence sentenceid="7705c46ed03bf3bc568b59e1ea9e2559" id="tgt311" class="tgtSentence">Configurar el Servicio MIM</caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence sentenceid="f0456d06813e5856757299e643fc2273" id="tgt312" class="tgtSentence">Para el escenario de este documento, realice los siguientes pasos en el Servicio MIM mediante el Portal de MIM:</caps:sentence>
              </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <caps:sentence sentenceid="0fd0a00ca140ff7bf54dd35716d5d6c8" id="tgt313" class="tgtSentence">Crear la regla de sincronización de entrada de usuario de AD</caps:sentence>
                  </para>
                </listItem>
              </list>
              <procedure>
                <title>
                  <caps:sentence sentenceid="8cc257c197be9a572094d20d691a353b" id="tgt314" class="tgtSentence">Para crear la regla de sincronización de entrada de usuario de AD
</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="7917ef0aa52f6731d38bd1a5fba27868" id="tgt315" class="tgtSentence">En la barra de navegación de la página principal del Portal de MIM, haga clic en Administración.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="ed1d82262899132f0ff939adc221bf23" id="tgt316" class="tgtSentence">Para abrir la página Reglas de sincronización, haga clic en Reglas de sincronización.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="55bb4f8c8943bbc04eb2da1b9b54402f" id="tgt317" class="tgtSentence">Para abrir el Asistente para crear reglas de sincronización, haga clic en Nueva en la barra de herramientas.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="c9dbd662c4490718814c75d71f0e0476" id="tgt318" class="tgtSentence">En la pestaña General, proporcione la siguiente información y después haga clic en Siguiente:
</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="254281b00f735bdcd837717da3a50590" id="tgt319" class="tgtSentence">Nombre para mostrar: Regla de sincronización de entrada de usuario de AD
</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="76d65fa474da9713c3f50e17b7de4741" id="tgt320" class="tgtSentence">Dirección del flujo de datos: Entrante</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="1a59f9872be8173267ff9cf6cf865b66" id="tgt321" class="tgtSentence">En la pestaña Ámbito, proporcione la siguiente información y después haga clic en Siguiente:
</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="c7cbc530bdaf202fdcba4dad627a720f" id="tgt322" class="tgtSentence">Tipo de recurso de metaverso: person</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="3ec176a9c4985117c7f41b0e35c9d5b7" id="tgt323" class="tgtSentence">Sistema externo: ADMA</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="c8be943576a41ee9f37b3bbf43ba6799" id="tgt324" class="tgtSentence">Tipo de recurso de sistema externo: persona
</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="99be3e9e6766e62f69bac71f14227da3" id="tgt325" class="tgtSentence">En la pestaña Relación, proporcione la siguiente información y después haga clic en Siguiente:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="e7994285ee331e705944fb9a646c998b" id="tgt326" class="tgtSentence">Para configurar los Criterios de relación, seleccione objectSID en la lista MetaverseObject:person(Attribute) y ObjectSID de la lista ConnectedSystemObject:person (Attribute).</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="2dd0d38da44f4cf39e671ae943bd8608" id="tgt327" class="tgtSentence">Seleccione Crear recurso en FIM.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="16ff06af083482b272ec7535ec695137" id="tgt328" class="tgtSentence">En la página Flujo del atributo entrante, proporcione la siguiente información y después haga clic en Siguiente:
 
</caps:sentence>
                      </para>
                      <table border="1">
                        <tbody>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="82f4c1848c69a4654ddeb1652051cb64" id="tgt329" class="tgtSentence">Regla de flujo</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="36cd38f49b9afa08222c0dc9ebfe35eb" id="tgt330" class="tgtSentence">Origen</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="6990a54322d9232390a784c5c9247dd6" id="tgt331" class="tgtSentence">Destination</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="79141684506f886b51651495564cf76d" id="tgt332" class="tgtSentence">Regla 1</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="7f5ac5ed292277dd0f8367d612bbe974" id="tgt333" class="tgtSentence">samAccountName</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="8fa14cdd754f91cc6554c9e71929cce7" id="tgt334" class="tgtSentence">f</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="5195cac673a0711858b5677c248dfef0" id="tgt335" class="tgtSentence">Regla 2</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <caps:sentence sentenceid="136b9caf6aca9aa4060730ce52609e23" id="tgt336" class="tgtSentence"> <para>displayName</para></caps:sentence>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="8d38cbc95c2cfb65c3ae913d1b1410b1" id="tgt337" class="tgtSentence">displayName</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="bbe1c88aa9cd4ed55b5558abf92cb9ab" id="tgt338" class="tgtSentence">Regla 3</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="cd2d171d7836aa13e1f51444e201ea79" id="tgt339" class="tgtSentence">EmployeeType</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="cd2d171d7836aa13e1f51444e201ea79" id="tgt340" class="tgtSentence">EmployeeType</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="33b47e8a9fd9401506ba222b2fd41797" id="tgt341" class="tgtSentence">Regla 4</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="6ce8ba046cf55cca086ac00e80859815" id="tgt342" class="tgtSentence">givenName</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="6ce8ba046cf55cca086ac00e80859815" id="tgt343" class="tgtSentence">givenName</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="3a425d0527df18f55210ceba2a1cdd40" id="tgt344" class="tgtSentence">Regla 5</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="afbe94cdbe69a93efabc9f1325fc7dff" id="tgt345" class="tgtSentence">sn</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="8ad75c5a8821cc294f189181722acb56" id="tgt346" class="tgtSentence">lastName</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="5537fe47ec5f34f4eba43de52d2d574d" id="tgt347" class="tgtSentence">Regla 6</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="1d0258c2440a8d19e716292b231e3190" id="tgt348" class="tgtSentence">Manager</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="1d0258c2440a8d19e716292b231e3190" id="tgt349" class="tgtSentence">manager</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="908eaaea8d5453bc1f4c354ca9596955" id="tgt350" class="tgtSentence">Regla 7</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="6381c8768508bc58d1e5d1539f373995" id="tgt351" class="tgtSentence">objectSID</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="6381c8768508bc58d1e5d1539f373995" id="tgt352" class="tgtSentence">ObjectSID</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="3e916d6bc7bb4186c13631b33bbe5755" id="tgt353" class="tgtSentence">Regla 8</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="6c145fb4d6e92675044df98e348138b5" id="tgt354" class="tgtSentence">"Contoso"</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence sentenceid="ad5f82e879a9c5d6b5b442eb37e50551" id="tgt355" class="tgtSentence">dominio</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                        </tbody>
                      </table>
                      <para>
                        <caps:sentence sentenceid="199c7641944a80c576c22e4334d6a8fa" id="tgt356" class="tgtSentence">Por cada fila de esta tabla, realice los pasos siguientes:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="8da72a3fcdcfc9e31cbf847f632c4ec6" id="tgt357" class="tgtSentence">Para abrir el cuadro de diálogo de Definición de flujo, haga clic en Nuevo flujo de atributo.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="09e26384ef0d58d344b684b93db73299" id="tgt358" class="tgtSentence">En la pestaña Origen, seleccione el atributo que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="53c9f65a165c61080bbbe3a7fc8ec472" id="tgt359" class="tgtSentence">En la pestaña Destino, seleccione el atributo que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="3cc02eb712e63b8506872275c6464970" id="tgt360" class="tgtSentence">Para aplicar la configuración de flujo de atributo, haga clic en Aceptar.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="ed08fa78e01abda7ed33dffc748386b0" id="tgt361" class="tgtSentence">En la pestaña Resumen, haga clic en Enviar.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
            </content>
          </section>
          <section>
            <title>
              <caps:sentence sentenceid="60bc131e8371ca78dc8f3867e149ef07" id="tgt362" class="tgtSentence">Inicializar el entorno de pruebas</caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence sentenceid="990ea22bd62aba05f9e44403164513f0" id="tgt363" class="tgtSentence">Antes de que pueda probar la configuración con los datos de AD, debe inicializar la configuración.</caps:sentence>
                <caps:sentence sentenceid="551e7283728446656a1a1b7ccedb5ef3" id="tgt364" class="tgtSentence"> Los siguientes pasos forman parte de este proceso:</caps:sentence>
              </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <caps:sentence sentenceid="59ced2dd15fb561280c64670eb3cefc3" id="tgt365" class="tgtSentence">Habilitar el aprovisionamiento</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="a4d55b4d40ce1dafc081bdcc2266a1ba" id="tgt366" class="tgtSentence">Inicializar el MIMMA</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="6fb4c1b4f675d254e0dece49de5db912" id="tgt367" class="tgtSentence">Configurar la prioridad del flujo de atributos</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence sentenceid="ec05bb25745d584666f41c05677f3215" id="tgt368" class="tgtSentence">Inicializar el ADMA</caps:sentence>
                  </para>
                </listItem>
              </list>
              <procedure>
                <title>
                  <caps:sentence sentenceid="352604a31277cc2d946cf1a241ea4209" id="tgt369" class="tgtSentence">Para habilitar el aprovisionamiento</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="86b882e9cb02b369feb5da13c32fcb32" id="tgt370" class="tgtSentence">Abra el Synchronization Service Manager.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="01532184a718e44592003f8cdb44fc31" id="tgt371" class="tgtSentence">Para abrir el cuadro de diálogo Opciones, haga clic en Opciones en el menú Herramientas.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="126e8a8cbd6389e889e6b60f2f41f02e" id="tgt372" class="tgtSentence">Seleccione Habilitar aprovisionamiento de reglas de sincronización.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="2d3f36885467508114f84a4b159da2ca" id="tgt373" class="tgtSentence">Para cerrar el cuadro de diálogo Opciones, haga clic en Aceptar.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure>
                <title>
                  <caps:sentence sentenceid="75fec1b15649977f406d5337c1781d4e" id="tgt374" class="tgtSentence">Para inicializar el MIMMA</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="03d0140db652dbf195bcf94037478e8f" id="tgt375" class="tgtSentence">Ejecute un ciclo de sincronización completo en este conector.</caps:sentence>
                        <caps:sentence sentenceid="1941cf033ea40bc7224afa23fbb312b9" id="tgt376" class="tgtSentence"> El ciclo completo consta de las siguientes ejecuciones del perfil de ejecución:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="7e129587bef6a100bfb18549b468ad61" id="tgt377" class="tgtSentence">Importación completa</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="201d5e1675715ca07c07d7e1158a7309" id="tgt378" class="tgtSentence">Sincronización completa</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="b2507468f95156358fa490fd543ad2f0" id="tgt379" class="tgtSentence">Exportar</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="d61e4e80b88f33b1c0c92ef645169a17" id="tgt380" class="tgtSentence">Importación diferencial</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="42dbe8c27593c8b4590aa485b914a0b0" id="tgt381" class="tgtSentence">	Abra el Synchronization Service Manager y haga clic en Agentes de administración, en el menú Herramientas.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="ee23a2d026f71917e9fa768daa132814" id="tgt382" class="tgtSentence">	En la lista Agentes de administración, seleccione MIMMA.
</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="7dbc2b7cd432fffd6177b562f1bc7a44" id="tgt383" class="tgtSentence">Para abrir el cuadro de diálogo Ejecutar agente de administración, haga clic en Ejecutar en el menú Acciones.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="0f7a4dbd058bca9f446fb20826afba54" id="tgt384" class="tgtSentence">Por cada fila de la tabla que se encuentre justo encima de este procedimiento, complete los siguientes pasos:
</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="7dbc2b7cd432fffd6177b562f1bc7a44" id="tgt385" class="tgtSentence">Para abrir el cuadro de diálogo Ejecutar agente de administración, haga clic en Ejecutar en el menú Acciones.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="67b85f35ed5b0ad31dfb3f167b3dbf61" id="tgt386" class="tgtSentence">En la lista Ejecutar perfiles, seleccione el perfil de ejecución que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="673509e06582836de817d628545e58e3" id="tgt387" class="tgtSentence">	Para iniciar el perfil de ejecución, haga clic en Aceptar.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure>
                <title>
                  <caps:sentence sentenceid="6fb4c1b4f675d254e0dece49de5db912" id="tgt388" class="tgtSentence">Configurar la prioridad del flujo de atributos</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="69f13b72db11a474e24b2460a72d05f5" id="tgt389" class="tgtSentence">Durante la inicialización del conector de MIM, las reglas de sincronización configuradas se introdujeron en el metaverso.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="d11ad1f88822b29c1110769e4632b277" id="tgt390" class="tgtSentence">Ajuste la prioridad del flujo de atributos para los atributos aportados por este conector con el fin de asegurarse de que los atributos que ya estén en AD puedan introducirse en el metaverso y más adelante en la base de datos del Servicio MIM.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure>
                <title>
                  <caps:sentence sentenceid="ec05bb25745d584666f41c05677f3215" id="tgt391" class="tgtSentence">Inicializar el ADMA</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="a001bc5bfac0c6b9f738d1d3197aa91b" id="tgt392" class="tgtSentence">Para inicializar el conector de Active Directory, debe ejecutar una importación completa y una sincronización completa en él.</caps:sentence>
                        <caps:sentence sentenceid="f31e3438cf79d2f1bfdb4c7b04edcbf8" id="tgt393" class="tgtSentence"> La importación completa es necesaria para traer los objetos existentes desde AD hasta el espacio del conector.</caps:sentence>
                        <caps:sentence sentenceid="dabe7a9e67a8dc69c620d7eeb3112c66" id="tgt394" class="tgtSentence"> La sincronización completa es necesaria porque las reglas de sincronización han cambiado mediante la proyección de nuevas reglas de sincronización desde el espacio del conector de MIM hacia el interior del metaverso.</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="3bce45a0c0fd3c1e298ed68d6bd9c3ab" id="tgt395" class="tgtSentence">Paso 1: Ejecutar importación completa</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="37e8efdcc466e90da8194cddbc62cf96" id="tgt396" class="tgtSentence">Paso 2: Ejecutar sincronización completa</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="6758cd85307451b3aa9bbd748d725490" id="tgt397" class="tgtSentence">Abra el Synchronization Service Manager y haga clic en Agentes de administración, en el menú Herramientas.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="5a387cd38f5183440fe795ecb655c96c" id="tgt398" class="tgtSentence">En la lista Agentes de administración, seleccione ADMA.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="7dbc2b7cd432fffd6177b562f1bc7a44" id="tgt399" class="tgtSentence">Para abrir el cuadro de diálogo Ejecutar agente de administración, haga clic en Ejecutar en el menú Acciones.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="fc4895d0c6d26451ecd8249e0812a916" id="tgt400" class="tgtSentence">Por cada fila de la tabla que se encuentre justo encima de este procedimiento, complete los siguientes pasos:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="7dbc2b7cd432fffd6177b562f1bc7a44" id="tgt401" class="tgtSentence">Para abrir el cuadro de diálogo Ejecutar agente de administración, haga clic en Ejecutar en el menú Acciones.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="67b85f35ed5b0ad31dfb3f167b3dbf61" id="tgt402" class="tgtSentence">En la lista Ejecutar perfiles, seleccione el perfil de ejecución que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="673509e06582836de817d628545e58e3" id="tgt403" class="tgtSentence">	Para iniciar el perfil de ejecución, haga clic en Aceptar.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure>
                <title>
                  <caps:sentence sentenceid="548b220a836b04ef8429dbebd08fe950" id="tgt404" class="tgtSentence">Rellenar la base de datos del Servicio MIM</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="4e0da9ce21240c231fd8eaab447a5697" id="tgt405" class="tgtSentence">Para rellenar la base de datos del Servicio MIM con los objetos, debe ejecutar un ciclo de sincronización en el conector MIMMA.</caps:sentence>
                        <caps:sentence sentenceid="1a4a6d2e6d8b2b748a23f94d97266c0a" id="tgt406" class="tgtSentence"> El ciclo consta de las siguientes ejecuciones del perfil de ejecución:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="71fdd13f43011b4b4bd33e9ee5984575" id="tgt407" class="tgtSentence">1: Exportar</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="26652b43260c7d0d651dc9b187bc3e5c" id="tgt408" class="tgtSentence">2: Importación completa</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="d6f501e6ba24b40f601b215795445fa1" id="tgt409" class="tgtSentence">3: Sincronización completa</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="286c3e8f205aae1a405fed49a77ad187" id="tgt410" class="tgtSentence">Abra el Synchronization Service Manager y haga clic en Agentes de administración, en el menú Herramientas.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="ee23a2d026f71917e9fa768daa132814" id="tgt411" class="tgtSentence">	En la lista Agentes de administración, seleccione MIMMA.
</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="f224b83de41c06672bf9249c6b9363da" id="tgt412" class="tgtSentence">	Para abrir el cuadro de diálogo Ejecutar agente de administración, haga clic en Ejecutar en el menú Acciones.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="fc4895d0c6d26451ecd8249e0812a916" id="tgt413" class="tgtSentence">Por cada fila de la tabla que se encuentre justo encima de este procedimiento, complete los siguientes pasos:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="7dbc2b7cd432fffd6177b562f1bc7a44" id="tgt414" class="tgtSentence">Para abrir el cuadro de diálogo Ejecutar agente de administración, haga clic en Ejecutar en el menú Acciones.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence sentenceid="67b85f35ed5b0ad31dfb3f167b3dbf61" id="tgt415" class="tgtSentence">En la lista Ejecutar perfiles, seleccione el perfil de ejecución que se muestra para esa fila en la tabla.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence sentenceid="673509e06582836de817d628545e58e3" id="tgt416" class="tgtSentence">	Para iniciar el perfil de ejecución, haga clic en Aceptar.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
            </content>
          </section>
        </sections>
      </section>
      <relatedTopics></relatedTopics>
    </developerConceptualDocument>
  </caps:SxSTarget>
  <caps:SxSSource locale="en-US">
    <developerConceptualDocument xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xlink="http://www.w3.org/1999/xlink">
      <introduction>
        <para></para>
      </introduction>
      <section>
        <title></title>
        <content>
          <para></para>
          <procedure>
            <title></title>
            <steps class="ordered">
              <step>
                <content>
                  <para>
                    <caps:sentence id="src1" class="srcSentence">On the corpidm server you are using for  identity management, log in as <legacyItalic>contoso\Administrator</legacyItalic>.</caps:sentence>
                    <caps:sentence id="src2" class="srcSentence"> Administrator rights are used to install <legacyBold>MIM Sync, Service, and Portal</legacyBold> in this environment.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src3" class="srcSentence">Unpack the MIM installation package or mount the MIM image DVD.</caps:sentence>
                  </para>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence id="src4" class="srcSentence">Install MIM 2016 Synchronization Service</caps:sentence>
        </title>
        <content>
          <para></para>
          <procedure>
            <title></title>
            <steps class="ordered">
              <step>
                <content>
                  <para>
                    <caps:sentence id="src5" class="srcSentence">In the unpacked MIM installation folder, navigate to the <legacyBold>Synchronization Service</legacyBold> folder.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src6" class="srcSentence">Run the <legacyBold>MIM Synchronization Service installer</legacyBold>.</caps:sentence>
                    <caps:sentence id="src7" class="srcSentence"> Follow the guidelines of the installer and complete the installation.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src8" class="srcSentence">In the welcome screen – click <legacyBold>Next</legacyBold>.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="7fce56b4-c389-487b-92cf-86a4ef8e9015"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src9" class="srcSentence">Review the license terms and if you accept them, click <legacyBold>Next</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src10" class="srcSentence">In the feature selection screen click <legacyBold>Next</legacyBold>.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="cebd3544-d6f2-45d3-9fdb-129f8c5ad39b"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src11" class="srcSentence">In the Sync database configuration screen, select:</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence id="src12" class="srcSentence">The SQL Server is located on: <legacyBold>This computer</legacyBold>.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src13" class="srcSentence">The SQL Server instance is: <legacyBold>The default instance</legacyBold>.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="8847f245-3dce-4bd0-a561-a78ebc8c1bad"></image>
                      </mediaLink>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src14" class="srcSentence">Configure the Sync Service Account according to the account you created earlier:</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence id="src15" class="srcSentence">Service account: <legacyItalic>MIMSync</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src16" class="srcSentence">Password: <legacyItalic>Pass@word1</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src17" class="srcSentence">Service Account Domain or local computer name: <legacyItalic>contoso</legacyItalic></caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="3efe7f1f-6b57-459c-b161-aa255d604c74"></image>
                      </mediaLink>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src18" class="srcSentence">Provide MIM Sync installer with the relevant security groups:</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence id="src19" class="srcSentence">Administrator = <legacyItalic>contoso\MIMSyncAdmins</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src20" class="srcSentence">Operator= <legacyItalic>contoso\MIMSyncOperators</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src21" class="srcSentence">Joiner = <legacyItalic>contoso\MIMSyncJoiners</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src22" class="srcSentence">Connector Browse = <legacyItalic>contoso\MIMSyncBrowse</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src23" class="srcSentence">WMI Password Management= <legacyItalic>contoso\MIMSyncPasswordReset</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src24" class="srcSentence">In the security settings screen, check Enable firewall rules for inbound RPC communications, and click <legacyBold>Next</legacyBold>.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="98412dd2-9cb0-48dd-aa6b-75810c401a4d"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src25" class="srcSentence">Click <legacyBold>Install</legacyBold> to begin the installation of MIM  Sync.</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence id="src26" class="srcSentence">A warning concerning the MIM Sync service account may appear – click <legacyBold>OK</legacyBold>.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src27" class="srcSentence">MIM Sync will now be installed.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="213ed09f-ae3a-4bc4-a45a-696b5cfcd165"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src28" class="srcSentence">A notice on creating a backup for the encryption key will be shown – click OK, then select a folder to store the encryption key backup.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="46ad2a92-20f5-4912-a9ed-0d4897846f18"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src29" class="srcSentence">When the installer successfully completes the installation, click <legacyBold>Finish</legacyBold>.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="3089e9b6-e243-420b-8d0d-b9d1ca4e34a3"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src30" class="srcSentence">You will be prompted to log off and log on for group membership changes to take effect.</caps:sentence>
                        <caps:sentence id="src31" class="srcSentence"> Click <legacyBold>Yes</legacyBold> to logoff.</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence id="src32" class="srcSentence">Install MIM Service and Portal</caps:sentence>
        </title>
        <content>
          <para></para>
          <procedure>
            <title></title>
            <steps class="ordered">
              <step>
                <content>
                  <para>
                    <caps:sentence id="src33" class="srcSentence">Run the <legacyBold>MIM Service and Portal installer</legacyBold> from the unpacked <legacyBold>Service and Portal</legacyBold> sub-folder.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src34" class="srcSentence">In the welcome screen, click <legacyBold>Next</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src35" class="srcSentence">Read the End-User License Agreement, and if you accept the license terms, click <legacyBold>Next</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src36" class="srcSentence">In the MIM Customer Experience Improvement Program screen, click <legacyBold>Next</legacyBold>.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src37" class="srcSentence">For this deployment, when selecting component features, it is necessary to include  the MIM Service (except for MIM Reporting) and MIM Portal features.</caps:sentence>
                    <caps:sentence id="src38" class="srcSentence"> You can also select the MIM Password Reset Portal and MIM Password Reset Portal.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src39" class="srcSentence">When configuring common services and the MIM database connection, specify “Create a new database”.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="5a2dd439-674d-43ae-ad84-8ad37cf7e973"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src40" class="srcSentence">When configuring a mail server connection, set the mail server to  your Exchange server.</caps:sentence>
                    <caps:sentence id="src41" class="srcSentence"> If you do not have a mail server configured, specify localhost as the mail server name, and uncheck the top two checkboxes.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="dfc22772-a353-457e-b402-949c90d715ed"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src42" class="srcSentence">Specify that you want to generate a new self-signed certificate, or select the relevant certificate.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src43" class="srcSentence">Specify the Service Account name to use, for example, <legacyItalic>MIMService</legacyItalic>, and the Service Account password, for example, <legacyItalic>Pass@word1</legacyItalic> (the password in the first step above), your Service Account domain, for example, contoso and the Service Email Account, for example contoso.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="fbcbcc15-410b-4a2e-a65d-f8f6a8a46fe7"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src44" class="srcSentence">Note that a warning may appear that the Service Account is not secure in its current configuration.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src45" class="srcSentence">Accept the defaults for the Synchronization Server location, and specify the MIM Management Agent account as <legacyItalic>contoso\MIMsync</legacyItalic>.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="8596cfda-8058-421f-abb7-3769bf4399f7"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src46" class="srcSentence">Specify <legacyItalic>CorpIDM (this computer's name)</legacyItalic> as MIM Service server address for the MIM Portal.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src47" class="srcSentence">Specify <legacyItalic>http://CorpIDM.contoso.local:82</legacyItalic> as the SharePoint site collection URL.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src48" class="srcSentence">Specify <legacyItalic>http://CorpIDM.contoso.local:8080</legacyItalic>  as the Password Registration URL.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src49" class="srcSentence">Specify <legacyItalic>http://CorpIDM.contoso.local:8088</legacyItalic>   as the Password Reset URL.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src50" class="srcSentence">Select the checkbox to open ports 5725 and 5726 in the firewall, and the checkbox to grant all authenticated users access to MIM Portal.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src51" class="srcSentence">In the MIM Password Registration Portal configuration screen</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence id="src52" class="srcSentence">Specify the service account name for SSPR Registration as <legacyItalic>contoso\MIMSSPR</legacyItalic> and its password to <legacyItalic>Pass@word1</legacyItalic>.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src53" class="srcSentence">Specify  CORPIDM as the Host Name for MIM Password Registration, and set the port to <legacyBold>8080</legacyBold>.</caps:sentence>
                        <caps:sentence id="src54" class="srcSentence"> Enable the opening the port in firewall.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="c4b77ce2-61b6-4f56-9fcc-53097b5a272f"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src55" class="srcSentence">A warning will appear – read it and click <legacyBold>Next</legacyBold>.</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src56" class="srcSentence">In the next MIM Password Registration Portal configuration screen, specify  <legacyItalic>http://CorpIDM.contoso.local</legacyItalic> as the MIM Service Server Address for the Password Registration Portal.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src57" class="srcSentence">In the MIM Password Reset Portal configuration screen</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence id="src58" class="srcSentence">State the service account name for SSPR Registration as <legacyItalic>Domain\MIMSSPRService</legacyItalic> and its password to <legacyItalic>Pass@word1</legacyItalic>.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src59" class="srcSentence">Specify  <legacyItalic>CorpIDname  http://CorpIDname.domain.local</legacyItalic> as the Host Name for MIM Password Registration, port <legacyBold>8088</legacyBold>.</caps:sentence>
                        <caps:sentence id="src60" class="srcSentence"> Enable the opening the port in firewall.</caps:sentence>
                      </para>
                      <mediaLink>
                        <image xlink:href="7f1735ac-058c-4fc0-b99e-dc7bf02a8bf4"></image>
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src61" class="srcSentence">A warning will appear – read it and click <legacyBold>Next</legacyBold>.</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src62" class="srcSentence">In the next MIM Password Registration Portal configuration screen, specify <legacyItalic>CorpIDname  http://CorpIDname.domain.local</legacyItalic>   as the MIM Service Server Address for the Password Registration Portal.</caps:sentence>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src63" class="srcSentence">When all pre-installation definitions are ready, click <legacyBold>Install</legacyBold> to begin installing the selected <legacyBold>Service and Portal</legacyBold> components.</caps:sentence>
                  </para>
                  <mediaLink>
                    <image xlink:href="a31e66b0-0c47-4c3b-840d-30fc521298e8"></image>
                  </mediaLink>
                </content>
              </step>
              <step>
                <content>
                  <para>
                    <caps:sentence id="src64" class="srcSentence">After installation completes, verify that the MIM Portal is active.</caps:sentence>
                  </para>
                  <list class="ordered">
                    <listItem>
                      <para>
                        <caps:sentence id="src65" class="srcSentence">Launch Internet Explorer and connect to the MIM Portal on  <legacyItalic>http://corpidm.contoso.local:82/identitymanagement</legacyItalic></caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src66" class="srcSentence">Note that there may be a short delay on the first visit to this page.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src67" class="srcSentence">If necessary, authenticate as <legacyItalic>contoso\Administrator</legacyItalic> to Internet Explorer.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src68" class="srcSentence">In Internet Explorer, open the <legacyBold>Internet Options</legacyBold>, change to the <legacyBold>security</legacyBold> tab, and add the site to the <legacyBold>Local intranet</legacyBold> zone if it is not already there.</caps:sentence>
                        <caps:sentence id="src69" class="srcSentence">  Close the <legacyBold>Internet Options</legacyBold> dialog.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src70" class="srcSentence">Enable users to view their own entry in MIM.</caps:sentence>
                      </para>
                      <list class="ordered">
                        <listItem>
                          <para>
                            <caps:sentence id="src71" class="srcSentence">Using Internet Explorer, in <legacyBold>MIM Portal</legacyBold>, click on <legacyBold>Management Policy Rules</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src72" class="srcSentence">Search for the management policy rule:
</caps:sentence>
                          </para>
                          <para>
                            <caps:sentence id="src73" class="srcSentence">User management: Users can read attributes of their own.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src74" class="srcSentence">Select this management policy rule, uncheck Policy is disabled, </caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src75" class="srcSentence">Click <legacyBold>OK</legacyBold> and then click <legacyBold>Submit</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src76" class="srcSentence">Verify that the firewall allows incoming connections to TCP port 5725 and 5726.</caps:sentence>
                      </para>
                      <list class="ordered">
                        <listItem>
                          <para>
                            <caps:sentence id="src77" class="srcSentence">Launch <legacyBold>Administrative Tools » Windows Firewall</legacyBold> with <legacyBold>Advanced Security</legacyBold></caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src78" class="srcSentence">Click on <legacyBold>Inbound Rules</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src79" class="srcSentence">Verify that the two following rules are listed:</caps:sentence>
                          </para>
                          <list class="bullet">
                            <listItem>
                              <para>
                                <caps:sentence id="src80" class="srcSentence">Forefront Identity Manager Service (STS).</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence id="src81" class="srcSentence">Forefront Identity Manager Service (Webservice).</caps:sentence>
                              </para>
                            </listItem>
                          </list>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src82" class="srcSentence">Complete the wizard and close the <legacyBold>Windows Firewall</legacyBold> application.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src83" class="srcSentence">Launch <legacyBold>Control Panel »</legacyBold> Network and Internet <legacyBold>»</legacyBold> View network status and tasks.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src84" class="srcSentence">Verify that there is an active Network listed as contoso.local as a Domain network.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src85" class="srcSentence">Close <legacyBold>Control Panel</legacyBold>.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </listItem>
                  </list>
                </content>
              </step>
            </steps>
          </procedure>
          <alert class="note">
            <para>
              <caps:sentence id="src86" class="srcSentence">Optional: At this point you can install MIM add-ins and extensions.</caps:sentence>
            </para>
          </alert>
        </content>
      </section>
      <section>
        <title>
          <caps:sentence id="src87" class="srcSentence">Configure MIM Sync to Synchronize from Active Directory to MIM Service</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence id="src88" class="srcSentence">By default, MIM Sync does not have any connectors configured.</caps:sentence>
            <caps:sentence id="src89" class="srcSentence">   A typical first step is to use MIM Sync to populate the FIM Service database with existing Active Directory accounts.</caps:sentence>
            <caps:sentence id="src90" class="srcSentence">  For this, you will use the MIM Sync Service application.</caps:sentence>
          </para>
        </content>
        <sections>
          <section>
            <title>
              <caps:sentence id="src91" class="srcSentence">Create the MIM MA</caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence id="src92" class="srcSentence">The MIM MA is a connector for MIM Sync to the MIM Service.</caps:sentence>
                <caps:sentence id="src93" class="srcSentence"> To create this connector, you use the Create Management Agent wizard.</caps:sentence>
              </para>
              <para>
                <caps:sentence id="src94" class="srcSentence">When you configure a MIM management agent, you need to specify a user account.</caps:sentence>
                <caps:sentence id="src95" class="srcSentence"> This document uses mimma as name for this account.</caps:sentence>
              </para>
              <alert class="caution">
                <para>
                  <caps:sentence id="src96" class="srcSentence">The account you use for your MIM management agent must be the same account as the one you have specified during the installation of MIM Service.</caps:sentence>
                </para>
              </alert>
              <para>
                <caps:sentence id="src97" class="srcSentence">To create the MIM MA</caps:sentence>
              </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <caps:sentence id="src98" class="srcSentence">Open the Synchronization Service Manager.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src99" class="srcSentence">To open the Create Management Agent wizard, on the Actions menu, click <ui>Create</ui>.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src100" class="srcSentence">On the Create Management Agent page, provide the following settings, and then click <ui>Next</ui>.</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src101" class="srcSentence">Management agent for: FIM Service management agent
</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src102" class="srcSentence">Name: MIMMA</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src103" class="srcSentence">On the Connect to Database page, provide the following settings, and then click Next</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src104" class="srcSentence">Server: localhost</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src105" class="srcSentence">Database: FIMService</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src106" class="srcSentence">FIM Service base address: http://localhost:5725</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src107" class="srcSentence">Authentication mode: Windows integrated authentication</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src108" class="srcSentence">User name: mimma
</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src109" class="srcSentence">Password: Pass@word</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src110" class="srcSentence">	Domain: contoso</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src111" class="srcSentence">
On the Selected Object Types page, verify that the object types that are listed below are selected, and then click Next</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src112" class="srcSentence">	ExpectedRuleEntry</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src113" class="srcSentence">DetectedRuleEntry</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src114" class="srcSentence">SynchronizationRule</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src115" class="srcSentence">Person</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src116" class="srcSentence">Group</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src117" class="srcSentence">On the Selected Attributes page, verify that all listed attributes are selected, and then click Next.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src118" class="srcSentence">	On the Configure Connector Filter page, click Next.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src119" class="srcSentence">On the Configure Object Type Mappings page, add the following mapping, and then click Next</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src120" class="srcSentence">In the Data Source Object Type list, select Person.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src121" class="srcSentence">To open the Mapping dialog box, click Add Mapping.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src122" class="srcSentence">In the Metaverse object type list, select person.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src123" class="srcSentence">To close the Mapping dialog box, click OK.</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src124" class="srcSentence">On the Configure Attribute Flow page, apply the following attribute flow mappings, and then click Next</caps:sentence>
                  </para>
                  <table border="1">
                    <tbody>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src125" class="srcSentence">Flow Direction</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src126" class="srcSentence">Data Source Attribute</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src127" class="srcSentence">Metaverse Attribute</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src128" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src129" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src130" class="srcSentence">accountName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src131" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src132" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src133" class="srcSentence">company</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src134" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src135" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src136" class="srcSentence">displayName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src137" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src138" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src139" class="srcSentence">employeeID</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src140" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src141" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src142" class="srcSentence">employeeType</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src143" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src144" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src145" class="srcSentence">firstName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src146" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src147" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src148" class="srcSentence">lastName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src149" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src150" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src151" class="srcSentence">Manager</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src152" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src153" class="srcSentence">Import</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src154" class="srcSentence">objectSid</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src155" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src156" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src157" class="srcSentence">accountName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src158" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src159" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src160" class="srcSentence">company</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src161" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src162" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src163" class="srcSentence">displayName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src164" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src165" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src166" class="srcSentence">domain</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src167" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src168" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src169" class="srcSentence">employeeID</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src170" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src171" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src172" class="srcSentence">employeeType</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src173" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src174" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src175" class="srcSentence">firstName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src176" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src177" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src178" class="srcSentence">lastName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src179" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src180" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src181" class="srcSentence">manager</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src182" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src183" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src184" class="srcSentence">objectSid</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src185" class="srcSentence">	Select Person as the Data source object type.</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src186" class="srcSentence">Select person as the Metaverse object type.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src187" class="srcSentence">Select Direct as the Mapping Type.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src188" class="srcSentence">For each row in the previous table, complete the following steps:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src189" class="srcSentence">Select the Flow Direction shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src190" class="srcSentence">Select the Data source attribute shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src191" class="srcSentence">Select the metaverse attribute shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src192" class="srcSentence">To apply the flow mapping, click New.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src193" class="srcSentence">Select Group as the data source type and as the metaverse object type.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src194" class="srcSentence">Select Direct as the Mapping Type.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src195" class="srcSentence">For each row in the following table, complete the following steps:
</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src196" class="srcSentence">Select the Flow Direction shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src197" class="srcSentence">Select the Data source attribute shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src198" class="srcSentence">Select the metaverse attribute shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src199" class="srcSentence">To apply the flow mapping, click New.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </listItem>
                  </list>
                  <table border="1">
                    <tbody>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src200" class="srcSentence">Flow Direction</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src201" class="srcSentence">Data Source Attribute</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src202" class="srcSentence">Metaverse Attribute</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src203" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src204" class="srcSentence">AccountName</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src205" class="srcSentence">accountName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src206" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src207" class="srcSentence">DisplayName</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src208" class="srcSentence">displayName</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src209" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src210" class="srcSentence">Domain</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src211" class="srcSentence">domain</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src212" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src213" class="srcSentence">Scope</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src214" class="srcSentence">scope</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src215" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src216" class="srcSentence">Type</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src217" class="srcSentence">type</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src218" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src219" class="srcSentence">Member</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src220" class="srcSentence">member</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src221" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src222" class="srcSentence">MembershipLocked</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src223" class="srcSentence">membershipLocked</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src224" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src225" class="srcSentence">MembershipAddWorkflow</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src226" class="srcSentence">membershipAddWorkflow</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>
                            <caps:sentence id="src227" class="srcSentence">Export</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src228" class="srcSentence">Manager</caps:sentence>
                          </para>
                        </TD>
                        <TD>
                          <para>
                            <caps:sentence id="src229" class="srcSentence">manager</caps:sentence>
                          </para>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src230" class="srcSentence">On the Configure Deprovisioning page, click Next</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src231" class="srcSentence">To create the management agent, on the Configure Extensions page, click Finish.</caps:sentence>
                  </para>
                </listItem>
              </list>
            </content>
          </section>
          <section>
            <title>
              <caps:sentence id="src232" class="srcSentence">Create the AD MA </caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence id="src233" class="srcSentence">The AD MA is a connector for AD DS.</caps:sentence>
                <caps:sentence id="src234" class="srcSentence"> To create this connector, you use the Create Management Agent wizard.</caps:sentence>
              </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <caps:sentence id="src235" class="srcSentence">To open the Create Management Agent wizard, on the Actions menu, click Create</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src236" class="srcSentence">On the Create Management Agent page, provide the following settings, and then click Next:</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src237" class="srcSentence">Management agent for: Active Directory Domain Services</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src238" class="srcSentence">Name: ADMA
</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src239" class="srcSentence">On the Connect to Active Directory Forest page, provide the following settings, and then click Next:
</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src240" class="srcSentence">	Forest name: contoso.local
</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src241" class="srcSentence">User name: administrator
</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src242" class="srcSentence">Password : &lt;the account’s password&gt;</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src243" class="srcSentence">Domain: contoso
</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src244" class="srcSentence">On the Configure Directory Partitions page, provide the following settings, and then click Next:
</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src245" class="srcSentence">In the Select directory partitions list, select DC=CONTOSO, DC=local.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src246" class="srcSentence">To open the Select Containers dialog box, click Containers.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src247" class="srcSentence">If you wish to change the container to only have MIM manage objects in a particular container, click the DC=CONTOSO,DC=local node, and then click the node for the container of interest.</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src248" class="srcSentence">To close the Select Containers dialog box, click  OK</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src249" class="srcSentence">On the Configure Provisioning Hierarchy page, click Next.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src250" class="srcSentence">On the Select Object Types page, provide the following settings, and then click Next</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src251" class="srcSentence">In the Object types list, select user and group.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src252" class="srcSentence">On the Select Attributes page, provide the following settings, and then click Next</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src253" class="srcSentence">Select Show All.</caps:sentence>
                  </para>
                  <para>
                    <caps:sentence id="src254" class="srcSentence">In the Attributes list, select the following attributes:</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src255" class="srcSentence">company</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src256" class="srcSentence">displayName</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src257" class="srcSentence">employeeID</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src258" class="srcSentence">employeeType</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src259" class="srcSentence">givenName</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src260" class="srcSentence">groupType</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src261" class="srcSentence">manager</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src262" class="srcSentence">managedBy</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src263" class="srcSentence">member</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src264" class="srcSentence">objectSid</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src265" class="srcSentence">sAMAccountName</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src266" class="srcSentence">sAMAccountType</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src267" class="srcSentence">sn</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src268" class="srcSentence">unicodePwd</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src269" class="srcSentence">userAccountControl</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src270" class="srcSentence">	On the Configure Connector Filter page, click Next.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src271" class="srcSentence">On the Configure Join and Projection Rues page, click Next.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src272" class="srcSentence">On the Configure Attribute Flow page, click Next.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src273" class="srcSentence">	On the Configure Deprovisioning page, click Next.</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src274" class="srcSentence">On the Configure Extensions page, click Finish.</caps:sentence>
                  </para>
                </listItem>
              </list>
            </content>
          </section>
          <section>
            <title>
              <caps:sentence id="src275" class="srcSentence">Create Run Profiles</caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence id="src276" class="srcSentence">Create run profiles for the  ADMA and MIMMA Connectors.</caps:sentence>
              </para>
            </content>
            <sections>
              <section>
                <title>
                  <caps:sentence id="src277" class="srcSentence">Create run profiles for the ADMA connector</caps:sentence>
                </title>
                <content>
                  <para>
                    <caps:sentence id="src278" class="srcSentence">Create the following profiles for the ADMA connector:</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src279" class="srcSentence">Profile1: Full Import (Stage Only)</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src280" class="srcSentence">Profile2: Full Synchronization</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src281" class="srcSentence">Profile3: Delta Import (Stage Only)</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src282" class="srcSentence">Profile4: Delta Synchronization</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src283" class="srcSentence">Profile5: Export</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                  <procedure>
                    <title>
                      <caps:sentence id="src284" class="srcSentence">To create run profiles for the ADMA connector:</caps:sentence>
                    </title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src285" class="srcSentence">Open the Synchronization Service Manager and, on the Tools menu, click Management Agents.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src286" class="srcSentence">In the Management Agents list, select ADMA.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src287" class="srcSentence">To open the Configure Run Profiles for dialog box, on the Actions menu, click Configure Run Profiles.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src288" class="srcSentence">	For each run profile in the table immediately above this procedure, complete the following steps:
</caps:sentence>
                          </para>
                          <list class="bullet">
                            <listItem>
                              <para>
                                <caps:sentence id="src289" class="srcSentence">To open the Configure Run Profile wizard, click New Profile.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence id="src290" class="srcSentence">In the Name box, type the profile name shown in the table, and click Next.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence id="src291" class="srcSentence">In the Type list, select the step type shown in the table, and then click Next.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence id="src292" class="srcSentence">Click Finish to create the run profile.</caps:sentence>
                              </para>
                            </listItem>
                          </list>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src293" class="srcSentence">To close the Configure Run Profiles dialog box, click OK.</caps:sentence>
                          </para>
                        </content>
                      </step>
                    </steps>
                  </procedure>
                </content>
              </section>
              <section>
                <title>
                  <caps:sentence id="src294" class="srcSentence">Create run profiles for the MIMMA connector</caps:sentence>
                </title>
                <content>
                  <para>
                    <caps:sentence id="src295" class="srcSentence">Create the following profiles for the MIMMA connector:</caps:sentence>
                  </para>
                  <list class="bullet">
                    <listItem>
                      <para>
                        <caps:sentence id="src296" class="srcSentence">Profile1: Full Import (Stage Only)</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src297" class="srcSentence">Profile2: Full Synchronization</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src298" class="srcSentence">Profile3: Delta Import (Stage Only)</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src299" class="srcSentence">Profile4: Delta Synchronization</caps:sentence>
                      </para>
                    </listItem>
                    <listItem>
                      <para>
                        <caps:sentence id="src300" class="srcSentence">Profile5: Export</caps:sentence>
                      </para>
                    </listItem>
                  </list>
                  <procedure>
                    <title>
                      <caps:sentence id="src301" class="srcSentence">To create run profiles for the MIMMA connector:</caps:sentence>
                    </title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src302" class="srcSentence">Open the Synchronization Service Manager and, on the Tools menu, click Management Agents.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src303" class="srcSentence">In the Management Agents list, select MIMMA.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src304" class="srcSentence">To open the Configure Run Profiles for dialog box, on the Actions menu, click Configure Run Profiles.</caps:sentence>
                          </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src305" class="srcSentence">	For each run profile in the table immediately above this procedure, complete the following steps:
</caps:sentence>
                          </para>
                          <list class="bullet">
                            <listItem>
                              <para>
                                <caps:sentence id="src306" class="srcSentence">To open the Configure Run Profile wizard, click New Profile.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence id="src307" class="srcSentence">In the Name box, type the profile name shown in the table, and click Next.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence id="src308" class="srcSentence">In the Type list, select the step type shown in the table, and then click Next.</caps:sentence>
                              </para>
                            </listItem>
                            <listItem>
                              <para>
                                <caps:sentence id="src309" class="srcSentence">Click Finish to create the run profile.</caps:sentence>
                              </para>
                            </listItem>
                          </list>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>
                            <caps:sentence id="src310" class="srcSentence">To close the Configure Run Profiles dialog box, click OK.</caps:sentence>
                          </para>
                        </content>
                      </step>
                    </steps>
                  </procedure>
                </content>
              </section>
            </sections>
          </section>
          <section>
            <title>
              <caps:sentence id="src311" class="srcSentence">Configuring the MIM Service</caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence id="src312" class="srcSentence">For the scenario in this document, you perform the following steps in the MIM Service, using the MIM Portal:</caps:sentence>
              </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <caps:sentence id="src313" class="srcSentence">Create the AD user inbound synchronization rule</caps:sentence>
                  </para>
                </listItem>
              </list>
              <procedure>
                <title>
                  <caps:sentence id="src314" class="srcSentence">To create the AD user inbound synchronization rule
</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src315" class="srcSentence">On the MIM portal home page, on the navigation bar, click Administration.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src316" class="srcSentence">To open the Synchronization Rules page, click Synchronization Rules.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src317" class="srcSentence">To open the Create Synchronization Rule wizard, in the toolbar, click New.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src318" class="srcSentence">On the General tab, provide the following information, and then click Next:
</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src319" class="srcSentence">Display Name: AD User Inbound Synchronization Rule
</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src320" class="srcSentence">Data Flow Direction: Inbound</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src321" class="srcSentence">On the Scope tab, provide the following information, and then click Next:
</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src322" class="srcSentence">Metaverse Resource Type: person</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src323" class="srcSentence">External System: ADMA</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src324" class="srcSentence">External System Resource Type: person
</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src325" class="srcSentence">On the Relationship tab, provide the following information, and then click Next</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src326" class="srcSentence">To configure the Relationship Criteria, select objectSID from the MetaverseObject:person(Attribute) list and ObjectSID from the ConnectedSystemObject:person(Attribute)list.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src327" class="srcSentence">Select Create Resource In FIM.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src328" class="srcSentence">On the Inbound Attribute Flow page, provide the following information, and then click Next:
 
</caps:sentence>
                      </para>
                      <table border="1">
                        <tbody>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence id="src329" class="srcSentence">Flow Rule</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src330" class="srcSentence">Source</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src331" class="srcSentence">Destination</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence id="src332" class="srcSentence">Rule 1</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src333" class="srcSentence">samAccountName</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src334" class="srcSentence">f</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence id="src335" class="srcSentence">Rule 2</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <caps:sentence id="src336" class="srcSentence"> <para>displayName</para></caps:sentence>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src337" class="srcSentence">displayName</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence id="src338" class="srcSentence">Rule 3</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src339" class="srcSentence">EmployeeType</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src340" class="srcSentence">EmployeeType</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence id="src341" class="srcSentence">Rule 4</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src342" class="srcSentence">givenName</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src343" class="srcSentence">givenName</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence id="src344" class="srcSentence">Rule 5</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src345" class="srcSentence">sn</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src346" class="srcSentence">lastName</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence id="src347" class="srcSentence">Rule 6</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src348" class="srcSentence">Manager</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src349" class="srcSentence">manager</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence id="src350" class="srcSentence">Rule 7</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src351" class="srcSentence">objectSID</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src352" class="srcSentence">ObjectSID</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                          <tr>
                            <TD>
                              <para>
                                <caps:sentence id="src353" class="srcSentence">Rule 8</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src354" class="srcSentence">"Contoso"</caps:sentence>
                              </para>
                            </TD>
                            <TD>
                              <para>
                                <caps:sentence id="src355" class="srcSentence">domain</caps:sentence>
                              </para>
                            </TD>
                          </tr>
                        </tbody>
                      </table>
                      <para>
                        <caps:sentence id="src356" class="srcSentence">For each row in this table, perform the following steps:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src357" class="srcSentence">To open the Flow Definition dialog box, click New Attribute Flow</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src358" class="srcSentence">On the Source tab, select the attribute shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src359" class="srcSentence">On the Destination tab, select the attribute shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src360" class="srcSentence">To apply the attribute flow configuration, click OK.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src361" class="srcSentence">On the Summary tab, click Submit.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
            </content>
          </section>
          <section>
            <title>
              <caps:sentence id="src362" class="srcSentence">Initializing the testing environment</caps:sentence>
            </title>
            <content>
              <para>
                <caps:sentence id="src363" class="srcSentence">Before you can test your configuration with your AD data, you need to initialize the configuration.</caps:sentence>
                <caps:sentence id="src364" class="srcSentence"> The following steps are part of this process:</caps:sentence>
              </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <caps:sentence id="src365" class="srcSentence">Enabling provisioning</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src366" class="srcSentence">Initializing the MIMMA</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src367" class="srcSentence">Configuring attribute flow precedence</caps:sentence>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <caps:sentence id="src368" class="srcSentence">Initializing the ADMA</caps:sentence>
                  </para>
                </listItem>
              </list>
              <procedure>
                <title>
                  <caps:sentence id="src369" class="srcSentence">To enable Provisioning</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src370" class="srcSentence">Open the Synchronization Service Manager.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src371" class="srcSentence">To open the Options dialog box, on the Tools menu, click Options</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src372" class="srcSentence">Select Enable Synchronization Rule Provisioning.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src373" class="srcSentence">To close the Options dialog box, click OK.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure>
                <title>
                  <caps:sentence id="src374" class="srcSentence">To initialize the MIMMA</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src375" class="srcSentence">run a complete synchronization cycle on this connector.</caps:sentence>
                        <caps:sentence id="src376" class="srcSentence"> The complete cycle consists of the following run profile runs:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src377" class="srcSentence">Full Import</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src378" class="srcSentence">Full Synchronization</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src379" class="srcSentence">Export</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src380" class="srcSentence">Delta Import</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src381" class="srcSentence">	Open the Synchronization Service Manager and on the Tools menu, click Management Agents.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src382" class="srcSentence">	In the Management Agents list, select MIMMA
</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src383" class="srcSentence">To open the Run Management Agent dialog box, on the Actions menu, click Run.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src384" class="srcSentence">For each row in the table immediately above this procedure, complete the following steps:
</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src385" class="srcSentence">To open the Run Management Agent dialog box, on the Actions menu, click Run.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src386" class="srcSentence">In the Run profiles list, select the run profile shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src387" class="srcSentence">	To start the run profile, click OK.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure>
                <title>
                  <caps:sentence id="src388" class="srcSentence">Configuring attribute flow precedence</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src389" class="srcSentence">During the initialization of the MIM connector, the configured synchronization rules have been brought into the metaverse.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src390" class="srcSentence">Adjust the attribute flow precedence for the attributes contributed by this connector to ensure that attributes already in AD can flow into the metaverse and later also into the MIM Service database.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure>
                <title>
                  <caps:sentence id="src391" class="srcSentence">Initializing the ADMA</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src392" class="srcSentence">To initialize the Active Directory connector, you need to run a full import and a full synchronization on it.</caps:sentence>
                        <caps:sentence id="src393" class="srcSentence"> The full import is required to bring the existing objects from AD into the connector space.</caps:sentence>
                        <caps:sentence id="src394" class="srcSentence"> The full synchronization is required because the synchronization rules have changed by projecting the new synchronization rules from the MIM connector space into the metaverse.</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src395" class="srcSentence">Step 1: Run Full Import</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src396" class="srcSentence">Step 2: Run Full Synchronization</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src397" class="srcSentence">Open the Synchronization Service Manager and in the Tools menu, click Management Agents.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src398" class="srcSentence">In the Management Agents list, select ADMA.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src399" class="srcSentence">To open the Run Management Agent dialog box, on the Actions menu, click Run.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src400" class="srcSentence">For each row in the table immediately above this procedure, complete the following steps:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src401" class="srcSentence">To open the Run Management Agent dialog box, on the Actions menu, click Run.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src402" class="srcSentence">In the Run profiles list, select the run profile shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src403" class="srcSentence">	To start the run profile, click OK.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure>
                <title>
                  <caps:sentence id="src404" class="srcSentence">Populating the MIM Service database</caps:sentence>
                </title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src405" class="srcSentence">To populate the MIM Service database with the objects, you need to run a synchronization cycle on the MIMMA connector.</caps:sentence>
                        <caps:sentence id="src406" class="srcSentence"> The cycle consists of the following run profile runs:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src407" class="srcSentence">1: Export</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src408" class="srcSentence">2: Full Import</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src409" class="srcSentence">3: Full Sync</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src410" class="srcSentence">Open the Synchronization Service Manager and on the Tools menu, click Management Agents.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src411" class="srcSentence">	In the Management Agents list, select MIMMA
</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src412" class="srcSentence">	To open the Run Management Agent dialog box, on the Actions menu, click Run.</caps:sentence>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src413" class="srcSentence">For each row in the table immediately above this procedure, complete the following steps:</caps:sentence>
                      </para>
                      <list class="bullet">
                        <listItem>
                          <para>
                            <caps:sentence id="src414" class="srcSentence">To open the Run Management Agent dialog box, on the Actions menu, click Run.</caps:sentence>
                          </para>
                        </listItem>
                        <listItem>
                          <para>
                            <caps:sentence id="src415" class="srcSentence">In the Run profiles list, select the run profile shown for that row in the table.</caps:sentence>
                          </para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>
                        <caps:sentence id="src416" class="srcSentence">	To start the run profile, click OK.</caps:sentence>
                      </para>
                    </content>
                  </step>
                </steps>
              </procedure>
            </content>
          </section>
        </sections>
      </section>
      <relatedTopics></relatedTopics>
    </developerConceptualDocument>
  </caps:SxSSource>
</caps:SxS>