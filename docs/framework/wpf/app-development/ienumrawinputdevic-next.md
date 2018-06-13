---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 3cf3231bd48290c5b6b0ce8eeb6534de564c0c85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546400"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="e27b7-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="e27b7-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="e27b7-103">Enumera os próximos `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) estruturas na lista do enumerador, retornando-os no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="e27b7-103">Enumerates the next `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e27b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e27b7-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e27b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e27b7-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="e27b7-106">[in] Número de [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) estruturas retornadas no `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="e27b7-106">[in] Number of [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="e27b7-107">[out] Matriz de tamanho celt (ou maior) para receber as estruturas RAWINPUTDEVICE enumeradas.</span><span class="sxs-lookup"><span data-stu-id="e27b7-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="e27b7-108">[out] Ponteiro para o número de elementos realmente fornecidos em `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="e27b7-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="e27b7-109">O chamador pode passar no `NULL` se `rgelt` é um.</span><span class="sxs-lookup"><span data-stu-id="e27b7-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e27b7-110">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e27b7-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="e27b7-111">HRESULT: S_OK se o número de elementos fornecido é `celt`; S_FALSE caso contrário.</span><span class="sxs-lookup"><span data-stu-id="e27b7-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
