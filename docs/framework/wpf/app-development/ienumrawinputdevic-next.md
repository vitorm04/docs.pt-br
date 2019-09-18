---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: c7450a9ababa9cf3cb02d572f5ed84f0791d74e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053406"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="2374d-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="2374d-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="2374d-103">Enumera as próximas `celt` estruturas [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) na lista do enumerador `rgelt` , retornando-as junto com o número real de elementos enumerados no. `pceltFetched`</span><span class="sxs-lookup"><span data-stu-id="2374d-103">Enumerates the next `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2374d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2374d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2374d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2374d-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="2374d-106">no Número de estruturas [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) retornadas `rgelt`em.</span><span class="sxs-lookup"><span data-stu-id="2374d-106">[in] Number of [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="2374d-107">fora Matriz de tamanho celt (ou maior) para receber estruturas RAWINPUTDEVICE enumeradas.</span><span class="sxs-lookup"><span data-stu-id="2374d-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="2374d-108">fora Ponteiro para o número de elementos realmente fornecidos no `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="2374d-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="2374d-109">O chamador pode passar `NULL` se `rgelt` for um.</span><span class="sxs-lookup"><span data-stu-id="2374d-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="2374d-110">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2374d-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="2374d-111">HRESULT: S_OK se o número de elementos fornecidos for `celt`; S_FALSE caso contrário.</span><span class="sxs-lookup"><span data-stu-id="2374d-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
