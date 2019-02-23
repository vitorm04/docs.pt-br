---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: a1f76bf42da9a311633de39e42dee2055fac4a27
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745179"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="33275-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="33275-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="33275-103">Enumera os próximos `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) estruturas na lista do enumerador, retornando-a no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="33275-103">Enumerates the next `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33275-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33275-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33275-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="33275-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="33275-106">[in] Número de [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) estruturas retornadas no `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="33275-106">[in] Number of [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="33275-107">[out] Matriz de tamanho celt (ou maior) para receber as estruturas RAWINPUTDEVICE enumeradas.</span><span class="sxs-lookup"><span data-stu-id="33275-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="33275-108">[out] Ponteiro para o número de elementos realmente fornecidos em `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="33275-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="33275-109">Chamador pode passar `NULL` se `rgelt` é um.</span><span class="sxs-lookup"><span data-stu-id="33275-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="33275-110">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="33275-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="33275-111">HRESULT: S_OK se o número de elementos fornecido é `celt`; S_FALSE caso contrário.</span><span class="sxs-lookup"><span data-stu-id="33275-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
