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
ms.openlocfilehash: 020df45f7f18a029f8c098fcc4dea1c131da017c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706911"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="79bbf-102">Método ICorDebugValueEnum::Next</span><span class="sxs-lookup"><span data-stu-id="79bbf-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="79bbf-103">Obtém o número especificado de instâncias de "ICorDebugValue" de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="79bbf-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79bbf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79bbf-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79bbf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="79bbf-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="79bbf-106">[in] O número de `ICorDebugValue` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="79bbf-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="79bbf-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="79bbf-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="79bbf-108">[out] Ponteiro para o número de `ICorDebugValue` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="79bbf-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="79bbf-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="79bbf-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79bbf-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79bbf-110">Requirements</span></span>  
 <span data-ttu-id="79bbf-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79bbf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79bbf-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79bbf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79bbf-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79bbf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79bbf-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79bbf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79bbf-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79bbf-115">See also</span></span>


