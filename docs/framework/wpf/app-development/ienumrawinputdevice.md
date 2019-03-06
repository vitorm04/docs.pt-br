---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: e7bc6f2c96413f3898a17b541733eeecd6a260f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375058"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="d0f7d-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="d0f7d-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="d0f7d-103">Essa interface enumera os dispositivos de entrada brutos e é usado somente por PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0f7d-104">Esta API é destinada e tem suporte somente para uso no computador cliente local</span><span class="sxs-lookup"><span data-stu-id="d0f7d-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="d0f7d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d0f7d-105">Members</span></span>  
  
|<span data-ttu-id="d0f7d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d0f7d-106">Member</span></span>|<span data-ttu-id="d0f7d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0f7d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0f7d-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="d0f7d-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="d0f7d-109">Enumera os próximos `celt` elementos (ou seja, estruturas RAWINPUTDEVICE) na lista do enumerador, retornando-os no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="d0f7d-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="d0f7d-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="d0f7d-111">Instrui o enumerador para ignorar a próxima `celt` elementos na enumeração para que a próxima chamada para [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) não retornará esses elementos.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="d0f7d-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="d0f7d-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="d0f7d-113">Redefine a sequência de enumeração para o início.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="d0f7d-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="d0f7d-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="d0f7d-115">Cria outro enumerador de dispositivo brutos de entrada com o mesmo estado que o enumerador atual para iterar sobre a mesma lista.</span><span class="sxs-lookup"><span data-stu-id="d0f7d-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0f7d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0f7d-116">See also</span></span>
- [<span data-ttu-id="d0f7d-117">Sobre entrada bruta</span><span class="sxs-lookup"><span data-stu-id="d0f7d-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
