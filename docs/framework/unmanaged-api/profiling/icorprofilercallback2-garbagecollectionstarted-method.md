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
ms.openlocfilehash: f4f639f9794002748e1019821514c546e4f4429f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746873"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="eb096-102">Método ICorProfilerCallback2::GarbageCollectionStarted</span><span class="sxs-lookup"><span data-stu-id="eb096-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="eb096-103">Notifica o criador de perfil de código que iniciou a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="eb096-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb096-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb096-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb096-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb096-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="eb096-106">[in] O número total de entradas na `generationCollected` matriz.</span><span class="sxs-lookup"><span data-stu-id="eb096-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="eb096-107">[in] Uma matriz de valores boolianos, que são `true` se a geração que corresponde ao índice da matriz está sendo coletado por essa coleta de lixo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="eb096-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="eb096-108">A matriz é indexada por um valor de [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeração, que indica a geração.</span><span class="sxs-lookup"><span data-stu-id="eb096-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="eb096-109">[in] Um valor igual a [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeração que indica o motivo pelo qual a coleta de lixo foi induzida.</span><span class="sxs-lookup"><span data-stu-id="eb096-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb096-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb096-110">Remarks</span></span>  
 <span data-ttu-id="eb096-111">Todos os retornos de chamada que pertencem a essa coleta de lixo ocorrer entre o `GarbageCollectionStarted` retorno de chamada e o correspondente [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="eb096-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="eb096-112">Esses retornos de chamada não precisam ocorrer no mesmo thread.</span><span class="sxs-lookup"><span data-stu-id="eb096-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="eb096-113">É seguro para o criador de perfil inspecionar objetos em seus locais originais durante o `GarbageCollectionStarted` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="eb096-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="eb096-114">O coletor de lixo começará a movimentação de objetos após o retorno de `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="eb096-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="eb096-115">Depois que o criador de perfil tem retornados desse retorno de chamada, o criador de perfil deve considerar todas as IDs de objeto como inválido até que ele receba um `ICorProfilerCallback2::GarbageCollectionFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="eb096-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb096-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb096-116">Requirements</span></span>  
 <span data-ttu-id="eb096-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb096-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb096-118">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb096-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb096-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb096-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb096-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb096-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb096-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb096-121">See also</span></span>

- [<span data-ttu-id="eb096-122">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="eb096-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="eb096-123">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="eb096-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
