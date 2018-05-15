---
title: Método ICorDebugCodeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 711c85b930617632d69497e4a9cf0a74360d27f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="24f46-102">Método ICorDebugCodeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="24f46-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="24f46-103">Obtém o número especificado de instâncias de "ICorDebugCode" de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="24f46-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f46-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24f46-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24f46-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24f46-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="24f46-106">[in] O número de `ICorDebugCode` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="24f46-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="24f46-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugCode` objeto.</span><span class="sxs-lookup"><span data-stu-id="24f46-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="24f46-108">[out] Um ponteiro para o número de `ICorDebugCode` , na verdade, retornadas de instâncias.</span><span class="sxs-lookup"><span data-stu-id="24f46-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="24f46-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="24f46-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24f46-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24f46-110">Requirements</span></span>  
 <span data-ttu-id="24f46-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24f46-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24f46-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24f46-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24f46-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24f46-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24f46-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24f46-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f46-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24f46-115">See Also</span></span>  
    
 
