---
title: Segurança
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
ms.openlocfilehash: e0a56dcbf8d151fcb0d4f6271ecba15c0ff955a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174609"
---
# <a name="security-wpf"></a>Segurança (WPF)
<a name="introduction"></a>Ao desenvolver aplicativos autônomos e hospedados no Windows Presentation Foundation (WPF), você deve considerar o modelo de segurança. Os aplicativos autônomos do WPF são executados com permissões irrestritas (conjunto de permissões CAS**FullTrust),** seja implantado usando o Windows Installer (.msi), XCopy ou ClickOnce. Não há suporte para a implantação de aplicativos WPF autônomos e de confiança parcial com o ClickOnce. No entanto, um aplicativo de host <xref:System.AppDomain> de confiança total pode criar uma confiança parcial usando o modelo de complemento do Framework .NET. Para obter mais informações, consulte [visão geral do WPF Add-Ins](./app-development/wpf-add-ins-overview.md).  
  
 Os aplicativos hospedados no navegador WPF são hospedados pelo Windows Internet Explorer ou pelo Firefox, e [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] podem ser aplicativos de navegador XAML (XBAPs) ou documentos soltos Para obter mais informações, consulte [visão geral dos aplicativos do navegador WPF XAML](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 Os aplicativos hospedados no navegador WPF são executados dentro de uma caixa de areia de segurança de confiança parcial, por padrão, que é limitada ao conjunto de permissões de região**de Internet** CAS padrão. Isso isola efetivamente os aplicativos hospedados no navegador WPF do computador cliente da mesma forma que você esperaria que aplicativos típicos da Web fossem isolados. Um XBAP é capaz de elevar privilégios, até confiança total, dependendo da zona de segurança da URL de implantação e da configuração de segurança do cliente. Para obter mais informações, consulte [Segurança parcialmente confiável do WPF](wpf-partial-trust-security.md).  
  
 Este tópico discute o modelo de segurança para aplicativos autônomos e hospedados no Windows Presentation Foundation (WPF).  
  
 Este tópico contém as seguintes seções:  
  
- [Navegação segura](#SafeTopLevelNavigation)  
  
- [Configurações de segurança de software de navegação na Web](#InternetExplorerSecuritySettings)  
  
- [Controle WebBrowser e controles de recurso](#webbrowser_control_and_feature_controls)  
  
- [Desabilitando os assemblies APTCA para aplicativos cliente parcialmente confiáveis](#APTCA)  
  
- [Comportamento da área restrita para arquivos XAML flexíveis](#LooseContentSandboxing)  
  
- [Recursos para o desenvolvimento de aplicativos do WPF que promovem a segurança](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>
## <a name="safe-navigation"></a>Navegação segura  
 Para XBAPs, o WPF distingue dois tipos de navegação: aplicativo e navegador.  
  
 *A navegação do aplicativo* é uma navegação entre itens de conteúdo dentro de um aplicativo hospedado por um navegador. *A navegação do navegador* é uma navegação que muda a URL de local e conteúdo do próprio navegador. A relação entre a navegação de aplicativos (tipicamente XAML) e a navegação do navegador (tipicamente HTML) é mostrada na ilustração a seguir:
  
 ![Relação entre navegação de aplicativos e navegação do navegador.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 O tipo de conteúdo que é considerado seguro para um XBAP navegar é determinado principalmente pela navegação do aplicativo ou navegação do navegador.  
  
<a name="Application_Navigation_Security"></a>
### <a name="application-navigation-security"></a>Segurança da navegação do aplicativo  
 A navegação do aplicativo é considerada segura se puder ser identificada com um URI de pacote, que suporta quatro tipos de conteúdo:  
  
|Tipo de conteúdo|Descrição|Exemplo de URI|  
|------------------|-----------------|-----------------|  
|Recurso|Arquivos adicionados a um projeto com um tipo de **recurso**de compilação .|`pack://application:,,,/MyResourceFile.xaml`|  
|Conteúdo|Arquivos adicionados a um projeto com um tipo de compilação de **conteúdo**.|`pack://application:,,,/MyContentFile.xaml`|  
|Site de origem|Arquivos que são adicionados a um projeto com um tipo de compilação de **Nenhum**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Código do aplicativo|Recursos XAML que têm um code-behind compilado.<br /><br /> -ou-<br /><br /> Arquivos XAML que são adicionados a um projeto com um tipo de compilação de **Página**.|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
> Para obter mais informações sobre arquivos de dados de aplicativos e embalar URIs, consulte [Recursos, Conteúdo e Arquivos de Dados do Aplicativo WPF](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 É possível navegar até arquivos desses tipos de conteúdo por meio do usuário ou programaticamente:  
  
- **Navegação do usuário**. O usuário navega clicando em um <xref:System.Windows.Documents.Hyperlink> elemento.  
  
- **Navegação programática**. O aplicativo navega sem envolver o usuário, <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> por exemplo, definindo a propriedade.  
  
<a name="Browser_Navigation_Security"></a>
### <a name="browser-navigation-security"></a>Segurança da navegação do navegador  
 A navegação do navegador é considerada segura somente nestas condições:  
  
- **Navegação do usuário**. O usuário navega clicando em um <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationWindow>elemento que está <xref:System.Windows.Controls.Frame>dentro do principal, não em um aninhado .  
  
- **Zona**. O conteúdo da navegação localiza-se na Internet ou na intranet local.  
  
- **Protocolo**. O protocolo que está sendo usado é **http,** **https,** **file**ou **mailto.**  
  
 Se um XBAP tentar navegar para o conteúdo de uma maneira <xref:System.Security.SecurityException> que não esteja em conformidade com essas condições, um é jogado.  
  
<a name="InternetExplorerSecuritySettings"></a>
## <a name="web-browsing-software-security-settings"></a>Configurações de segurança de software de navegação na Web  
 As configurações de segurança no seu computador determinam o acesso concedido a qualquer software de navegação Web. O software de navegação na Web inclui qualquer aplicativo ou componente que use as APIs [WinINet](/windows/win32/wininet/portal) ou [UrlMon,](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) incluindo o Internet Explorer e o PresentationHost.exe.  
  
 O Internet Explorer fornece um mecanismo pelo qual você pode configurar a funcionalidade que pode ser executada pelo Internet Explorer ou pelo Internet Explorer, incluindo o seguinte:  
  
- .NET Framework-reliant components  
  
- Controles ActiveX e plug-ins  
  
- Downloads  
  
- Scripting  
  
- Autenticação de usuário  
  
 A coleção de funcionalidades que podem ser protegidas dessa forma é configurada por zona para as regiões **da Internet,** **Intranet,** **Sites Confiáveis**e **Sites Restritos.** As etapas a seguir descrevem como definir as configurações de segurança:  
  
1. Abra **Painel de Controle**.  
  
2. Clique **em Rede e Internet** e clique em **Opções de Internet**.  
  
     É exibida a caixa de diálogo Opções da Internet.  
  
3. Na guia **Segurança,** selecione a região para configurar as configurações de segurança para.  
  
4. Clique no botão **Nível personalizado.**  
  
     A caixa de diálogo **Configurações** de segurança é exibida e você pode configurar as configurações de segurança da região selecionada.  
  
     ![Captura de tela que mostra a caixa de diálogo Configurações de segurança.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> Também é possível acessar a caixa de diálogo Opções da Internet pelo Internet Explorer. Clique **em Ferramentas** e clique em **Opções de Internet**.  
  
 Começando com o Windows Internet Explorer 7, as seguintes configurações de segurança especificamente para .NET Framework estão incluídas:  
  
- **XAML flexível**. Controla se o Internet Explorer [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pode navegar para e soltar arquivos. (Opções de Habilitar, Desabilitar e Prompt.)  
  
- **Aplicativos do navegador XAML**. Controla se o Internet Explorer pode navegar e executar XBAPs. (Opções de Habilitar, Desabilitar e Prompt.)  
  
 Por padrão, essas configurações estão todas habilitadas para as regiões de **Sites da Internet,** **Intranet Local**e **Confiáveis** e desativadas para a região **de sites restritos.**  
  
<a name="Security_Settings_for_IE6_and_Below"></a>
### <a name="security-related-wpf-registry-settings"></a>Configurações do Registro de WPF relacionadas à segurança  
 Além das configurações de segurança disponíveis por meio das Opções da Internet, os valores de Registro a seguir estão disponíveis para bloquear seletivamente alguns recursos do WPF sensíveis à segurança. Os valores são definidos na seguinte chave:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 A tabela a seguir lista os valores que podem ser definidos.  
  
|Nome do valor|Tipo de valor|Dados do valor|  
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
 O controle <xref:System.Windows.Controls.WebBrowser> WPF pode ser usado para hospedar conteúdo da Web. O controle <xref:System.Windows.Controls.WebBrowser> WPF envolve o controle ActiveX do WebBrowser subjacente. O WPF fornece algum suporte para proteger <xref:System.Windows.Controls.WebBrowser> seu aplicativo quando você usa o controle WPF para hospedar conteúdo da Web não confiável. No entanto, alguns recursos de segurança devem <xref:System.Windows.Controls.WebBrowser> ser aplicados diretamente pelos aplicativos que usam o controle. Para obter mais informações sobre o controle do WebBrowser ActiveX, consulte [Visões gerais e tutoriais do Controle do Navegador web](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85)).  
  
> [!NOTE]
> Esta seção também <xref:System.Windows.Controls.Frame> se aplica ao <xref:System.Windows.Controls.WebBrowser> controle, uma vez que usa o para navegar para conteúdo HTML.  
  
 Se o <xref:System.Windows.Controls.WebBrowser> controle WPF for usado para hospedar conteúdo da Web <xref:System.AppDomain> não confiável, seu aplicativo deve usar uma confiança parcial para ajudar a isolar seu código de aplicativo de código de script HTML potencialmente malicioso. Isso é especialmente verdadeiro se o aplicativo estiver interagindo <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> com o <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> script hospedado usando o método e a propriedade. Para obter mais informações, consulte [visão geral do WPF Add-Ins](./app-development/wpf-add-ins-overview.md).  
  
 Se o aplicativo usar <xref:System.Windows.Controls.WebBrowser> o controle WPF, outra maneira de aumentar a segurança e mitigar ataques é ativar os controles de recursos do Internet Explorer. Os controles de recursos são adições ao Internet Explorer que permitem que administradores e desenvolvedores configurem recursos <xref:System.Windows.Controls.WebBrowser> do Internet Explorer e aplicativos que hospedam o controle WebBrowser ActiveX, que o controle WPF envolve. Os controles de recursos podem ser configurados usando a função [CoInternetSetFeatureEnabled](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85)) ou alterando valores no registro. Para obter mais informações sobre controles de recursos, consulte [Introdução aos controles de recursos](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) e controles de recursos da [Internet](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85)).  
  
 Se você estiver desenvolvendo um aplicativo WPF <xref:System.Windows.Controls.WebBrowser> autônomo que usa o controle WPF, o WPF habilita automaticamente os seguintes controles de recurso para o seu aplicativo.  
  
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
  
 Os controles de recursos são aplicados pelo processo de instanciação do objeto WebBrowser ActiveX. Portanto, se estiver criando um aplicativo autônomo capaz de navegar até o conteúdo não confiável, considere seriamente a possibilidade de habilitar controles de recurso adicionais.  
  
> [!NOTE]
> Essa recomendação baseia-se em recomendações gerais para segurança do host MSHTML e SHDOCVW. Para obter mais informações, consulte [o FAQ de segurança do host MSHTML: Parte I do II](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/) e [o FAQ de segurança do host MSHTML: Parte II de II](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/).  
  
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
  
 Se você executar um aplicativo de navegador XAML de confiança parcial <xref:System.Windows.Controls.WebBrowser> (XBAP) que inclui um controle WPF no Windows Internet Explorer, o WPF hospeda o controle WebBrowser ActiveX no espaço de endereço do processo do Internet Explorer. Como o controle Do WebBrowser ActiveX está hospedado no processo do Internet Explorer, todos os controles de recursos do Internet Explorer também estão habilitados para o controle do WebBrowser ActiveX.  
  
 Os XBAPs executados no Internet Explorer também têm um nível adicional de segurança em comparação com aplicativos autônomos normais. Essa segurança adicional é porque o Internet Explorer e, portanto, o controle Do Navegador ActiveX do WebBrowser, é executado no modo protegido por padrão no Windows Vista e no Windows 7. Para obter mais informações sobre o modo protegido, consulte [Compreensão e Trabalho no Modo Protegido Internet Explorer](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/).  
  
> [!NOTE]
> Se você tentar executar um XBAP que <xref:System.Windows.Controls.WebBrowser> inclua um controle WPF no <xref:System.Security.SecurityException> Firefox, enquanto na região da Internet, um será jogado. Isso ocorre por causa da política de segurança do WPF.  
  
<a name="APTCA"></a>
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Desabilitando os assemblies APTCA para aplicativos cliente parcialmente confiáveis  
 Quando os conjuntos gerenciados são instalados no cache de montagem global (GAC), eles se tornam totalmente confiáveis porque o usuário deve fornecer permissão explícita para instalá-los. Como são totalmente confiáveis, apenas aplicativos clientes gerenciados totalmente confiáveis podem usá-los. Para permitir que aplicativos parcialmente confiáveis os utilizem, eles devem ser marcados com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Somente assemblies que foram testados em relação à segurança para execução com confiança parcial devem ser marcados com tal atributo.  
  
 No entanto, é possível que um conjunto APTCA exiba uma falha de segurança após ser instalado no GAC . Após a descoberta de uma falha de segurança, os publicadores de assembly podem produzir uma atualização de segurança para corrigir o problema em instalações existentes, além de protege de instalações que poderão ocorrer após a descoberta do problema. Uma opção para a atualização é desinstalar o assembly, embora isso possa interromper outros aplicativos clientes totalmente confiáveis que o utilizam.  
  
 O WPF fornece um mecanismo pelo qual um conjunto APTCA pode ser desativado para XBAPs parcialmente confiáveis sem desinstalar o conjunto APTCA.  
  
 Para desabilitar um assembly APTCA, é necessário criar uma chave do Registro especial:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Um exemplo é mostrado a seguir:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Essa chave estabelece uma entrada para o assembly APTCA. Você também precisa criar um valor nessa chave que habilite ou desabilite o assembly. Abaixo estão os detalhes do valor:  
  
- Nome do valor: **APTCA_FLAG**.  
  
- Tipo de valor: **REG_DWORD**.  
  
- Dados de valor: **1** para desativar; **0** para habilitar.  
  
 Caso seja necessário desabilitar um assembly para aplicativos clientes parcialmente confiáveis, você pode gravar uma atualização que crie a chave do Registro e o valor.  
  
> [!NOTE]
> As assembléias do Core .NET Framework não são afetadas por desativá-las dessa forma porque são necessárias para que os aplicativos gerenciados sejam executados. O suporte para desabilitar assemblies APTCA é destinado principalmente a aplicativos de terceiros.  
  
<a name="LooseContentSandboxing"></a>
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Comportamento da área restrita para arquivos XAML flexíveis  
 Arquivos [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soltos são arquivos XAML somente de marcação que não dependem de nenhum conjunto de códigos atrás, manipulador de eventos ou conjunto específico de aplicativo. Quando [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] os arquivos soltos são navegados diretamente do navegador, eles são carregados em uma caixa de areia de segurança com base no conjunto de permissões de região da Internet padrão.  
  
 No entanto, o comportamento [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] de segurança é diferente <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> quando os arquivos soltos são navegados para a partir de um ou em um aplicativo autônomo.  
  
 Em ambos os [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] casos, o arquivo solto que é navegado para herdar as permissões de seu aplicativo host. No entanto, esse comportamento pode ser indesejável [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] do ponto de vista da segurança, particularmente se um arquivo solto foi produzido por uma entidade que não é confiável ou desconhecida. Esse tipo de conteúdo é conhecido <xref:System.Windows.Controls.Frame> como <xref:System.Windows.Navigation.NavigationWindow> *conteúdo externo*e ambos podem ser configurados para isolá-lo quando navegados. O isolamento é alcançado definindo a propriedade **SandboxExternalContent** como <xref:System.Windows.Controls.Frame> true, como mostrado nos exemplos a seguir e <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Com essa configuração, o conteúdo externo será carregado em um processo separado do processo que está hospedando o aplicativo. Esse processo restringe-se ao conjunto de permissões da zona da Internet padrão, isolando-o eficazmente do aplicativo host e do computador cliente.  
  
> [!NOTE]
> Embora a navegação [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] para arquivos <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> soltos de um ou em um aplicativo autônomo seja implementada com base na infra-estrutura de hospedagem do navegador WPF, envolvendo o processo PresentationHost, o nível de segurança é ligeiramente menor do que quando o conteúdo é carregado diretamente no Internet Explorer no Windows Vista e no Windows 7 (que ainda seria através do PresentationHost). Isso ocorre porque um aplicativo autônomo do WPF que usa um navegador da Web não oferece o recurso de segurança adicional de modo protegido do Internet Explorer.  
  
<a name="BestPractices"></a>
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Recursos para o desenvolvimento de aplicativos do WPF que promovem a segurança  
 A seguir, alguns recursos adicionais para ajudar a desenvolver aplicativos WPF que promovam a segurança:  
  
|Área|Recurso|  
|----------|--------------|  
|Código gerenciado|[Padrões e práticas de orientação de segurança para aplicativos](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))|  
|CAS|[Segurança de acesso a código](../misc/code-access-security.md)|  
|ClickOnce|[Cliqueemememem em Segurança e Implantação](/visualstudio/deployment/clickonce-security-and-deployment)|  
|WPF|[Segurança parcial de confiança do WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Confira também

- [Segurança parcial de confiança do WPF](wpf-partial-trust-security.md)
- [Estratégia de segurança do WPF - segurança da plataforma](wpf-security-strategy-platform-security.md)
- [Estratégia de segurança do WPF – Engenharia de segurança](wpf-security-strategy-security-engineering.md)
- [Padrões e práticas de orientação de segurança para aplicativos](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))
- [Segurança de acesso a código](../misc/code-access-security.md)
- [Cliqueemememem em Segurança e Implantação](/visualstudio/deployment/clickonce-security-and-deployment)
- [Visão geral xaml (WPF)](../../desktop-wpf/fundamentals/xaml.md)
