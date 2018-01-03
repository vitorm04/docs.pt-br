---
title: "Método ICorDebugHeapSegmentEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f8e197bb5d31635e4abc8e8bc6e3d62eb7632be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="80e5a-102">Método ICorDebugHeapSegmentEnum::Next</span><span class="sxs-lookup"><span data-stu-id="80e5a-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="80e5a-103">Obtém o número especificado de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instâncias que contêm informações sobre regiões de memória de heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="80e5a-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e5a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80e5a-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80e5a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80e5a-105">Parameters</span></span>  
 <span data-ttu-id="80e5a-106">celt</span><span class="sxs-lookup"><span data-stu-id="80e5a-106">celt</span></span>  
 <span data-ttu-id="80e5a-107">[in] O número de segmentos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="80e5a-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="80e5a-108">segmentos</span><span class="sxs-lookup"><span data-stu-id="80e5a-108">segments</span></span>  
 <span data-ttu-id="80e5a-109">[out] Uma matriz de ponteiros, cada qual apontando para um [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objeto que fornece informações sobre uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="80e5a-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="80e5a-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="80e5a-110">pceltFetched</span></span>  
 <span data-ttu-id="80e5a-111">[out] Um ponteiro para o número de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos retornados na verdade em `segments`.</span><span class="sxs-lookup"><span data-stu-id="80e5a-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="80e5a-112">Esse valor pode ser `null` se `celt` é 1.</span><span class="sxs-lookup"><span data-stu-id="80e5a-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80e5a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="80e5a-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e5a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80e5a-114">Requirements</span></span>  
 <span data-ttu-id="80e5a-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e5a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e5a-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80e5a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80e5a-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80e5a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80e5a-118">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e5a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e5a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80e5a-119">See Also</span></span>  
 [<span data-ttu-id="80e5a-120">Interface ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="80e5a-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 [<span data-ttu-id="80e5a-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="80e5a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
