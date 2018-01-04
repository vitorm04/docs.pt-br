---
title: "Método ICorDebugGCReferenceEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGCReferenceEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e61edea76b4e3be8a03000899b72d486163ceaf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="8fe9c-102">Método ICorDebugGCReferenceEnum::Next</span><span class="sxs-lookup"><span data-stu-id="8fe9c-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="8fe9c-103">Obtém o número especificado de [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instâncias que contêm informações sobre os objetos que serão coletados como lixo.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe9c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8fe9c-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fe9c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8fe9c-105">Parameters</span></span>  
 <span data-ttu-id="8fe9c-106">celt</span><span class="sxs-lookup"><span data-stu-id="8fe9c-106">celt</span></span>  
 <span data-ttu-id="8fe9c-107">[in] O número de raízes a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="8fe9c-108">raízes</span><span class="sxs-lookup"><span data-stu-id="8fe9c-108">roots</span></span>  
 <span data-ttu-id="8fe9c-109">[out] Uma matriz de ponteiros, cada qual apontando para um [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objeto que representa a raiz de um objeto a ser coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="8fe9c-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="8fe9c-110">pceltFetched</span></span>  
 <span data-ttu-id="8fe9c-111">[out] Um ponteiro para o número de [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objetos retornados na verdade em `roots`.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="8fe9c-112">Esse valor pode ser `null` se `celt` é 1.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fe9c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8fe9c-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe9c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8fe9c-114">Requirements</span></span>  
 <span data-ttu-id="8fe9c-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe9c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe9c-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fe9c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fe9c-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fe9c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe9c-118">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe9c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe9c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fe9c-119">See Also</span></span>  
 [<span data-ttu-id="8fe9c-120">Interface ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="8fe9c-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [<span data-ttu-id="8fe9c-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8fe9c-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
