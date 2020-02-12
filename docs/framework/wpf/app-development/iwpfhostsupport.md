---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: e3edd7f7080562d03453898dba7a9326561803b5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124189"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplicativos que hospedam conteúdo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] via PresentationHost.exe implementam essa interface para fornecer um ponto de integração entre o host e PresentationHost.exe.  
  
## <a name="remarks"></a>Comentários  
 Aplicativos Win32, como navegadores da Web, podem hospedar conteúdo WPF, incluindo aplicativos de navegador XAML (XBAPs) e XAML flexível. Para hospedar o conteúdo do WPF, os aplicativos Win32 criam uma instância do [controle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)). Para ser hospedado, o WPF cria uma instância de PresentationHost. exe, que fornece o conteúdo WPF hospedado para o host para exibição no [controle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).  
  
 A integração habilitada por `IWpfHostSupport` permite ao PresentationHost.exe:  
  
- Descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.  
  
- Receber mensagens de entrada de dispositivos de dados brutos registrados e encaminhar as mensagens apropriadas ao aplicativo host.  
  
- Consultar o aplicativo host para interfaces do usuário de andamento e de erro personalizadas.  
  
> [!NOTE]
> Esta API é destinada e tem suporte somente para uso no computador cliente local  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.|  
|[FilterInputMessage](filterinputmessage.md)|Chamado pelo PresentationHost.exe sempre que uma mensagem é recebida, a menos que E_NOTIMPL seja retornado.|  
|[GetCustomUI](getcustomui.md)|Por padrão, o PresentationHost.exe fornece suas próprias interfaces do usuário de andamento da implantação e de erro da implantação que são exibidas quando o conteúdo WPF é implantado.|
