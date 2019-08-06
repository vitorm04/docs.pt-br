---
title: Implantando um aplicativo do WPF (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 2d3a72dad6a4e139288bf3c1fa9f4cde5124586f
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796769"
---
# <a name="deploying-a-wpf-application-wpf"></a>Implantando um aplicativo do WPF (WPF)
Depois que os aplicativos do Windows Presentation Foundation (WPF) são criados, eles precisam ser implantados. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]e o .NET Framework incluem várias tecnologias de implantação. A tecnologia de implantação que é usada para implantar um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] depende do tipo de aplicativo. Este tópico fornece uma breve visão geral de cada tecnologia de implantação e como elas são usadas em conjunto com os requisitos de implantação de cada tipo de aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>Tecnologias de implantação  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]e o .NET Framework incluem várias tecnologias de implantação, incluindo:  
  
- Implantação do XCopy.  
  
- Implantação [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)].  
  
- Implantação do ClickOnce.  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>Implantação do XCopy  
 Implantação do XCopy se refere ao uso do programa de linha de comando XCopy para copiar arquivos de um local para outro. A implantação do XCopy é adequada nas seguintes circunstâncias:  
  
- O aplicativo é independente. Ele não precisa atualizar o cliente para ser executado.  
  
- Arquivos do aplicativo precisam ser movidos de um local para outro, como de um local de build (disco local, compartilhamento de arquivos do [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] e assim por diante) para um local de publicação (site, compartilhamento de arquivos do [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] e assim por diante).  
  
