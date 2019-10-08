---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 85309e46403b2f22f9afb760d4c4ae370c39246b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004098"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplicativos que hospedam conteúdo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] via PresentationHost.exe implementam essa interface para fornecer um ponto de integração entre o host e PresentationHost.exe.  
  
## <a name="remarks"></a>Comentários  
 aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], como navegadores da Web, podem hospedar conteúdo WPF, incluindo [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] e XAML flexível. Para hospedar conteúdo do WPF, os aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] criam uma instância do [controle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Para ser hospedado, o WPF cria uma instância de PresentationHost. exe, que fornece o conteúdo WPF hospedado para o host para exibição no [controle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 A integração habilitada por `IWpfHostSupport` permite ao PresentationHost.exe:  
  
- Descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.  
  
- Receber mensagens de entrada de dispositivos de dados brutos registrados e encaminhar as mensagens apropriadas ao aplicativo host.  
  
- Consultar o aplicativo host para interfaces do usuário de andamento e de erro personalizadas.  
  
> [!NOTE]
> Esta API é destinada e tem suporte somente para uso no computador cliente local  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.|  
|[FilterInputMessage](filterinputmessage.md)|Chamado pelo PresentationHost.exe sempre que uma mensagem é recebida, a menos que E_NOTIMPL seja retornado.|  
|[GetCustomUI](getcustomui.md)|Por padrão, o PresentationHost.exe fornece suas próprias interfaces do usuário de andamento da implantação e de erro da implantação que são exibidas quando o conteúdo WPF é implantado.|
