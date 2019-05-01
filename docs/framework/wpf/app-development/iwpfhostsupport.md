---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 074167111b78edc517dda019465260d0acd54737
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006688"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="4e068-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="4e068-102">IWpfHostSupport</span></span>
<span data-ttu-id="4e068-103">Aplicativos que hospedam conteúdo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] via PresentationHost.exe implementam essa interface para fornecer um ponto de integração entre o host e PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4e068-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e068-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="4e068-104">Remarks</span></span>  
 <span data-ttu-id="4e068-105">Aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], como navegadores da Web podem hospedar conteúdo [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)], incluindo [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] e XAML avulsos.</span><span class="sxs-lookup"><span data-stu-id="4e068-105">[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="4e068-106">Para hospedar conteúdo [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)], os aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] criam uma instância do [controle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="4e068-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="4e068-107">Para ser hospedado, o [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] cria uma instância de PresentationHost.exe, que fornece o conteúdo [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] hospedado para o host para exibição no [controle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="4e068-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="4e068-108">A integração habilitada por `IWpfHostSupport` permite ao PresentationHost.exe:</span><span class="sxs-lookup"><span data-stu-id="4e068-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="4e068-109">Descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.</span><span class="sxs-lookup"><span data-stu-id="4e068-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="4e068-110">Receber mensagens de entrada de dispositivos de dados brutos registrados e encaminhar as mensagens apropriadas ao aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="4e068-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="4e068-111">Consultar o aplicativo host para interfaces do usuário de andamento e de erro personalizadas.</span><span class="sxs-lookup"><span data-stu-id="4e068-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e068-112">Esta API é destinada e tem suporte somente para uso no computador cliente local</span><span class="sxs-lookup"><span data-stu-id="4e068-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="4e068-113">Membros</span><span class="sxs-lookup"><span data-stu-id="4e068-113">Members</span></span>  
  
|<span data-ttu-id="4e068-114">Membro</span><span class="sxs-lookup"><span data-stu-id="4e068-114">Member</span></span>|<span data-ttu-id="4e068-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e068-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e068-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="4e068-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="4e068-117">Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.</span><span class="sxs-lookup"><span data-stu-id="4e068-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="4e068-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="4e068-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="4e068-119">Chamado pelo PresentationHost.exe sempre que uma mensagem é recebida, a menos que E_NOTIMPL seja retornado.</span><span class="sxs-lookup"><span data-stu-id="4e068-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="4e068-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="4e068-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="4e068-121">Por padrão, o PresentationHost.exe fornece suas próprias interfaces do usuário de andamento da implantação e de erro da implantação que são exibidas quando o conteúdo WPF é implantado.</span><span class="sxs-lookup"><span data-stu-id="4e068-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
