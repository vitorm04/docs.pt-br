---
title: Segurança (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- XAML files [WPF], sandbox behavior
- browser-hosted application security [WPF]
- application security [WPF]
- navigation security [WPF]
- loose XAML files [WPF], sandbox behavior
- WPF security [WPF]
- WebBrowser control [WPF], security
- feature controls [WPF], security
- XBAP security [WPF]
- Internet Explorer security settings [WPF]
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
ms.openlocfilehash: 031313c6f56801f032a5aeaff06cde8d0550af92
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582408"
---
# <a name="security-wpf"></a>Segurança (WPF)
<a name="introduction"></a>Ao desenvolver Windows Presentation Foundation (WPF) aplicativos autônomos e hospedados em navegador, você deve considerar o modelo de segurança. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos autônomos são executados com permissões irrestritas (conjunto de permissões do CAS**FullTrust** ), sejam implantados usando Windows Installer (. msi), xcopy ou ClickOnce. Não há suporte para a implantação de aplicativos WPF autônomos e de confiança parcial com o ClickOnce. No entanto, um aplicativo de host totalmente confiável pode criar um <xref:System.AppDomain> de confiança parcial usando o modelo de suplemento de .NET Framework. Para obter mais informações, consulte [visão geral dos suplementos do WPF](./app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos hospedados em navegador são hospedados pelo Windows Internet Explorer ou pelo Firefox e podem ser [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] ou [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] documentos soltos para obter mais informações, consulte [visão geral de aplicativos de navegador XAML WPF](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos hospedados em navegador são executados em uma área de segurança de confiança parcial, por padrão, que é limitada ao conjunto de permissões de zona da**Internet** CAS padrão. Isso isola efetivamente [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos hospedados por navegador do computador cliente da mesma forma que você esperaria que aplicativos Web típicos fossem isolados. Um XBAP é capaz de elevar privilégios, até confiança total, dependendo da zona de segurança da URL de implantação e da configuração de segurança do cliente. Para obter mais informações, consulte [Segurança parcialmente confiável do WPF](wpf-partial-trust-security.md).  
  
 Este tópico discute o modelo de segurança para aplicativos do Windows Presentation Foundation (WPF) autônomos e hospedados em navegador.  
  
 Esse tópico contém as seguintes seções:  
  
- [Navegação segura](#SafeTopLevelNavigation)  
  
- [Configurações de segurança de software de navegação na Web](#InternetExplorerSecuritySettings)  
  
- [Controle WebBrowser e controles de recurso](#webbrowser_control_and_feature_controls)  
  
- [Desabilitando os assemblies APTCA para aplicativos cliente parcialmente confiáveis](#APTCA)  
  
- [Comportamento da área restrita para arquivos XAML flexíveis](#LooseContentSandboxing)  
  
- [Recursos para o desenvolvimento de aplicativos do WPF que promovem a segurança](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Navegação segura  
 Por [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] distingue dois tipos de navegação: aplicativo e navegador.  
  
 *A navegação do aplicativo* é uma navegação entre itens de conteúdo dentro de um aplicativo hospedado por um navegador. *A navegação do navegador* é uma navegação que muda a URL de local e conteúdo do próprio navegador. A relação entre a navegação do aplicativo (normalmente XAML) e a navegação do navegador (normalmente HTML) é mostrada na ilustração a seguir:
  
 ![Relação entre navegação do aplicativo e navegação do navegador.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 O tipo de conteúdo que é considerado seguro para um [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] navegar é determinado principalmente pelo fato de a navegação do aplicativo ou da navegação do navegador ser usada.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Segurança da navegação do aplicativo  
 A navegação do aplicativo é considerada segura se puder ser identificada com um pacote URI, que dá suporte a quatro tipos de conteúdo:  
  
|Tipo de Conteúdo|Descrição|Exemplo de URI|  
|------------------|-----------------|-----------------|  
|Recurso|Arquivos que são adicionados a um projeto com um tipo de **recurso**de compilação.|`pack://application:,,,/MyResourceFile.xaml`|  
|Conteúdo|Arquivos que são adicionados a um projeto com um tipo de **conteúdo**de compilação.|`pack://application:,,,/MyContentFile.xaml`|  
|Site de origem|Arquivos que são adicionados a um projeto com um tipo de compilação **nenhum**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Código do aplicativo|Recursos XAML que têm um code-behind compilado.<br /><br /> \- ou -<br /><br /> Arquivos XAML que são adicionados a um projeto com um tipo de compilação de **página**.|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
> Para obter mais informações sobre os arquivos de dados de aplicativo e URIs de pacote, consulte [recursos de aplicativo WPF, conteúdo e arquivos de dados](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 É possível navegar até arquivos desses tipos de conteúdo por meio do usuário ou programaticamente:  
  
- **Navegação do usuário**. O usuário navega clicando em um elemento <xref:System.Windows.Documents.Hyperlink>.  
  
- **Navegação programática**. O aplicativo navega sem envolver o usuário, por exemplo, definindo a propriedade <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Segurança da navegação do navegador  
 A navegação do navegador é considerada segura somente nestas condições:  
  
- **Navegação do usuário**. O usuário navega clicando em um elemento <xref:System.Windows.Documents.Hyperlink> que está dentro do <xref:System.Windows.Navigation.NavigationWindow> principal, não em um <xref:System.Windows.Controls.Frame> aninhado.  
  
- **Zona**. O conteúdo da navegação localiza-se na Internet ou na intranet local.  
  
- **Protocolo**. O protocolo que está sendo usado é **http**, **https**, **File**ou **mailto**.  
  
 Se um [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] tentar navegar até o conteúdo de uma maneira que não esteja em conformidade com essas condições, uma <xref:System.Security.SecurityException> será lançada.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Configurações de segurança de software de navegação na Web  
 As configurações de segurança no seu computador determinam o acesso concedido a qualquer software de navegação Web. O software de navegação na Web inclui qualquer aplicativo ou componente que usa as APIs [WinInet](https://go.microsoft.com/fwlink/?LinkId=179379) ou [Urlmon](https://go.microsoft.com/fwlink/?LinkId=179383) , incluindo o Internet Explorer e o PresentationHost. exe.  
  
 O Internet Explorer fornece um mecanismo pelo qual você pode configurar a funcionalidade que tem permissão para ser executada pelo ou do Internet Explorer, incluindo o seguinte:  
  
- Componentes dependentes de .NET Framework  
  
- Controles ActiveX e plug-ins  
  
- Downloads  
  
- Script  
  
- Autenticação do usuário  
  
 A coleção de funcionalidades que podem ser protegidas dessa maneira é configurada por zona para a **Internet**, **intranet**, **sites confiáveis**e zonas de **sites restritos** . As etapas a seguir descrevem como definir as configurações de segurança:  
  
1. Abra **Painel de Controle**.  
  
2. Clique em **rede e Internet** e em **Opções da Internet**.  
  
     É exibida a caixa de diálogo Opções da Internet.  
  
3. Na guia **segurança** , selecione a zona para definir as configurações de segurança.  
  
4. Clique no botão **nível personalizado** .  
  
     A caixa de diálogo **configurações de segurança** é exibida e você pode definir as configurações de segurança para a zona selecionada.  
  
     ![Captura de tela que mostra a caixa de diálogo Configurações de segurança.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> Também é possível acessar a caixa de diálogo Opções da Internet pelo Internet Explorer. Clique em **ferramentas** e em **Opções da Internet**.  
  
 A partir do Windows Internet Explorer 7, as seguintes configurações de segurança especificamente para .NET Framework estão incluídas:  
  
- **XAML flexível**. Controla se o Internet Explorer pode navegar e soltar [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivos. (Opções de Habilitar, Desabilitar e Prompt.)  
  
- **Aplicativos do navegador XAML**. Controla se o Internet Explorer pode navegar e executar [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. (Opções de Habilitar, Desabilitar e Prompt.)  
  
 Por padrão, essas configurações são todas habilitadas para as zonas **Internet**, **intranet local**e **sites confiáveis** e desabilitadas para a zona de **sites restritos** .  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>Configurações do Registro de WPF relacionadas à segurança  
 Além das configurações de segurança disponíveis por meio das Opções da Internet, os valores de Registro a seguir estão disponíveis para bloquear seletivamente alguns recursos do WPF sensíveis à segurança. Os valores são definidos na seguinte chave:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 A tabela a seguir lista os valores que podem ser definidos.  
  
|Nome do valor|Tipo do Valor|Dados do valor|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|1 para não permitir; 0 para permitir.|  
|LooseXamlDisallow|REG_DWORD|1 para não permitir; 0 para permitir.|  
|WebBrowserDisallow|REG_DWORD|1 para não permitir; 0 para permitir.|  
|MediaAudioDisallow|REG_DWORD|1 para não permitir; 0 para permitir.|  
|MediaImageDisallow|REG_DWORD|1 para não permitir; 0 para permitir.|  
|MediaVideoDisallow|REG_DWORD|1 para não permitir; 0 para permitir.|  
|ScriptInteropDisallow|REG_DWORD|1 para não permitir; 0 para permitir.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>Controle WebBrowser e controles de recurso  
 O controle de <xref:System.Windows.Controls.WebBrowser> do WPF pode ser usado para hospedar conteúdo da Web. O controle de <xref:System.Windows.Controls.WebBrowser> do WPF encapsula o controle ActiveX do WebBrowser subjacente. O WPF fornece algum suporte para proteger seu aplicativo quando você usa o controle de <xref:System.Windows.Controls.WebBrowser> do WPF para hospedar conteúdo da Web não confiável. No entanto, alguns recursos de segurança devem ser aplicados diretamente pelos aplicativos usando o controle de <xref:System.Windows.Controls.WebBrowser>. Para obter mais informações sobre o controle ActiveX do WebBrowser, consulte [visões gerais do controle WebBrowser e tutoriais](https://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
> Esta seção também se aplica ao controle de <xref:System.Windows.Controls.Frame>, já que ele usa o <xref:System.Windows.Controls.WebBrowser> para navegar até o conteúdo HTML.  
  
 Se o controle de <xref:System.Windows.Controls.WebBrowser> do WPF for usado para hospedar conteúdo da Web não confiável, seu aplicativo deverá usar um <xref:System.AppDomain> de confiança parcial para ajudar a isolar o código do aplicativo de código de script HTML potencialmente mal-intencionado. Isso é especialmente verdadeiro se seu aplicativo estiver interagindo com o script hospedado usando o método <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> e a propriedade <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>. Para obter mais informações, consulte [visão geral dos suplementos do WPF](./app-development/wpf-add-ins-overview.md).  
  
 Se seu aplicativo usa o controle de <xref:System.Windows.Controls.WebBrowser> do WPF, outra maneira de aumentar a segurança e mitigar os ataques é habilitar os controles de recursos do Internet Explorer. Os controles de recurso são adições ao Internet Explorer que permitem que administradores e desenvolvedores configurem recursos do Internet Explorer e aplicativos que hospedam o controle ActiveX do WebBrowser, que o controle de <xref:System.Windows.Controls.WebBrowser> do WPF encapsula. Os controles de recurso podem ser configurados usando a função [CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394) ou alterando os valores no registro. Para obter mais informações sobre controles de recursos, consulte [introdução aos controles de recursos](https://go.microsoft.com/fwlink/?LinkId=179390) e [controles de recursos da Internet](https://go.microsoft.com/fwlink/?LinkId=179392).  
  
 Se você estiver desenvolvendo um aplicativo WPF autônomo que usa o controle de <xref:System.Windows.Controls.WebBrowser> do WPF, o WPF habilita automaticamente os seguintes controles de recurso para seu aplicativo.  
  
|Controle de recurso|  
|---------------------|  
|FEATURE_MIME_HANDLING|  
|FEATURE_MIME_SNIFFING|  
|FEATURE_OBJECT_CACHING|  
|FEATURE_SAFE_BINDTOOBJECT|  
|FEATURE_WINDOW_RESTRICTIONS|  
|FEATURE_ZONE_ELEVATION|  
|FEATURE_RESTRICT_FILEDOWNLOAD|  
|FEATURE_RESTRICT_ACTIVEXINSTALL|  
|FEATURE_ADDON_MANAGEMENT|  
|FEATURE_HTTP_USERNAME_PASSWORD_DISABLE|  
|FEATURE_SECURITYBAND|  
|FEATURE_UNC_SAVEDFILECHECK|  
|FEATURE_VALIDATE_NAVIGATE_URL|  
|FEATURE_DISABLE_TELNET_PROTOCOL|  
|FEATURE_WEBOC_POPUPMANAGEMENT|  
|FEATURE_DISABLE_LEGACY_COMPRESSION|  
|FEATURE_SSLUX|  
  
 Como esses controles de recurso são habilitados incondicionalmente, um aplicativo de confiança total pode ser prejudicado por eles. Nesse caso, se não houver risco de segurança para o aplicativo específico e o conteúdo hospedado por ele, o controle de recurso correspondente poderá ser desabilitado.  
  
 Os controles de recurso são aplicados pelo processo instanciando o objeto ActiveX do WebBrowser. Portanto, se estiver criando um aplicativo autônomo capaz de navegar até o conteúdo não confiável, considere seriamente a possibilidade de habilitar controles de recurso adicionais.  
  
> [!NOTE]
> Essa recomendação baseia-se em recomendações gerais para segurança do host MSHTML e SHDOCVW. Para obter mais informações, consulte [as perguntas frequentes sobre segurança de host MSHTML: parte I de II](https://go.microsoft.com/fwlink/?LinkId=179396) e [as perguntas frequentes sobre segurança de host MSHTML: parte II de II](https://go.microsoft.com/fwlink/?LinkId=179415).  
  
 Para o executável, considere a possibilidade de habilitar os controles de recurso a seguir ao definir o valor de Registro como 1.  
  
|Controle de recurso|  
|---------------------|  
|FEATURE_ACTIVEX_REPURPOSEDETECTION|  
|FEATURE_BLOCK_LMZ_IMG|  
|FEATURE_BLOCK_LMZ_OBJECT|  
|FEATURE_BLOCK_LMZ_SCRIPT|  
|FEATURE_RESTRICT_RES_TO_LMZ|  
|FEATURE_RESTRICT_ABOUT_PROTOCOL_IE7|  
|FEATURE_SHOW_APP_PROTOCOL_WARN_DIALOG|  
|FEATURE_LOCALMACHINE_LOCKDOWN|  
|FEATURE_FORCE_ADDR_AND_STATUS|  
|FEATURE_RESTRICTED_ZONE_WHEN_FILE_NOT_FOUND|  
  
 Para o executável, considere a possibilidade de desabilitar o controle de recurso a seguir ao definir o valor de Registro como 0.  
  
|Controle de recurso|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Se você executar um [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] de confiança parcial que inclua um controle de <xref:System.Windows.Controls.WebBrowser> do WPF no Windows Internet Explorer, o WPF hospedará o controle WebBrowser ActiveX no espaço de endereço do processo do Internet Explorer. Como o controle ActiveX do WebBrowser é hospedado no processo do Internet Explorer, todos os controles de recurso do Internet Explorer também estão habilitados para o controle ActiveX do WebBrowser.  
  
 Os XBAPs executados no Internet Explorer também têm um nível adicional de segurança em comparação com aplicativos autônomos normais. Essa segurança adicional ocorre porque o Internet Explorer e, portanto, o controle ActiveX do WebBrowser, é executado no modo protegido por padrão em [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] e [!INCLUDE[win7](../../../includes/win7-md.md)]. Para obter mais informações sobre o modo protegido, consulte [compreendendo e trabalhando no modo protegido do Internet Explorer](https://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
> Se você tentar executar um XBAP que inclui um controle de <xref:System.Windows.Controls.WebBrowser> WPF no Firefox, enquanto estiver na zona da Internet, uma <xref:System.Security.SecurityException> será lançada. Isso ocorre por causa da política de segurança do WPF.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Desabilitando os assemblies APTCA para aplicativos cliente parcialmente confiáveis  
 Quando os assemblies gerenciados são instalados no GAC (cache de assembly global), eles se tornam totalmente confiáveis, pois o usuário deve fornecer permissão explícita para instalá-los. Como são totalmente confiáveis, apenas aplicativos clientes gerenciados totalmente confiáveis podem usá-los. Para permitir que aplicativos parcialmente confiáveis os usem, eles devem ser marcados com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Somente assemblies que foram testados em relação à segurança para execução com confiança parcial devem ser marcados com tal atributo.  
  
 No entanto, é possível que um assembly APTCA exiba uma falha de segurança depois de ser instalado no GAC. Após a descoberta de uma falha de segurança, os publicadores de assembly podem produzir uma atualização de segurança para corrigir o problema em instalações existentes, além de protege de instalações que poderão ocorrer após a descoberta do problema. Uma opção para a atualização é desinstalar o assembly, embora isso possa interromper outros aplicativos clientes totalmente confiáveis que o utilizam.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] fornece um mecanismo pelo qual um assembly APTCA pode ser desabilitado para [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] parcialmente confiável sem desinstalar o assembly APTCA.  
  
 Para desabilitar um assembly APTCA, é necessário criar uma chave do Registro especial:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Um exemplo é mostrado a seguir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Essa chave estabelece uma entrada para o assembly APTCA. Você também precisa criar um valor nessa chave que habilite ou desabilite o assembly. Abaixo estão os detalhes do valor:  
  
- Nome do valor: **APTCA_FLAG**.  
  
- Tipo de valor: **REG_DWORD**.  
  
- Dados do valor: **1** para desabilitar; **0** para habilitar.  
  
 Caso seja necessário desabilitar um assembly para aplicativos clientes parcialmente confiáveis, você pode gravar uma atualização que crie a chave do Registro e o valor.  
  
> [!NOTE]
> Os assemblies de .NET Framework principal não são afetados desabilitando-os dessa forma porque eles são necessários para que os aplicativos gerenciados sejam executados. O suporte para desabilitar assemblies APTCA é destinado principalmente a aplicativos de terceiros.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Comportamento da área restrita para arquivos XAML flexíveis  
 Arquivos de [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] flexíveis são arquivos XAML somente de marcação que não dependem de qualquer código-behind, manipulador de eventos ou assembly específico do aplicativo. Quando soltos [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivos são navegados diretamente do navegador, eles são carregados em uma área restrita de segurança com base no conjunto de permissões de zona da Internet padrão.  
  
 No entanto, o comportamento de segurança é diferente quando os arquivos flexíveis [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] são navegados de um <xref:System.Windows.Navigation.NavigationWindow> ou <xref:System.Windows.Controls.Frame> em um aplicativo autônomo.  
  
 Em ambos os casos, o arquivo de [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] flexível que é navegado para herda as permissões de seu aplicativo host. No entanto, esse comportamento pode ser indesejável de uma perspectiva de segurança, especialmente se um arquivo de [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] flexível for produzido por uma entidade que não seja confiável ou desconhecida. Esse tipo de conteúdo é conhecido como *conteúdo externo*, e os <xref:System.Windows.Controls.Frame> e <xref:System.Windows.Navigation.NavigationWindow> podem ser configurados para isolá-lo quando navegados para o. O isolamento é obtido definindo a propriedade **SandboxExternalContent** como true, conforme mostrado nos exemplos a seguir para <xref:System.Windows.Controls.Frame> e <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Com essa configuração, o conteúdo externo será carregado em um processo separado do processo que está hospedando o aplicativo. Esse processo restringe-se ao conjunto de permissões da zona da Internet padrão, isolando-o eficazmente do aplicativo host e do computador cliente.  
  
> [!NOTE]
> Embora a navegação para arquivos soltos [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] de um <xref:System.Windows.Navigation.NavigationWindow> ou <xref:System.Windows.Controls.Frame> em um aplicativo autônomo seja implementada com base na infraestrutura de hospedagem do navegador do WPF, envolvendo o processo do PresentationHost, o nível de segurança é um pouco menor do que quando o o conteúdo é carregado diretamente no Internet Explorer em [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] e [!INCLUDE[win7](../../../includes/win7-md.md)] (que ainda seria por meio do PresentationHost). Isso ocorre porque um aplicativo autônomo do WPF que usa um navegador da Web não oferece o recurso de segurança adicional de modo protegido do Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Recursos para o desenvolvimento de aplicativos do WPF que promovem a segurança  
 A seguir estão alguns recursos adicionais para ajudar a desenvolver [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos que promovem a segurança:  
  
|Área|Recurso|  
|----------|--------------|  
|Código gerenciado|[Padrões e práticas de orientação de segurança para aplicativos](https://go.microsoft.com/fwlink/?LinkId=117426)|  
|CAS|[Segurança de acesso do código](../misc/code-access-security.md)|  
|ClickOnce|[Segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[Segurança parcialmente confiável do WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Consulte também

- [Segurança parcialmente confiável do WPF](wpf-partial-trust-security.md)
- [Estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)
- [Estratégia de segurança do WPF – Engenharia de segurança](wpf-security-strategy-security-engineering.md)
- [Padrões e práticas de orientação de segurança para aplicativos](https://go.microsoft.com/fwlink/?LinkId=117426)
- [Segurança de acesso do código](../misc/code-access-security.md)
- [Segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Visão geral de XAML (WPF)](./advanced/xaml-overview-wpf.md)