- O aplicativo não requer integração com o shell (atalho no menu Iniciar, ícone da área de trabalho e assim por diante).  
  
 Embora o XCopy seja adequado para cenários de implantação simples, ele é limitado quando recursos de implantação mais complexos são necessários. Em particular, o uso do XCopy frequentemente causa sobrecarga para criar, executar e manter scripts para gerenciar a implantação de forma robusta. Além disso, o XCopy não dá suporte a controle de versão, desinstalação ou reversão.  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Windows Installer  
 O [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] permite que aplicativos sejam empacotados como executáveis independentes que podem ser distribuídos facilmente para os clientes e executados. Além disso, o [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] é instalado com [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e permite integração com a área de trabalho, o menu Iniciar e o painel de controle Programas.  
  
 O [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] simplifica a instalação e a desinstalação de aplicativos, mas não fornece recursos para garantir que os aplicativos instalados sejam mantidos atualizados do ponto de vista do controle de versão.  
  
 Para obter mais informações sobre Windows Installer, consulte [Windows Installer implantação](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Implantação do ClickOnce  
 O ClickOnce permite a implantação de aplicativos de estilo da Web para aplicativos que não são da Web. Os aplicativos são publicados e implantados de servidores Web ou de arquivos. Embora o ClickOnce não ofereça suporte a toda a gama de recursos [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]de cliente que os aplicativos instalados, ele oferece suporte a um subconjunto que inclui o seguinte:  
  
- Integração com o menu Iniciar e o painel de controle Programas.  
  
- Controle de versão, reversão e desinstalação.  
  
- Modo de instalação online, que sempre inicializa um aplicativo do local de implantação.  
  
- Atualização automática quando novas versões são lançadas.  
  
- Registro de extensões de arquivo.  
  
 Para obter mais informações sobre o ClickOnce, consulte [segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>Implantando aplicativos do WPF  
 As opções de implantação de um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dependem do tipo de aplicativo. Da perspectiva da implantação, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tem três tipos de aplicativo significativos:  
  
- Aplicativos autônomos.  
  
- Aplicativos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente de marcação.  
  
- [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>Implantando aplicativos autônomos  
 Os aplicativos autônomos são implantados [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]usando o ClickOnce ou o. De qualquer maneira, aplicativos autônomos exigem confiança total para serem executados. A confiança total é concedida automaticamente aos aplicativos autônomos implantados usando [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Os aplicativos autônomos que são implantados usando o ClickOnce não recebem automaticamente confiança total. Em vez disso, o ClickOnce exibe uma caixa de diálogo de aviso de segurança que os usuários devem aceitar antes que um aplicativo autônomo seja instalado. Se for aceita, o aplicativo autônomo será instalado e terá confiança total. Caso contrário, o aplicativo autônomo não será instalado.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>Implantando aplicativos XAML somente marcação  
 As páginas somente [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de marcação geralmente são publicadas em servidores Web, como páginas HTML, e podem ser [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]exibidas usando o. Páginas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente marcação são executadas em uma área restrita de segurança com confiança parcial, com restrições que são definidas pelo conjunto de permissões da zona da Internet. Isso fornece uma área restrita de segurança equivalente a aplicativos Web baseados em HTML.  
  
 Para obter mais informações sobre a segurança de aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [Segurança](../security-wpf.md).  
  
 Páginas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente marcação podem ser instaladas no sistema de arquivos local usando XCopy ou [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]. Essas páginas podem ser exibidas usando [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] o ou o Windows Explorer.  
  
 Para obter mais informações sobre XAML, consulte [Visão geral de XAML (WPF)](../advanced/xaml-overview-wpf.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>Implantando aplicativos de navegador XAML  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] são aplicativos compilados que exigem que os três arquivos a seguir sejam implantados:  
  
- *ApplicationName*.exe: O arquivo do aplicativo do assembly executável.  
  
- *ApplicationName*. XBAP: O manifesto de implantação.  
  
- *ApplicationName*.exe.manifest: O manifesto do aplicativo.  
  
> [!NOTE]
>  Para obter mais informações sobre manifestos de aplicativo e de implantação, consulte [Compilando um aplicativo WPF](building-a-wpf-application-wpf.md).  
  
 Esses arquivos são produzidos quando um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é criado. Para obter mais informações, confira [Como: Crie um novo projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))de aplicativo de navegador do WPF. Assim como as páginas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente marcação, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] normalmente são publicados em um servidor Web e exibidos usando [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)].  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pode ser implantado em clientes usando qualquer uma das técnicas de implantação. No entanto, o ClickOnce é recomendado, pois fornece os seguintes recursos:  
  
1. Atualizações automáticas quando uma nova versão é publicada.  
  
2. Elevação de privilégios para o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] em execução com confiança total.  
  
 Por padrão, o ClickOnce publica os arquivos do aplicativo com a extensão .deploy. Isso pode ser problemático, mas pode ser desabilitado. Para obter mais informações, consulte [Problemas de configuração de servidor e cliente em implantações do ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Para obter mais informações sobre a implantação de [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)], consulte [Visão geral dos aplicativos de navegador XAML do WPF](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>Instalando o .NET Framework  
 Para executar um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo, a estrutura de Microsoft .NET deve ser instalada no cliente. [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]detecta automaticamente se os clientes são instalados com .NET Framework [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] quando aplicativos hospedados em navegador são exibidos. Se o .NET Framework não estiver instalado, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] o solicitará que os usuários o instalem.  
  
 Para detectar se o .NET Framework está instalado, [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] inclui um aplicativo bootstrapper que é registrado como o manipulador [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] de fallback para arquivos de conteúdo com as seguintes extensões:. XAML,. XPS,. XBAP e. Application. Se você navegar para esses tipos de arquivo e o .NET Framework não estiver instalado no cliente, o aplicativo bootstrapper solicitará permissão para instalá-lo. Se a permissão não for fornecida, nem a .NET Framework nem o aplicativo será instalado.  
  
 Se a permissão for concedida [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] , o baixará e instalará o .NET Framework usando o Microsoft serviço de transferência inteligente em segundo plano (bits). Após a instalação bem-sucedida do .NET Framework, o arquivo originalmente solicitado é aberto em uma nova janela do navegador.  
  
 .NET Framework detecção automática está disponível [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]em, [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)]e [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] clientes que tenham [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] o ou posterior instalado.  
  
 Para obter mais informações, consulte [Implantando o .NET Framework e aplicativos](../../deployment/index.md).  
  
## <a name="see-also"></a>Consulte também

- [Compilar um aplicativo WPF](building-a-wpf-application-wpf.md)
- [Segurança](../security-wpf.md)
