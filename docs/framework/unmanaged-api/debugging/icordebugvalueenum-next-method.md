---
title: "Método ICorDebugValueEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 71775db7134c8f376099b0820f4330602d3db0e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="4511c-102">Método ICorDebugValueEnum::Next</span><span class="sxs-lookup"><span data-stu-id="4511c-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="4511c-103">Obtém o número especificado de instâncias de "ICorDebugValue" de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="4511c-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4511c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4511c-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4511c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4511c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4511c-106">[in] O número de `ICorDebugValue` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="4511c-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="4511c-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugValue` objeto.</span><span class="sxs-lookup"><span data-stu-id="4511c-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4511c-108">[out] Ponteiro para o número de `ICorDebugValue` , na verdade, retornadas de instâncias.</span><span class="sxs-lookup"><span data-stu-id="4511c-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="4511c-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="4511c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4511c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4511c-110">Requirements</span></span>  
 <span data-ttu-id="4511c-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4511c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4511c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4511c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4511c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4511c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4511c-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4511c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4511c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4511c-115">See Also</span></span>  
    
 
