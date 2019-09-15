---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 4fc7a5021f9f8d9e6badcd3e13266fb8f4bfe7a4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991754"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="739cf-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="739cf-102">GetRawInputDevices</span></span>
<span data-ttu-id="739cf-103">Permite ao PresentationHost.exe descobrir e registrar os dispositivos de dados brutos (dispositivos de interface humana) no qual o aplicativo host está interessado.</span><span class="sxs-lookup"><span data-stu-id="739cf-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="739cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="739cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a><span data-ttu-id="739cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="739cf-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="739cf-106">fora Um ponteiro para um [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) para enumerar os dispositivos de entrada brutos.</span><span class="sxs-lookup"><span data-stu-id="739cf-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="739cf-107">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="739cf-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="739cf-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="739cf-108">HRESULT:</span></span>  
  
 <span data-ttu-id="739cf-109">S_OK- [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) será usado somente pelo PresentationHost. exe se S_OK for retornado.</span><span class="sxs-lookup"><span data-stu-id="739cf-109">S_OK - [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="739cf-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="739cf-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="739cf-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="739cf-111">Remarks</span></span>  
 <span data-ttu-id="739cf-112">Os dispositivos de entrada brutos são o conjunto de dispositivos de entrada que inclui teclados, mouses e dispositivos menos tradicionais, como controles remotos.</span><span class="sxs-lookup"><span data-stu-id="739cf-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="739cf-113">Depois que a lista de dispositivos de entrada brutos for recuperada, o PresentationHost. exe será registrado com os dispositivos para receber mensagens de notificação WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="739cf-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="739cf-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="739cf-114">See also</span></span>

- [<span data-ttu-id="739cf-115">GetRawInputDeviceList</span><span class="sxs-lookup"><span data-stu-id="739cf-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [<span data-ttu-id="739cf-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="739cf-116">FilterInputMessage</span></span>](filterinputmessage.md)
