---
title: Método ICorProfilerCallback2::GarbageCollectionStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f5f9104dded44540c47c955c15354d8d76a27650
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183060"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="60906-102">Método ICorProfilerCallback2::GarbageCollectionStarted</span><span class="sxs-lookup"><span data-stu-id="60906-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="60906-103">Notifica o criador de perfil de código que iniciou a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="60906-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60906-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60906-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60906-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60906-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="60906-106">[in] O número total de entradas na `generationCollected` matriz.</span><span class="sxs-lookup"><span data-stu-id="60906-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="60906-107">[in] Uma matriz de valores boolianos, que são `true` se a geração que corresponde ao índice da matriz está sendo coletado por essa coleta de lixo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="60906-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="60906-108">A matriz é indexada por um valor de [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeração, que indica a geração.</span><span class="sxs-lookup"><span data-stu-id="60906-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="60906-109">[in] Um valor igual a [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeração que indica o motivo pelo qual a coleta de lixo foi induzida.</span><span class="sxs-lookup"><span data-stu-id="60906-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60906-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="60906-110">Remarks</span></span>  
 <span data-ttu-id="60906-111">Todos os retornos de chamada que pertencem a essa coleta de lixo ocorrer entre o `GarbageCollectionStarted` retorno de chamada e o correspondente [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="60906-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="60906-112">Esses retornos de chamada não precisam ocorrer no mesmo thread.</span><span class="sxs-lookup"><span data-stu-id="60906-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="60906-113">É seguro para o criador de perfil inspecionar objetos em seus locais originais durante o `GarbageCollectionStarted` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="60906-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="60906-114">O coletor de lixo começará a movimentação de objetos após o retorno de `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="60906-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="60906-115">Depois que o criador de perfil tem retornados desse retorno de chamada, o criador de perfil deve considerar todas as IDs de objeto como inválido até que ele receba um `ICorProfilerCallback2::GarbageCollectionFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="60906-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60906-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60906-116">Requirements</span></span>  
 <span data-ttu-id="60906-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60906-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60906-118">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60906-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60906-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60906-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="60906-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="60906-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="60906-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60906-121">See also</span></span>

- [<span data-ttu-id="60906-122">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="60906-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="60906-123">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="60906-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
