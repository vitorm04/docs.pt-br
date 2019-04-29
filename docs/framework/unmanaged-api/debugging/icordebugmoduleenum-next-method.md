---
title: Método ICorDebugModuleEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa341c726ba84dc1d12b6c5628253a100d65a719
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942474"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="764c7-102">Método ICorDebugModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="764c7-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="764c7-103">Obtém o número de instâncias de "ICorDebugModule" especificado pelo `celt` de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="764c7-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="764c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="764c7-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="764c7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="764c7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="764c7-106">[in] O número de `ICorDebugModule` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="764c7-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="764c7-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugModule` objeto.</span><span class="sxs-lookup"><span data-stu-id="764c7-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="764c7-108">[out] Ponteiro para o número de `ICorDebugModule` instâncias, na verdade, retornadas.</span><span class="sxs-lookup"><span data-stu-id="764c7-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="764c7-109">Esse valor pode ser nulo se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="764c7-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="764c7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="764c7-110">Requirements</span></span>  
 <span data-ttu-id="764c7-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="764c7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="764c7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="764c7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="764c7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="764c7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="764c7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="764c7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764c7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="764c7-115">See also</span></span>
