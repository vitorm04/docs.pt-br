---
title: Implantar um aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 54d14503a0f65bb50f2dfb14d40af3b47d51589c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186321"
---
# <a name="deploy-a-wpf-application"></a>Implantar um aplicativo WPF

Depois que os aplicativos do Windows Presentation Foundation (WPF) forem construídos, eles precisam ser implantados. O Windows e o .NET Framework incluem várias tecnologias de implantação. A tecnologia de implantação usada para implantar um aplicativo WPF depende do tipo de aplicativo. Este tópico fornece uma breve visão geral de cada tecnologia de implantação e como elas são usadas em conjunto com os requisitos de implantação de cada tipo de aplicativo WPF.

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>Tecnologias de implantação  
 O Windows e o .NET Framework incluem várias tecnologias de implantação, incluindo:  
  
- Implantação do XCopy.  
  
- Implantação do Windows Installer.  
  
- Implantação do ClickOnce.  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a>Implantação do XCopy  
 Implantação do XCopy se refere ao uso do programa de linha de comando XCopy para copiar arquivos de um local para outro. A implantação do XCopy é adequada nas seguintes circunstâncias:  
  
- O aplicativo é independente. Ele não precisa atualizar o cliente para ser executado.  
  
- Os arquivos de aplicativos devem ser movidos de um local para outro, como de um local de compilação (disco local, compartilhamento de arquivos UNC e assim por diante) para um local de publicação (site da Web, compartilhamento de arquivos UNC e assim por diante).  
  
