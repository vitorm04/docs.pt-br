---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 04caca0c580d26fde7fc9a3e3a11b7a8fed26d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225515"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="bf3be-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="bf3be-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="bf3be-103">Essa interface enumera os dispositivos de entrada brutos e é usado somente por PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="bf3be-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf3be-104">Esta API é destinada e tem suporte somente para uso no computador cliente local</span><span class="sxs-lookup"><span data-stu-id="bf3be-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="bf3be-105">Membros</span><span class="sxs-lookup"><span data-stu-id="bf3be-105">Members</span></span>  
  
|<span data-ttu-id="bf3be-106">Membro</span><span class="sxs-lookup"><span data-stu-id="bf3be-106">Member</span></span>|<span data-ttu-id="bf3be-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf3be-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf3be-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="bf3be-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="bf3be-109">Enumera os próximos `celt` elementos (ou seja, estruturas RAWINPUTDEVICE) na lista do enumerador, retornando-os no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="bf3be-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="bf3be-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="bf3be-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="bf3be-111">Instrui o enumerador para ignorar a próxima `celt` elementos na enumeração para que a próxima chamada para [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) não retornará esses elementos.</span><span class="sxs-lookup"><span data-stu-id="bf3be-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="bf3be-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="bf3be-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="bf3be-113">Redefine a sequência de enumeração para o início.</span><span class="sxs-lookup"><span data-stu-id="bf3be-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="bf3be-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="bf3be-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="bf3be-115">Cria outro enumerador de dispositivo brutos de entrada com o mesmo estado que o enumerador atual para iterar sobre a mesma lista.</span><span class="sxs-lookup"><span data-stu-id="bf3be-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf3be-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf3be-116">See also</span></span>

- [<span data-ttu-id="bf3be-117">Sobre entrada bruta</span><span class="sxs-lookup"><span data-stu-id="bf3be-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
