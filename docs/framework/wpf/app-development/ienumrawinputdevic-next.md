---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 329a2cd96346e199ee834856dd6dbfac6175b722
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515311"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="3fb89-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="3fb89-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="3fb89-103">Enumera os próximos `celt` [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) estruturas na lista do enumerador, retornando-a no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="3fb89-103">Enumerates the next `celt` [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fb89-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fb89-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fb89-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="3fb89-106">[in] Número de [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) estruturas retornadas no `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="3fb89-106">[in] Number of [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="3fb89-107">[out] Matriz de tamanho celt (ou maior) para receber as estruturas RAWINPUTDEVICE enumeradas.</span><span class="sxs-lookup"><span data-stu-id="3fb89-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="3fb89-108">[out] Ponteiro para o número de elementos realmente fornecidos em `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="3fb89-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="3fb89-109">Chamador pode passar `NULL` se `rgelt` é um.</span><span class="sxs-lookup"><span data-stu-id="3fb89-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="3fb89-110">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3fb89-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="3fb89-111">HRESULT: S_OK se o número de elementos fornecido é `celt`; S_FALSE caso contrário.</span><span class="sxs-lookup"><span data-stu-id="3fb89-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
