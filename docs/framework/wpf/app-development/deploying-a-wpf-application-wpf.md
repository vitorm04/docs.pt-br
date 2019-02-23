---
title: Implantando um aplicativo do WPF (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 120e2ecdf5869200fa9280ce3fc0a2a3a76c667f
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748317"
---
# <a name="deploying-a-wpf-application-wpf"></a>Implantando um aplicativo do WPF (WPF)
Depois de aplicativos do Windows Presentation Foundation (WPF) são criados, eles precisam ser implantados. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e o .NET Framework incluem várias tecnologias de implantação. A tecnologia de implantação que é usada para implantar um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] depende do tipo de aplicativo. Este tópico fornece uma breve visão geral de cada tecnologia de implantação e como elas são usadas em conjunto com os requisitos de implantação de cada tipo de aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
   
<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Tecnologias de implantação  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e o .NET Framework incluem várias tecnologias de implantação, incluindo:  
  
-   Implantação do XCopy.  
  
-   Implantação [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)].  
  
-   Implantação [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>Implantação do XCopy  
 Implantação do XCopy se refere ao uso do programa de linha de comando XCopy para copiar arquivos de um local para outro. A implantação do XCopy é adequada nas seguintes circunstâncias:  
  
-   O aplicativo é independente. Ele não precisa atualizar o cliente para ser executado.  
  
-   Arquivos do aplicativo precisam ser movidos de um local para outro, como de um local de build (disco local, compartilhamento de arquivos do [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] e assim por diante) para um local de publicação (site, compartilhamento de arquivos do [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] e assim por diante).  
  
-   O aplicativo não requer integração com o shell (atalho no menu Iniciar, ícone da área de trabalho e assim por diante).  
  
 Embora o XCopy seja adequado para cenários de implantação simples, ele é limitado quando recursos de implantação mais complexos são necessários. Em particular, o uso do XCopy frequentemente causa sobrecarga para criar, executar e manter scripts para gerenciar a implantação de forma robusta. Além disso, o XCopy não dá suporte a controle de versão, desinstalação ou reversão.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Windows Installer  
 O [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] permite que aplicativos sejam empacotados como executáveis independentes que podem ser distribuídos facilmente para os clientes e executados. Além disso, o [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] é instalado com [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e permite integração com a área de trabalho, o menu Iniciar e o painel de controle Programas.  
  
 O [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] simplifica a instalação e a desinstalação de aplicativos, mas não fornece recursos para garantir que os aplicativos instalados sejam mantidos atualizados do ponto de vista do controle de versão.  
  
 Para obter mais informações sobre o Windows Installer, consulte [implantação do Windows Installer](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Implantação do ClickOnce  
 O [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] permite uma implantação com estilo Web da para aplicativos que não são Web. Os aplicativos são publicados e implantados de servidores Web ou de arquivos. Embora o [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] não dê suporte a toda a gama de recursos de cliente a que aplicativos instalados por [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] dão, ele dá suporte a um subconjunto que inclui o seguinte:  
  
-   Integração com o menu Iniciar e o painel de controle Programas.  
  
-   Controle de versão, reversão e desinstalação.  
  
-   Modo de instalação online, que sempre inicializa um aplicativo do local de implantação.  
  
-   Atualização automática quando novas versões são lançadas.  
  
-   Registro de extensões de arquivo.  
  
 Para obter mais informações sobre o [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], consulte [Segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>Implantando aplicativos do WPF  
 As opções de implantação de um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dependem do tipo de aplicativo. Da perspectiva da implantação, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tem três tipos de aplicativo significativos:  
  
-   Aplicativos autônomos.  
  
-   Aplicativos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente de marcação.  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Implantando aplicativos autônomos  
 Aplicativos autônomos são implantados usando [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] ou [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. De qualquer maneira, aplicativos autônomos exigem confiança total para serem executados. A confiança total é concedida automaticamente aos aplicativos autônomos implantados usando [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Aplicativos autônomos implantados usando [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] não recebem confiança total automaticamente. Em vez disso, o [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] exibe uma caixa de diálogo de aviso de segurança que os usuários devem aceitar antes que um aplicativo autônomo seja instalado. Se for aceita, o aplicativo autônomo será instalado e terá confiança total. Caso contrário, o aplicativo autônomo não será instalado.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Implantando aplicativos XAML somente marcação  
 Páginas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente marcação normalmente são publicadas em servidores Web, como páginas de [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] e podem ser exibidas usando [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]. Páginas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente marcação são executadas em uma área restrita de segurança com confiança parcial, com restrições que são definidas pelo conjunto de permissões da zona da Internet. Isso fornece uma área restrita de segurança equivalente a aplicativos Web baseados em [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)].  
  
 Para obter mais informações sobre a segurança de aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [Segurança](../../../../docs/framework/wpf/security-wpf.md).  
  
 Páginas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente marcação podem ser instaladas no sistema de arquivos local usando XCopy ou [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Essas páginas podem ser exibidas usando [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] ou no Windows Explorer.  
  
 Para obter mais informações sobre XAML, consulte [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>Implantando aplicativos de navegador XAML  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] são aplicativos compilados que exigem que os três arquivos a seguir sejam implantados:  
  
-   *ApplicationName*.exe: O arquivo de aplicativo do assembly executável.  
  
-   *ApplicationName*.xbap: O manifesto de implantação.  
  
-   *ApplicationName*.exe.manifest: O manifesto do aplicativo.  
  
> [!NOTE]
>  Para obter mais informações sobre manifestos de aplicativo e de implantação, consulte [Compilando um aplicativo WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 Esses arquivos são produzidos quando um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é criado. Para obter mais informações, confira [Como: Criar um novo projeto de aplicativo de navegador WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Assim como as páginas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente marcação, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] normalmente são publicados em um servidor Web e exibidos usando [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)].  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pode ser implantado em clientes usando qualquer uma das técnicas de implantação. No entanto, [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] é recomendável por fornecer os seguintes recursos:  
  
1.  Atualizações automáticas quando uma nova versão é publicada.  
  
2.  Elevação de privilégios para o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] em execução com confiança total.  
  
 Por padrão, o ClickOnce publica os arquivos do aplicativo com a extensão .deploy. Isso pode ser problemático, mas pode ser desabilitado. Para obter mais informações, consulte [Problemas de configuração de servidor e cliente em implantações do ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Para obter mais informações sobre a implantação de [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], consulte [Visão geral dos aplicativos de navegador XAML do WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>Instalando o .NET Framework  
 Para executar um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo, o Microsoft .NET Framework deve ser instalado no cliente. [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] detecta automaticamente se os clientes são instalados com o .NET Framework quando [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos hospedados pelo navegador são exibidos. Se o .NET Framework não estiver instalado, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] solicita aos usuários para instalá-lo.  
  
 Para detectar se o .NET Framework é instalado, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] inclui um aplicativo bootstrapper registrado como o fallback [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] manipulador para arquivos de conteúdo com as seguintes extensões:. XAML,. XPS,. xbap e. Application. Se você navegar para esses tipos de arquivo e o .NET Framework não está instalado no cliente, o aplicativo bootstrapper solicitará permissão para instalá-lo. Se a permissão não for fornecida, o .NET Framework nem o aplicativo está instalado.  
  
 Se a permissão é concedida, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] baixa e instala o .NET Framework usando o [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)]. Após a instalação bem-sucedida do .NET Framework, o arquivo solicitado originalmente é aberto em uma nova janela do navegador.  
  
 Detecção automática do .NET framework está disponível no [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)], e [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] os clientes que possuem [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] ou posterior instalado.  
  
 Para obter mais informações, consulte [Implantando o .NET Framework e aplicativos](../../../../docs/framework/deployment/index.md).  
  
## <a name="see-also"></a>Consulte também
- [Compilar um aplicativo WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Segurança](../../../../docs/framework/wpf/security-wpf.md)
