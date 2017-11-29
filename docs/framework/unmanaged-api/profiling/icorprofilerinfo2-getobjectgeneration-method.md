---
title: "Método ICorProfilerInfo2::GetObjectGeneration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetObjectGeneration
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e90139f96638dbb1a183f98e754838ff52424fc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="df9ec-102">Método ICorProfilerInfo2::GetObjectGeneration</span><span class="sxs-lookup"><span data-stu-id="df9ec-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="df9ec-103">Obtém o segmento do heap que contém o objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="df9ec-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df9ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df9ec-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df9ec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df9ec-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="df9ec-106">[in] A ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="df9ec-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="df9ec-107">[out] Um ponteiro para um [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estrutura, que descreve um intervalo (ou seja, um bloco) de memória dentro a geração que está passando por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="df9ec-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="df9ec-108">Esse intervalo contém o objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="df9ec-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df9ec-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="df9ec-109">Remarks</span></span>  
 <span data-ttu-id="df9ec-110">O `GetObjectGeneration` método pode ser chamado de qualquer retorno de chamada do criador de perfil, desde que a coleta de lixo não está em andamento.</span><span class="sxs-lookup"><span data-stu-id="df9ec-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="df9ec-111">Ou seja, ele pode ser chamado de qualquer retorno de chamada, exceto os que ocorrem entre [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) e [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="df9ec-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df9ec-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df9ec-112">Requirements</span></span>  
 <span data-ttu-id="df9ec-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df9ec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df9ec-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="df9ec-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df9ec-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df9ec-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df9ec-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df9ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df9ec-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df9ec-117">See Also</span></span>  
 [<span data-ttu-id="df9ec-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="df9ec-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="df9ec-119">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="df9ec-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
