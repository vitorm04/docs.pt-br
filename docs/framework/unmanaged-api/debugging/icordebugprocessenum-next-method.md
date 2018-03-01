---
title: "Método ICorDebugProcessEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 566d4a7eefee846f26abbc64f97e0063e847218b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="38dc2-102">Método ICorDebugProcessEnum::Next</span><span class="sxs-lookup"><span data-stu-id="38dc2-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="38dc2-103">Obtém o número especificado de instâncias de ICorDebugProcess de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="38dc2-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38dc2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38dc2-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38dc2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38dc2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="38dc2-106">[in] O número de `ICorDebugProcess` instâncias a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="38dc2-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processess`  
 <span data-ttu-id="38dc2-107">[out] Uma matriz de ponteiros, cada qual apontando para um `ICorDebugProcess` objeto que representa um processo.</span><span class="sxs-lookup"><span data-stu-id="38dc2-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="38dc2-108">[out] Ponteiro para o número de `ICorDebugProcess` , na verdade, retornadas de instâncias.</span><span class="sxs-lookup"><span data-stu-id="38dc2-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="38dc2-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="38dc2-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38dc2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38dc2-110">Requirements</span></span>  
 <span data-ttu-id="38dc2-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38dc2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38dc2-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38dc2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38dc2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38dc2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38dc2-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dc2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
