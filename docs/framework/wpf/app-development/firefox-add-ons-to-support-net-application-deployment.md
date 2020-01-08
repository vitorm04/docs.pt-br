---
title: Suplementos do Firefox para dar suporte à implantação do aplicativo .NET
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 687f61bd3ec7d10c6aa66c20cd5eb58fcc56f18a
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636361"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Suplementos do Firefox para dar suporte à implantação do aplicativo .NET
O plug-in do Windows Presentation Foundation (WPF) para Firefox e o assistente de .NET Framework para Firefox habilitam aplicativos de navegador XAML (XBAPs), [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]flexíveis e aplicativos ClickOnce para trabalhar com o navegador Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Plug-in WPF para Firefox  
 O plug-in do WPF para Firefox permite que XBAPs e arquivos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soltos sejam navegados e executados no nível superior ou em um IFRAME HTML no navegador Firefox. Um XBAP é um aplicativo do WPF que pode ser publicado em um servidor Web e iniciado dentro de navegadores com suporte. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] flexível é um arquivo somente XAML que pode ser navegado e exibido em navegadores com suporte, assim como um arquivo XML.  
  
 O plug-in do WPF para Firefox é instalado com o .NET Framework 3,5. O Windows 7 inclui o .NET Framework 3,5, mas não inclui o plug-in do WPF para o Firefox. Você não pode instalar o plug-in do WPF para o Firefox no Windows 7.  
  
 O .NET Framework 4 não inclui o plug-in do WPF para o Firefox. No entanto, se o .NET Framework 3,5 e o .NET Framework 4 estiverem instalados, o plug-in do WPF para o Firefox será instalado com o .NET Framework 3,5. Portanto .NET Framework 4 aplicativos ainda serão executados porque o host do WPF carregará a versão correta da estrutura. Para obter mais informações, consulte [Host do WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 O .NET Framework Assistant para Firefox permite que os aplicativos ClickOnce independentes sejam executados do navegador Firefox. O .NET Framework Assistant para Firefox funciona de forma idêntica quando instalado antes e depois do navegador Firefox. Quando o navegador Firefox é iniciado e o .NET Framework 3,5 SP1 é instalado, o Firefox localiza e instala o assistente de .NET Framework para Firefox. Os usuários podem configurar o .NET Framework Assistant para Firefox para fazer o seguinte:  
  
- Avisar antes de executar o aplicativo ClickOnce.  
  
- Relate todas as versões instaladas do .NET Framework ou apenas a versão mais recente.  
  
 O assistente de .NET Framework para Firefox está incluído no .NET Framework 3,5 SP1. Para obter informações sobre como remover o .NET Framework Assistant para Firefox, consulte [Como remover o .NET Framework Assistant para Firefox](https://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Veja também

- [Implantando um aplicativo WPF](deploying-a-wpf-application-wpf.md)
- [Visão geral dos aplicativos de navegador XAML do WPF](wpf-xaml-browser-applications-overview.md)
- [Detectar se o plug-in do WPF para Firefox está instalado](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
