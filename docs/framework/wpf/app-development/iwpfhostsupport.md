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
# <a name="iwpfhostsupport"></a><span data-ttu-id="2a004-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="2a004-102">IWpfHostSupport</span></span>
<span data-ttu-id="2a004-103">Aplicativos que hospedam conteúdo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] via PresentationHost.exe implementam essa interface para fornecer um ponto de integração entre o host e PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="2a004-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a004-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a004-104">Remarks</span></span>  
 <span data-ttu-id="2a004-105">Aplicativos Win32, como navegadores da Web, podem hospedar conteúdo WPF, incluindo aplicativos de navegador XAML (XBAPs) e XAML flexível.</span><span class="sxs-lookup"><span data-stu-id="2a004-105">Win32 applications such as Web browsers can host WPF content, including XAML browser applications (XBAPs) and loose XAML.</span></span> <span data-ttu-id="2a004-106">Para hospedar o conteúdo do WPF, os aplicativos Win32 criam uma instância do [controle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="2a004-106">To host WPF content, Win32 applications create an instance of the [WebBrowser control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span> <span data-ttu-id="2a004-107">Para ser hospedado, o WPF cria uma instância de PresentationHost. exe, que fornece o conteúdo WPF hospedado para o host para exibição no [controle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="2a004-107">To be hosted, WPF creates an instance of PresentationHost.exe, which provides the hosted WPF content to the host for display in the [WebBrowser control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span>  
  
 <span data-ttu-id="2a004-108">A integração habilitada por `IWpfHostSupport` permite ao PresentationHost.exe:</span><span class="sxs-lookup"><span data-stu-id="2a004-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="2a004-109">Descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.</span><span class="sxs-lookup"><span data-stu-id="2a004-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="2a004-110">Receber mensagens de entrada de dispositivos de dados brutos registrados e encaminhar as mensagens apropriadas ao aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="2a004-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="2a004-111">Consultar o aplicativo host para interfaces do usuário de andamento e de erro personalizadas.</span><span class="sxs-lookup"><span data-stu-id="2a004-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a004-112">Esta API é destinada e tem suporte somente para uso no computador cliente local</span><span class="sxs-lookup"><span data-stu-id="2a004-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="2a004-113">Membros</span><span class="sxs-lookup"><span data-stu-id="2a004-113">Members</span></span>  
  
|<span data-ttu-id="2a004-114">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2a004-114">Member</span></span>|<span data-ttu-id="2a004-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a004-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a004-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="2a004-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="2a004-117">Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.</span><span class="sxs-lookup"><span data-stu-id="2a004-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="2a004-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="2a004-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="2a004-119">Chamado pelo PresentationHost.exe sempre que uma mensagem é recebida, a menos que E_NOTIMPL seja retornado.</span><span class="sxs-lookup"><span data-stu-id="2a004-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="2a004-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="2a004-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="2a004-121">Por padrão, o PresentationHost.exe fornece suas próprias interfaces do usuário de andamento da implantação e de erro da implantação que são exibidas quando o conteúdo WPF é implantado.</span><span class="sxs-lookup"><span data-stu-id="2a004-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
