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
ms.openlocfilehash: 968913a52a1d86746498aed7c97b63594d346a31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696767"
---
# <a name="security-wpf"></a>Segurança (WPF)
<a name="introduction"></a> Ao desenvolver autônomo do Windows Presentation Foundation (WPF) e aplicativos hospedados pelo navegador, você deve considerar o modelo de segurança. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos autônomos executados com permissões ilimitadas ( [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **FullTrust** conjunto de permissões), se implantado usando o Windows Installer (. msi), XCopy, ou [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]. Não há suporte para a implantação de aplicativos WPF autônomos e de confiança parcial com o ClickOnce. No entanto, um aplicativo host de confiança total pode criar uma confiança parcial <xref:System.AppDomain> usando o modelo de suplemento do .NET Framework. Para obter mais informações, consulte [visão geral de suplementos WPF](./app-development/wpf-add-ins-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos hospedados pelo navegador são hospedados por [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)] ou o Firefox, e pode ser [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] ou flexível [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] documentos para obter mais informações, consulte [visão geral dos aplicativos de navegador XAML do WPF](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos hospedados pelo navegador executam em uma área de restrita de segurança de confiança parcial, por padrão, que é limitado ao padrão [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **Internet** conjunto de permissões da zona. Isso isola efetivamente [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos hospedados pelo navegador do computador cliente da mesma forma que você esperaria que aplicativos Web típicos fossem isolados. Um XBAP é capaz de elevar privilégios, até confiança total, dependendo da zona de segurança da URL de implantação e da configuração de segurança do cliente. Para obter mais informações, consulte [Segurança parcialmente confiável do WPF](wpf-partial-trust-security.md).  
  
 Este tópico discute o modelo de segurança para autônomo do Windows Presentation Foundation (WPF) e aplicativos hospedados pelo navegador.  
  
 Esse tópico contém as seguintes seções:  
  
- [Navegação segura](#SafeTopLevelNavigation)  
  
- [Configurações de segurança de software de navegação na Web](#InternetExplorerSecuritySettings)  
  
- [Controle WebBrowser e controles de recurso](#webbrowser_control_and_feature_controls)  
  
- [Desabilitando os assemblies APTCA para aplicativos cliente parcialmente confiáveis](#APTCA)  
  
- [Comportamento da área restrita para arquivos XAML flexíveis](#LooseContentSandboxing)  
  
- [Recursos para o desenvolvimento de aplicativos do WPF que promovem a segurança](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Navegação segura  
 Para [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] distingue dois tipos de navegação: aplicativo e navegador.  
  
 *A navegação do aplicativo* é uma navegação entre itens de conteúdo dentro de um aplicativo hospedado por um navegador. *A navegação do navegador* é uma navegação que muda a URL de local e conteúdo do próprio navegador. A relação entre a navegação de aplicativo (normalmente XAML) e navegação do navegador (normalmente HTML) é mostrada na ilustração a seguir:
  
 ![Relação entre a navegação em aplicativos e navegação do navegador.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 O tipo de conteúdo que é considerado seguro para um [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] navegar até é determinado principalmente pelo se a navegação do aplicativo ou navegação do navegador é usada.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Segurança da navegação do aplicativo  
 Navegação do aplicativo é considerada segura se ele pode ser identificado com um pacote [!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)], que oferece suporte a quatro tipos de conteúdo:  
  
|Tipo de Conteúdo|Descrição|Exemplo de URI|  
|------------------|-----------------|-----------------|  
|Recurso|Arquivos que são adicionados a um projeto com um tipo de compilação do **recurso**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Conteúdo|Arquivos que são adicionados a um projeto com um tipo de compilação do **conteúdo**.|`pack://application:,,,/MyContentFile.xaml`|  
|Site de origem|Arquivos que são adicionados a um projeto com um tipo de compilação do **None**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Código do aplicativo|Recursos XAML que têm um code-behind compilado.<br /><br /> - ou -<br /><br /> Arquivos XAML que são adicionados a um projeto com um tipo de compilação do **página**.|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
>  Para obter mais informações sobre arquivos de dados do aplicativo e o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)], consulte [recurso de aplicativo do WPF, conteúdo e arquivos de dados](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 É possível navegar até arquivos desses tipos de conteúdo por meio do usuário ou programaticamente:  
  
- **Navegação do usuário**. O usuário navega, clicando em um <xref:System.Windows.Documents.Hyperlink> elemento.  
  
- **Navegação programática**. O aplicativo navega sem envolver o usuário, por exemplo, definindo o <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> propriedade.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Segurança da navegação do navegador  
 A navegação do navegador é considerada segura somente nestas condições:  
  
- **Navegação do usuário**. O usuário navega, clicando em um <xref:System.Windows.Documents.Hyperlink> elemento que está dentro do principal <xref:System.Windows.Navigation.NavigationWindow>, e não no aninhado <xref:System.Windows.Controls.Frame>.  
  
- **Zona**. O conteúdo da navegação localiza-se na Internet ou na intranet local.  
  
- **Protocolo**. É o protocolo usado **http**, **https**, **arquivo**, ou **mailto**.  
  
 Se um [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] tenta navegar até o conteúdo de uma maneira que não são compatíveis com essas condições, um <xref:System.Security.SecurityException> é gerada.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Configurações de segurança de software de navegação na Web  
 As configurações de segurança no seu computador determinam o acesso concedido a qualquer software de navegação Web. Navegador da Web inclui qualquer aplicativo ou componente que usa o [WinINet](https://go.microsoft.com/fwlink/?LinkId=179379) ou [UrlMon](https://go.microsoft.com/fwlink/?LinkId=179383) APIs, incluindo o Internet Explorer e PresentationHost.exe.  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] Fornece um mecanismo pelo qual você pode configurar a funcionalidade que pode ser executada por ou de [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)], incluindo o seguinte:  
  
- Componentes dependentes do framework .NET  
  
- Controles ActiveX e plug-ins  
  
- Downloads  
  
- Script  
  
- Autenticação do usuário  
  
 A coleção de funcionalidade que pode ser protegida dessa maneira é configurada em uma base por zona para o **Internet**, **Intranet**, **Sites confiáveis**, e  **Sites restritos** zonas. As etapas a seguir descrevem como definir as configurações de segurança:  
  
1. Abra **Painel de Controle**.  
  
2. Clique em **rede e Internet** e, em seguida, clique em **opções da Internet**.  
  
     É exibida a caixa de diálogo Opções da Internet.  
  
3. Sobre o **segurança** , selecione para definir as configurações de segurança para a zona.  
  
4. Clique o **nível personalizado** botão.  
  
     O **as configurações de segurança** caixa de diálogo é exibida e você pode configurar as configurações de segurança para a zona selecionada.  
  
     ![Captura de tela que mostra a caixa de diálogo Configurações de segurança.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
>  Também é possível acessar a caixa de diálogo Opções da Internet pelo Internet Explorer. Clique em **ferramentas** e, em seguida, clique em **opções da Internet**.  
  
 Começando com [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], as seguintes configurações de segurança especificamente para o .NET Framework são incluídas:  
  
- **XAML flexível**. Controles se [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] navegar até eles e flexível [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivos. (Opções de Habilitar, Desabilitar e Prompt.)  
  
- **Aplicativos do navegador XAML**. Controles se [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] pode navegar para e execute [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]. (Opções de Habilitar, Desabilitar e Prompt.)  
  
 Por padrão, essas configurações são habilitadas para o **Internet**, **intranet Local**, e **sites confiáveis** zonas e desabilitado para o **sites restritos**  zona.  
  
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
 O WPF <xref:System.Windows.Controls.WebBrowser> controle pode ser usado para hospedar o conteúdo da Web. O WPF <xref:System.Windows.Controls.WebBrowser> controle envolve o controle WebBrowser ActiveX subjacente. O WPF fornece algum suporte para proteger seu aplicativo quando você usa o WPF <xref:System.Windows.Controls.WebBrowser> controle para o host de conteúdo da Web não confiável. No entanto, alguns recursos de segurança devem ser aplicados diretamente pelos aplicativos, usando o <xref:System.Windows.Controls.WebBrowser> controle. Para obter mais informações sobre o controle WebBrowser ActiveX, consulte [visões gerais do controle WebBrowser e tutoriais](https://go.microsoft.com/fwlink/?LinkId=179388).  
  
> [!NOTE]
>  Esta seção também se aplica a <xref:System.Windows.Controls.Frame> controlar, pois ele usa o <xref:System.Windows.Controls.WebBrowser> para navegar até o conteúdo HTML.  
  
 Se o WPF <xref:System.Windows.Controls.WebBrowser> controle é usado para hospedar conteúdo Web não confiável, seu aplicativo deve usar um de confiança parcial <xref:System.AppDomain> para ajudar a isolar o código do aplicativo do código de script HTML potencialmente mal-intencionados. Isso é especialmente verdadeiro se o aplicativo interage com o script hospedado usando o <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> método e o <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> propriedade. Para obter mais informações, consulte [visão geral de suplementos WPF](./app-development/wpf-add-ins-overview.md).  
  
 Se seu aplicativo usa o WPF <xref:System.Windows.Controls.WebBrowser> controle, outra maneira de aumentar a segurança e reduzir os ataques é habilitar os controles de recurso do Internet Explorer. Controles de recurso são adições ao Internet Explorer que permitem que os administradores e desenvolvedores configurar os recursos do Internet Explorer e aplicativos que hospedam o controle WebBrowser ActiveX, que o WPF <xref:System.Windows.Controls.WebBrowser> controlar encapsula. Controles de recurso podem ser configurados usando o [CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394) função ou alterando os valores no registro. Para obter mais informações sobre controles de recurso, consulte [Introdução aos controles de recurso](https://go.microsoft.com/fwlink/?LinkId=179390) e [controles de recurso de Internet](https://go.microsoft.com/fwlink/?LinkId=179392).  
  
 Se você estiver desenvolvendo um aplicativo WPF autônomo que usa o WPF <xref:System.Windows.Controls.WebBrowser> controle, WPF habilita automaticamente os seguintes controles de recurso para o seu aplicativo.  
  
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
  
 Controles de recurso são aplicados pelo processo que instancia o objeto WebBrowser ActiveX. Portanto, se estiver criando um aplicativo autônomo capaz de navegar até o conteúdo não confiável, considere seriamente a possibilidade de habilitar controles de recurso adicionais.  
  
> [!NOTE]
>  Essa recomendação baseia-se em recomendações gerais para segurança do host MSHTML e SHDOCVW. Para obter mais informações, consulte [a FAQ de segurança do Host MSHTML: Parte I de II](https://go.microsoft.com/fwlink/?LinkId=179396) e [a segurança do Host MSHTML perguntas Frequentes: Parte II de II](https://go.microsoft.com/fwlink/?LinkId=179415).  
  
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
  
 Se você executar uma confiança parcial [!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] que inclui um WPF <xref:System.Windows.Controls.WebBrowser> controlar em [!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)], WPF hospeda o controle WebBrowser ActiveX no espaço de endereço do processo do Internet Explorer. Uma vez que o controle WebBrowser ActiveX é hospedado no [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] processo, todos os controles de recurso para o Internet Explorer também são habilitados para o controle WebBrowser ActiveX.  
  
 Os XBAPs executados no Internet Explorer também têm um nível adicional de segurança em comparação com aplicativos autônomos normais. Essa segurança adicional é porque o Internet Explorer e, portanto, o controle WebBrowser ActiveX, é executado protegido modo por padrão em [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] e [!INCLUDE[win7](../../../includes/win7-md.md)]. Para obter mais informações sobre o modo protegido, consulte [Compreendendo e trabalhando no modo protegido do Internet Explorer](https://go.microsoft.com/fwlink/?LinkId=179393).  
  
> [!NOTE]
>  Se você tenta executar um XBAP que inclui um WPF <xref:System.Windows.Controls.WebBrowser> controle no Firefox, enquanto estiver na zona da Internet, um <xref:System.Security.SecurityException> será lançada. Isso ocorre por causa da política de segurança do WPF.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Desabilitando os assemblies APTCA para aplicativos cliente parcialmente confiáveis  
 Quando os assemblies gerenciados estão instalados para o [!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)], eles se tornam totalmente confiáveis porque o usuário deve fornecer permissão explícita para instalá-los. Como são totalmente confiáveis, apenas aplicativos clientes gerenciados totalmente confiáveis podem usá-los. Para permitir que aplicativos parcialmente confiáveis para usá-los, eles devem ser marcados com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Somente assemblies que foram testados em relação à segurança para execução com confiança parcial devem ser marcados com tal atributo.  
  
 No entanto, é possível que um assembly APTCA exiba uma falha de segurança após ser instalado no [!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)]. Após a descoberta de uma falha de segurança, os publicadores de assembly podem produzir uma atualização de segurança para corrigir o problema em instalações existentes, além de protege de instalações que poderão ocorrer após a descoberta do problema. Uma opção para a atualização é desinstalar o assembly, embora isso possa interromper outros aplicativos clientes totalmente confiáveis que o utilizam.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Fornece um mecanismo pelo qual um assembly APTCA pode ser desabilitado para parcialmente confiável [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] sem desinstalar o assembly APTCA.  
  
 Para desabilitar um assembly APTCA, é necessário criar uma chave do Registro especial:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Um exemplo é mostrado a seguir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Essa chave estabelece uma entrada para o assembly APTCA. Você também precisa criar um valor nessa chave que habilite ou desabilite o assembly. Abaixo estão os detalhes do valor:  
  
- Nome do valor: **APTCA_FLAG**.  
  
- Tipo de valor: **REG_DWORD**.  
  
- Dados de valor: **1** desabilitar; **0** para habilitar.  
  
 Caso seja necessário desabilitar um assembly para aplicativos clientes parcialmente confiáveis, você pode gravar uma atualização que crie a chave do Registro e o valor.  
  
> [!NOTE]
>  Assemblies do núcleo do .NET Framework não são afetados por desabilitá-las dessa forma, porque eles são necessários para aplicativos gerenciados sejam executados. O suporte para desabilitar assemblies APTCA é destinado principalmente a aplicativos de terceiros.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Comportamento da área restrita para arquivos XAML flexíveis  
 Flexível [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivos são arquivos XAML somente marcação que não dependem de nenhum code-behind, manipulador de eventos ou assembly específico de aplicativo. Flexíveis [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivos são acessados diretamente do navegador, eles são carregados em uma área restrita de segurança com base no conjunto de permissões da zona de Internet padrão.  
  
 No entanto, o comportamento de segurança é diferente quando solto [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivos são acessados de qualquer um uma <xref:System.Windows.Navigation.NavigationWindow> ou <xref:System.Windows.Controls.Frame> em um aplicativo autônomo.  
  
 Em ambos os casos, o flexíveis [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivo navegação herda as permissões do aplicativo host. No entanto, esse comportamento pode ser indesejável de uma perspectiva de segurança, especialmente se um flexível [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivo foi produzido por uma entidade que não é confiável ou desconhecido. Esse tipo de conteúdo é conhecido como *conteúdo externo*e ambos <xref:System.Windows.Controls.Frame> e <xref:System.Windows.Navigation.NavigationWindow> podem ser configurados para isolá-lo quando navegada. Isolamento é obtido, definindo a **SandboxExternalContent** propriedade como true, conforme mostrado nos exemplos a seguir para <xref:System.Windows.Controls.Frame> e <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Com essa configuração, o conteúdo externo será carregado em um processo separado do processo que está hospedando o aplicativo. Esse processo restringe-se ao conjunto de permissões da zona da Internet padrão, isolando-o eficazmente do aplicativo host e do computador cliente.  
  
> [!NOTE]
>  Embora a navegação para flexível [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] arquivos de qualquer um uma <xref:System.Windows.Navigation.NavigationWindow> ou <xref:System.Windows.Controls.Frame> em um autônomo do aplicativo é implementado com base no navegador do WPF hospedando a infra-estrutura, envolvendo o processo PresentationHost, o nível de segurança é um pouco menor do que quando o conteúdo é carregado diretamente no Internet Explorer na [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] e [!INCLUDE[win7](../../../includes/win7-md.md)] (que ainda seria por meio do PresentationHost). Isso ocorre porque um aplicativo autônomo do WPF que usa um navegador da Web não oferece o recurso de segurança adicional de modo protegido do Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Recursos para o desenvolvimento de aplicativos do WPF que promovem a segurança  
 A seguir está alguns recursos adicionais para ajudar a desenvolver [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos que promovem a segurança:  
  
|Área|Recurso|  
|----------|--------------|  
|Código gerenciado|[Padrões e práticas de orientação de segurança para aplicativos](https://go.microsoft.com/fwlink/?LinkId=117426)|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[Segurança de acesso do código](../misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[Segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[Segurança parcialmente confiável do WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Consulte também

- [Segurança parcialmente confiável do WPF](wpf-partial-trust-security.md)
- [Estratégia de segurança do WPF – segurança da plataforma](wpf-security-strategy-platform-security.md)
- [Estratégia de segurança do WPF – Engenharia de segurança](wpf-security-strategy-security-engineering.md)
- [Padrões e práticas de orientação de segurança para aplicativos](https://go.microsoft.com/fwlink/?LinkId=117426)
- [Segurança de acesso do código](../misc/code-access-security.md)
- [Segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Visão geral de XAML (WPF)](./advanced/xaml-overview-wpf.md)
