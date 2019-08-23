---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964773"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="04ccc-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="04ccc-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="04ccc-103">Essa interface enumera os dispositivos de entrada brutos e é usada somente pelo PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="04ccc-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04ccc-104">Esta API é destinada e tem suporte somente para uso no computador cliente local</span><span class="sxs-lookup"><span data-stu-id="04ccc-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="04ccc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="04ccc-105">Members</span></span>  
  
|<span data-ttu-id="04ccc-106">Membro</span><span class="sxs-lookup"><span data-stu-id="04ccc-106">Member</span></span>|<span data-ttu-id="04ccc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="04ccc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04ccc-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="04ccc-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="04ccc-109">Enumera os elementos seguintes `celt` (ou seja, estruturas RAWINPUTDEVICE) na lista do enumerador, retornando `rgelt` -os junto com o número real de elementos enumerados no `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="04ccc-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="04ccc-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="04ccc-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="04ccc-111">Instrui o enumerador a ignorar os próximos `celt` elementos na enumeração para que a próxima chamada para [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) não retorne esses elementos.</span><span class="sxs-lookup"><span data-stu-id="04ccc-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="04ccc-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="04ccc-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="04ccc-113">Redefine a sequência de enumeração para o início.</span><span class="sxs-lookup"><span data-stu-id="04ccc-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="04ccc-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="04ccc-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="04ccc-115">Cria outro enumerador de dispositivo de entrada bruto com o mesmo estado que o enumerador atual para iterar na mesma lista.</span><span class="sxs-lookup"><span data-stu-id="04ccc-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04ccc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04ccc-116">See also</span></span>

- [<span data-ttu-id="04ccc-117">Sobre a entrada bruta</span><span class="sxs-lookup"><span data-stu-id="04ccc-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
