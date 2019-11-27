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
ms.openlocfilehash: fdfd3715220785a1fa5285b19e677bf0dc190719
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433085"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="c7e7f-102">Método ICorProfilerInfo2::GetObjectGeneration</span><span class="sxs-lookup"><span data-stu-id="c7e7f-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="c7e7f-103">Obtém o segmento do heap que contém o objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="c7e7f-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7e7f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7e7f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7e7f-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="c7e7f-106">no A ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="c7e7f-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="c7e7f-107">fora Um ponteiro para uma estrutura de [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) , que descreve um intervalo (ou seja, um bloco) de memória na geração que está passando pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c7e7f-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="c7e7f-108">Este intervalo contém o objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="c7e7f-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7e7f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7e7f-109">Remarks</span></span>  
 <span data-ttu-id="c7e7f-110">O método `GetObjectGeneration` pode ser chamado de qualquer retorno de chamada do criador de perfil, desde que a coleta de lixo não esteja em andamento.</span><span class="sxs-lookup"><span data-stu-id="c7e7f-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="c7e7f-111">Ou seja, ele pode ser chamado de qualquer retorno de chamada, exceto aqueles que ocorrem entre [ICorProfilerCallback2:: GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) e [ICorProfilerCallback2:: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="c7e7f-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7e7f-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c7e7f-112">Requirements</span></span>  
 <span data-ttu-id="c7e7f-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7e7f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7e7f-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c7e7f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7e7f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7e7f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7e7f-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7e7f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e7f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7e7f-117">See also</span></span>

- [<span data-ttu-id="c7e7f-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="c7e7f-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="c7e7f-119">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="c7e7f-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
