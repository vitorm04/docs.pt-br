---
title: Método ICorDebugValueEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b24507c7cb0860fc04fa519c6bd95113483f629d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174207"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="4dae4-102">Método ICorDebugValueEnum::Next</span><span class="sxs-lookup"><span data-stu-id="4dae4-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="4dae4-103">Obtém o número especificado de instâncias de "ICorDebugValue" de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="4dae4-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dae4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4dae4-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dae4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4dae4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4dae4-106">[in] O número de `ICorDebugValue` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="4dae4-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="4dae4-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="4dae4-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4dae4-108">[out] Ponteiro para o número de `ICorDebugValue` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="4dae4-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="4dae4-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="4dae4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dae4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4dae4-110">Requirements</span></span>  
 <span data-ttu-id="4dae4-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dae4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dae4-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dae4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dae4-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dae4-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4dae4-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="4dae4-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4dae4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4dae4-115">See also</span></span>
