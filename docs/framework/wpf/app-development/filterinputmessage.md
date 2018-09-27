---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 1a22071696ca012968e042e15cd8a9f4b876fd9f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47236222"
---
# <a name="filterinputmessage"></a><span data-ttu-id="0eb97-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="0eb97-102">FilterInputMessage</span></span>
<span data-ttu-id="0eb97-103">Chamado pelo PresentationHost.exe sempre que uma mensagem é recebida, a menos que E_NOTIMPL seja retornado.</span><span class="sxs-lookup"><span data-stu-id="0eb97-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0eb97-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0eb97-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0eb97-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="0eb97-106">[in] A mensagem WM_INPUT enviada para a janela que está obtendo entrada não processada.</span><span class="sxs-lookup"><span data-stu-id="0eb97-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0eb97-107">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0eb97-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="0eb97-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="0eb97-108">HRESULT:</span></span>  
  
 <span data-ttu-id="0eb97-109">S_OK – o filtro não processou a mensagem e o processamento adicional pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="0eb97-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="0eb97-110">S_FALSE – o filtro processou esta mensagem e nenhum processamento adicional deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="0eb97-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="0eb97-111">E_NOTIMPL – Se esse valor for retornado, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) não será chamado novamente.</span><span class="sxs-lookup"><span data-stu-id="0eb97-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="0eb97-112">Isso pode ser retornado de um aplicativo host que só está interessado em fornecer progresso personalizado e interfaces de usuário de erro para PresentationHost.exe que não está interessado em receber mensagens de entrada não processada do PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="0eb97-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0eb97-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="0eb97-113">Remarks</span></span>  
 <span data-ttu-id="0eb97-114">PresentationHost.exe é o destino de vários dispositivos de entrada não processada, incluindo teclado, mouse e controles remotos.</span><span class="sxs-lookup"><span data-stu-id="0eb97-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="0eb97-115">Às vezes, o comportamento no aplicativo host é dependente da entrada que seria consumida pelo PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="0eb97-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="0eb97-116">Por exemplo, um aplicativo host pode depender de receber certas mensagens de entrada para determinar se deve ou não exibir elementos de interface do usuário específicos.</span><span class="sxs-lookup"><span data-stu-id="0eb97-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="0eb97-117">Para permitir que o aplicativo host receba as mensagens de entrada necessárias para fornecer esses comportamentos, o PresentationHost.exe encaminha mensagens apropriadas de entrada não processada para o aplicativo hospedado chamando [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="0eb97-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="0eb97-118">O aplicativo hospedado recebe mensagens de entrada não processada registrando com o conjunto de dispositivos de entrada não processada (dispositivos de interface humana) retornado pelo [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="0eb97-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb97-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0eb97-119">See Also</span></span>  
 [<span data-ttu-id="0eb97-120">Notificação de WM_INPUT</span><span class="sxs-lookup"><span data-stu-id="0eb97-120">WM_INPUT Notification</span></span>](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
