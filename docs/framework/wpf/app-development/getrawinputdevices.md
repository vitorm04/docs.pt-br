---
title: GetRawInputDevices
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5229eb7e72b63f3e44f67dc750d49acbf44410da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getrawinputdevices"></a><span data-ttu-id="ed589-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="ed589-102">GetRawInputDevices</span></span>
<span data-ttu-id="ed589-103">Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.</span><span class="sxs-lookup"><span data-stu-id="ed589-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed589-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed589-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed589-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed589-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="ed589-106">[out] Um ponteiro para um [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) para enumerar os dispositivos de entrada raw.</span><span class="sxs-lookup"><span data-stu-id="ed589-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ed589-107">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ed589-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="ed589-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="ed589-108">HRESULT:</span></span>  
  
 <span data-ttu-id="ed589-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) somente será usado por PresentationHost.exe se for retornado S_OK.</span><span class="sxs-lookup"><span data-stu-id="ed589-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="ed589-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ed589-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed589-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed589-111">Remarks</span></span>  
 <span data-ttu-id="ed589-112">Dispositivos de entrada crua são o conjunto de dispositivos de entrada que inclui os teclados e mouses dispositivos menos tradicionais como controles remotos.</span><span class="sxs-lookup"><span data-stu-id="ed589-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="ed589-113">Depois que a lista de dispositivos de entrada crua foi obtida, PresentationHost.exe registra nos dispositivos para receber mensagens de notificação WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="ed589-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed589-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed589-114">See Also</span></span>  
 [<span data-ttu-id="ed589-115">http://msdn.microsoft.com/library/default.asp?URL=/Library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.ASP</span><span class="sxs-lookup"><span data-stu-id="ed589-115">http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [<span data-ttu-id="ed589-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="ed589-116">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
