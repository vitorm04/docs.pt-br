---
title: "Suplementos do Firefox para dar suporte à implantação do aplicativo .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5734d58d0cce15c52da6b7242b28ffc8d574060
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Suplementos do Firefox para dar suporte à implantação do aplicativo .NET
O plug-in [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] para Firefox e o .NET Framework Assistant para Firefox permitem que aplicativos [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] flexível e ClickOnce funcionem com o navegador Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Plug-in WPF para Firefox  
 O plug-in de WPF para Firefox habilita que os arquivos [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] flexível sejam acessados e executados no nível superior ou em um IFRAME HTML no navegador Firefox. Um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] que pode ser publicado em um servidor Web e iniciado em navegadores com suporte. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] flexível é um arquivo somente XAML que pode ser navegado e exibido em navegadores com suporte, assim como um arquivo XML.  
  
 O plug-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para Firefox é instalado com o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. O Windows 7 inclui o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], mas não inclui o plug-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para o Firefox. Não é possível instalar o plug-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para Firefox no Windows 7.  
  
 O [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] não inclui o plug-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para o Firefox. No entanto, se [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] e [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] forem instalados, o plug-in de WPF para Firefox será instalado com o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Portanto, aplicativos [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ainda serão executados, pois o Host do WPF carregará a versão correta da estrutura. Para obter mais informações, consulte [Host do WPF (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 O .NET Framework Assistant para Firefox permite que os aplicativos ClickOnce independentes sejam executados do navegador Firefox. O .NET Framework Assistant para Firefox funciona de forma idêntica quando instalado antes e depois do navegador Firefox. Quando o navegador Firefox é iniciado e o [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] é instalado, o Firefox localiza e instala o .NET Framework Assistant para Firefox. Os usuários podem configurar o .NET Framework Assistant para Firefox para fazer o seguinte:  
  
-   Avisar antes de executar o aplicativo ClickOnce.  
  
-   Relate todas as versões instaladas do .NET Framework ou apenas a versão mais recente.  
  
 O .NET Framework Assistant para Firefox está incluído com o [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]. Para obter informações sobre como remover o .NET Framework Assistant para Firefox, consulte [Como remover o .NET Framework Assistant para Firefox](http://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Consulte também  
 [Implantando um aplicativo WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [Visão geral dos aplicativos de navegador XAML do WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [Detectar se o plug-in do WPF para Firefox está instalado](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
