---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 0cb1184ddc3e8051a68dfed12367dea65a06b623
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50034477"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="301b2-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="301b2-102">GetRawInputDevices</span></span>
<span data-ttu-id="301b2-103">Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.</span><span class="sxs-lookup"><span data-stu-id="301b2-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="301b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="301b2-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="301b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="301b2-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="301b2-106">[out] Um ponteiro para um [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) para enumerar os dispositivos de entrada brutos.</span><span class="sxs-lookup"><span data-stu-id="301b2-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="301b2-107">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="301b2-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="301b2-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="301b2-108">HRESULT:</span></span>  
  
 <span data-ttu-id="301b2-109">S_OK – [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) só será usado pelo PresentationHost.exe se S_OK será retornado.</span><span class="sxs-lookup"><span data-stu-id="301b2-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="301b2-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="301b2-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="301b2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="301b2-111">Remarks</span></span>  
 <span data-ttu-id="301b2-112">Dispositivos de dados brutos são o conjunto de dispositivos de entrada que inclui os teclados, mouses e dispositivos menos tradicionais como controles remotos.</span><span class="sxs-lookup"><span data-stu-id="301b2-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="301b2-113">Depois que a lista de dispositivos brutos de entrada tiver sido recuperada, PresentationHost.exe registra nos dispositivos para receber mensagens de notificação de WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="301b2-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301b2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="301b2-114">See Also</span></span>  
 [<span data-ttu-id="301b2-115">GetRawInputDeviceList</span><span class="sxs-lookup"><span data-stu-id="301b2-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)  
 [<span data-ttu-id="301b2-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="301b2-116">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
