---
title: "Método ICorDebugObjectEnum::Next"
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
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c8edc9273710a843b4e99568097646825fc52a09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="f6c1f-102">Método ICorDebugObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="f6c1f-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="f6c1f-103">Obtém os endereços virtuais relativos (RVAs) do número especificado de objetos de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c1f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6c1f-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6c1f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6c1f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f6c1f-106">[in] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="f6c1f-107">[out] Uma matriz de ponteiros, cada um deles aponta para um objeto CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f6c1f-108">[out] Ponteiro para o número de objetos retornados na verdade.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="f6c1f-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="f6c1f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6c1f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6c1f-110">Requirements</span></span>  
 <span data-ttu-id="f6c1f-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6c1f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6c1f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6c1f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6c1f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6c1f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6c1f-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6c1f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c1f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6c1f-115">See Also</span></span>  
 
