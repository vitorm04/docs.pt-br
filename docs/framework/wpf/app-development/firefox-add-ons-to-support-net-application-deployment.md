---
title: Suplementos do Firefox para dar suporte à implantação do aplicativo .NET
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 39f4548bfe9e505c1369a0de8262560070fd6221
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833923"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Suplementos do Firefox para dar suporte à implantação do aplicativo .NET
Habilitar o Windows Presentation Foundation (WPF) plug-in para Firefox e o .NET Framework Assistant para Firefox [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], flexível [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]e os aplicativos ClickOnce para trabalhar com o navegador Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Plug-in WPF para Firefox  
 O plug-in de WPF para Firefox habilita que os arquivos [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] flexível sejam acessados e executados no nível superior ou em um IFRAME HTML no navegador Firefox. Um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] que pode ser publicado em um servidor Web e iniciado em navegadores com suporte. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] flexível é um arquivo somente XAML que pode ser navegado e exibido em navegadores com suporte, assim como um arquivo XML.  
  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in para Firefox está instalado com o .NET Framework 3.5. Windows 7 inclui o .NET Framework 3.5, mas não inclui o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in para Firefox. Não é possível instalar o plug-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para Firefox no Windows 7.  
  
 O .NET Framework 4 não inclui o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] plug-in para Firefox. No entanto, se o .NET Framework 3.5 e o .NET Framework 4 estiverem instalados, o WPF plug-in para Firefox é instalado com o .NET Framework 3.5. Portanto, aplicativos do .NET Framework 4 ainda serão executado porque o Host do WPF carregará a versão correta do framework. Para obter mais informações, consulte [Host do WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 O .NET Framework Assistant para Firefox permite que os aplicativos ClickOnce independentes sejam executados do navegador Firefox. O .NET Framework Assistant para Firefox funciona de forma idêntica quando instalado antes e depois do navegador Firefox. Quando o navegador Firefox é iniciado e o .NET Framework 3.5 SP1 está instalado, o Firefox localiza e instala o .NET Framework Assistant para Firefox. Os usuários podem configurar o .NET Framework Assistant para Firefox para fazer o seguinte:  
  
- Avisar antes de executar o aplicativo ClickOnce.  
  
- Relate todas as versões instaladas do .NET Framework ou apenas a versão mais recente.  
  
 O .NET Framework Assistant para Firefox está incluído com o .NET Framework 3.5 SP1. Para obter informações sobre como remover o .NET Framework Assistant para Firefox, consulte [Como remover o .NET Framework Assistant para Firefox](https://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Consulte também

- [Implantando um aplicativo WPF](deploying-a-wpf-application-wpf.md)
- [Visão geral dos aplicativos de navegador XAML do WPF](wpf-xaml-browser-applications-overview.md)
- [Detectar se o plug-in do WPF para Firefox está instalado](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
