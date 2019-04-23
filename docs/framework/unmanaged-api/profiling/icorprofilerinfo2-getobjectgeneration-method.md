---
title: Método ICorProfilerInfo2::GetObjectGeneration
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 64e362be57a96bbe0f61b964ab413234f30d0ed1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143774"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="0ce44-102">Método ICorProfilerInfo2::GetObjectGeneration</span><span class="sxs-lookup"><span data-stu-id="0ce44-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="0ce44-103">Obtém o segmento de heap que contém o objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="0ce44-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ce44-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ce44-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ce44-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="0ce44-106">[in] A ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="0ce44-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="0ce44-107">[out] Um ponteiro para um [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estrutura, que descreve um intervalo (ou seja, um bloco) de memória dentro a geração que está passando por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0ce44-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="0ce44-108">Esse intervalo contém o objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="0ce44-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ce44-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ce44-109">Remarks</span></span>  
 <span data-ttu-id="0ce44-110">O `GetObjectGeneration` método pode ser chamado de qualquer retorno de chamada do criador de perfil, desde que a coleta de lixo não está em andamento.</span><span class="sxs-lookup"><span data-stu-id="0ce44-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="0ce44-111">Ou seja, ele pode ser chamado de qualquer retorno de chamada, exceto aquelas que ocorrem entre [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) e [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="0ce44-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ce44-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ce44-112">Requirements</span></span>  
 <span data-ttu-id="0ce44-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ce44-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ce44-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ce44-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0ce44-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ce44-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ce44-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ce44-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce44-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ce44-117">See also</span></span>

- [<span data-ttu-id="0ce44-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="0ce44-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="0ce44-119">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="0ce44-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
