---
title: "Método ICorDebugHeapEnum::Next"
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
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9869542b04b26fdf343b4112c2f84a26a3061c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="1cecb-102">Método ICorDebugHeapEnum::Next</span><span class="sxs-lookup"><span data-stu-id="1cecb-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="1cecb-103">Obtém o número especificado de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias que contêm informações sobre objetos no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1cecb-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cecb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cecb-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cecb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1cecb-105">Parameters</span></span>  
 <span data-ttu-id="1cecb-106">celt</span><span class="sxs-lookup"><span data-stu-id="1cecb-106">celt</span></span>  
 <span data-ttu-id="1cecb-107">[in] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="1cecb-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="1cecb-108">objetos</span><span class="sxs-lookup"><span data-stu-id="1cecb-108">objects</span></span>  
 <span data-ttu-id="1cecb-109">[out] Uma matriz de ponteiros, cada qual apontando para um [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objeto que fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1cecb-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="1cecb-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="1cecb-110">pceltFetched</span></span>  
 <span data-ttu-id="1cecb-111">[out] Um ponteiro para o número de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos retornados na verdade em `objects`.</span><span class="sxs-lookup"><span data-stu-id="1cecb-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="1cecb-112">Esse valor pode ser `null` se `celt` é 1.</span><span class="sxs-lookup"><span data-stu-id="1cecb-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cecb-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cecb-113">Remarks</span></span>  
 <span data-ttu-id="1cecb-114">O `COR_HEAPOBJECT.type` campo é o identificador de uma interface de COM aninhada contado por referência.</span><span class="sxs-lookup"><span data-stu-id="1cecb-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="1cecb-115">Essa referência deve ser liberada, o chamador de `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="1cecb-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cecb-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1cecb-116">Requirements</span></span>  
 <span data-ttu-id="1cecb-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cecb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cecb-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cecb-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cecb-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cecb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cecb-120">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cecb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cecb-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cecb-121">See Also</span></span>  
 [<span data-ttu-id="1cecb-122">Interface ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="1cecb-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 [<span data-ttu-id="1cecb-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1cecb-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
