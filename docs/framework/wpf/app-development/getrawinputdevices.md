---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: acaa3a2ff0f08f60956caedba60c996e01a6eff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getrawinputdevices"></a><span data-ttu-id="96c1b-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="96c1b-102">GetRawInputDevices</span></span>
<span data-ttu-id="96c1b-103">Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.</span><span class="sxs-lookup"><span data-stu-id="96c1b-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c1b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96c1b-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96c1b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96c1b-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="96c1b-106">[out] Um ponteiro para um [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) para enumerar os dispositivos de entrada raw.</span><span class="sxs-lookup"><span data-stu-id="96c1b-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="96c1b-107">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="96c1b-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="96c1b-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="96c1b-108">HRESULT:</span></span>  
  
 <span data-ttu-id="96c1b-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) somente será usado por PresentationHost.exe se for retornado S_OK.</span><span class="sxs-lookup"><span data-stu-id="96c1b-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="96c1b-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="96c1b-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96c1b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="96c1b-111">Remarks</span></span>  
 <span data-ttu-id="96c1b-112">Dispositivos de entrada crua são o conjunto de dispositivos de entrada que inclui os teclados e mouses dispositivos menos tradicionais como controles remotos.</span><span class="sxs-lookup"><span data-stu-id="96c1b-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="96c1b-113">Depois que a lista de dispositivos de entrada crua foi obtida, PresentationHost.exe registra nos dispositivos para receber mensagens de notificação WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="96c1b-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c1b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96c1b-114">See Also</span></span>  
 [http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [<span data-ttu-id="96c1b-115">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="96c1b-115">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