- O aplicativo não requer integração com o shell (atalho no menu Iniciar, ícone da área de trabalho e assim por diante).  
  
 Embora o XCopy seja adequado para cenários de implantação simples, ele é limitado quando recursos de implantação mais complexos são necessários. Em particular, o uso do XCopy frequentemente causa sobrecarga para criar, executar e manter scripts para gerenciar a implantação de forma robusta. Além disso, o XCopy não dá suporte a controle de versão, desinstalação ou reversão.  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a>Windows Installer  
 O Windows Installer permite que os aplicativos sejam embalados como executáveis independentes que podem ser facilmente distribuídos aos clientes e executados. Além disso, o Windows Installer é instalado com o Windows e permite a integração com a área de trabalho, o menu Iniciar e o painel de controle Programas.  
  
 O Windows Installer simplifica a instalação e a desinstalação de aplicativos, mas não fornece facilidades para garantir que os aplicativos instalados sejam mantidos atualizados do ponto de vista da versão.  
  
 Para obter mais informações sobre o Windows Installer, consulte [a implantação do instalador do Windows](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>Implantação do ClickOnce  
 O ClickOnce habilita a implantação de aplicativos no estilo Web para aplicativos não-Web. Os aplicativos são publicados e implantados de servidores Web ou de arquivos. Embora o ClickOnce não suporte toda a gama de recursos do cliente que os aplicativos instalados pelo Windows Installer fazem, ele oferece suporte a um subconjunto que inclui o seguinte:  
  
- Integração com o menu Iniciar e o painel de controle Programas.  
  
- Controle de versão, reversão e desinstalação.  
  
- Modo de instalação online, que sempre inicializa um aplicativo do local de implantação.  
  
- Atualização automática quando novas versões são lançadas.  
  
- Registro de extensões de arquivo.  
  
 Para obter mais informações sobre o ClickOnce, consulte [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>Implantando aplicativos do WPF  
 As opções de implantação de um aplicativo WPF dependem do tipo de aplicação. Do ponto de vista da implantação, o WPF tem três tipos de aplicativos significativos:  
  
- Aplicativos autônomos.  
  
- Aplicativos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente de marcação.  
  
- Aplicativos de navegador XAML (XBAPs).  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>Implantando aplicativos autônomos  
 Os aplicativos autônomos são implantados usando o ClickOnce ou o Windows Installer. De qualquer maneira, aplicativos autônomos exigem confiança total para serem executados. A confiança total é concedida automaticamente a aplicativos autônomos que são implantados usando o Windows Installer. Os aplicativos autônomos que são implantados usando o ClickOnce não são automaticamente concedidos total confiança. Em vez disso, o ClickOnce exibe uma caixa de diálogo de aviso de segurança que os usuários devem aceitar antes que um aplicativo autônomo seja instalado. Se for aceita, o aplicativo autônomo será instalado e terá confiança total. Caso contrário, o aplicativo autônomo não será instalado.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>Implantando aplicativos XAML somente marcação  
 As páginas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente de marcação geralmente são publicadas em servidores da Web, como páginas HTML, e podem ser visualizadas usando o Internet Explorer. Páginas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente marcação são executadas em uma área restrita de segurança com confiança parcial, com restrições que são definidas pelo conjunto de permissões da zona da Internet. Isso fornece uma caixa de areia de segurança equivalente a aplicativos web baseados em HTML.  
  
 Para obter mais informações sobre segurança para aplicativos WPF, consulte [Segurança](../security-wpf.md).  
  
 As páginas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] somente de marcação podem ser instaladas no sistema de arquivos local usando xCopy ou Windows Installer. Essas páginas podem ser visualizadas usando o Internet Explorer ou o Windows Explorer.  
  
 Para obter mais informações sobre XAML, consulte [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>Implantando aplicativos de navegador XAML  
 XBAPs são aplicativos compilados que exigem que os três arquivos a seguir sejam implantados:  
  
- *ApplicationName*.exe: o arquivo de aplicativo do assembly executável.  
  
- *ApplicationName*.xbap: o manifesto de implantação.  
  
- *ApplicationName*.exe.manifest: o manifesto do aplicativo.  
  
> [!NOTE]
> Para obter mais informações sobre manifestos de aplicativo e de implantação, consulte [Compilando um aplicativo WPF](building-a-wpf-application-wpf.md).  
  
 Esses arquivos são produzidos quando um XBAP é construído. Para obter mais informações, consulte [Como criar um novo projeto de aplicativo de navegador do WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Como páginas somente [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de marcação, os XBAPs são normalmente publicados em um servidor da Web e visualizados usando o Internet Explorer.  
  
 XBAPs podem ser implantados para clientes usando qualquer uma das técnicas de implantação. No entanto, o ClickOnce é recomendado, pois fornece os seguintes recursos:  
  
1. Atualizações automáticas quando uma nova versão é publicada.  
  
2. Privilégios de elevação para o XBAP funcionando com total confiança.  
  
 Por padrão, o ClickOnce publica os arquivos do aplicativo com a extensão .deploy. Isso pode ser problemático, mas pode ser desabilitado. Para obter mais informações, consulte [Problemas de configuração de servidor e cliente em implantações do ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Para obter mais informações sobre a implantação de aplicativos de navegador XAML (XBAPs), consulte [A visão geral dos aplicativos do navegador WPF XAML](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>Instalando o .NET Framework  
 Para executar um aplicativo WPF, o Microsoft .NET Framework deve ser instalado no cliente. O Internet Explorer detecta automaticamente se os clientes estão instalados no .NET Framework quando os aplicativos hospedados no navegador WPF são visualizados. Se o .NET Framework não estiver instalado, o Internet Explorer solicitará aos usuários que o instalem.  
  
 Para detectar se o .NET Framework está instalado, o Internet Explorer inclui um aplicativo bootstrapper que é registrado como o manipulador mime (Multipurpose Internet Mail Extensions, extensões de internet multiuso) para arquivos de conteúdo com as seguintes extensões: .xaml, .xps, .xbap , e .aplicação. Se você navegar para esses tipos de arquivos e o .NET Framework não estiver instalado no cliente, o aplicativo bootstrapper solicitará permissão para instalá-lo. Se a permissão não for fornecida, nem o .NET Framework nem o aplicativo serão instalados.  
  
 Se a permissão for concedida, o Internet Explorer baixa e instala o .NET Framework usando o Serviço de Transferência Inteligente (BITS) do Microsoft Background. Após a instalação bem-sucedida do .NET Framework, o arquivo originalmente solicitado é aberto em uma nova janela do navegador.  
  
 Para obter mais informações, consulte [Implantando o .NET Framework e aplicativos](../../deployment/index.md).  
  
## <a name="see-also"></a>Confira também

- [Compilando um aplicativo WPF](building-a-wpf-application-wpf.md)
- [Segurança](../security-wpf.md)
